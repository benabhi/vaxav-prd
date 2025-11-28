# Arquitectura Técnica y Base de Datos

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 15. Stack Tecnológico

### 15.1 Backend

**Laravel (Latest Stable)**
- Framework principal
- Eloquent ORM
- Blade Components
- Form Requests
- Resource Controllers
- Policies & Gates
- Queue System (para ticks)
- Scheduler (para eventos periódicos)

**Arquitectura:**
- Service Layer Pattern
- Repository Pattern (donde tenga sentido)
- Domain-Driven Design ligero
- Interfaces para extensibilidad

### 15.2 Frontend

**Blade Templates**
- Server-side rendering
- Componentes reutilizables
- Slots y props

**Tailwind CSS**
- Diseño utility-first
- Tema personalizado para sci-fi
- Responsive design

**Alpine.js**
- Interactividad mínima
- Componentes reactivos ligeros
- Integración con Blade

### 15.3 Base de Datos

**PostgreSQL**
- Tablas relacionales para entidades core
- **JSONB** para atributos dinámicos

**Ejemplos de uso de JSONB:**

```sql
-- Planetas
CREATE TABLE planets (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    description TEXT,
    resources JSONB -- {"tritanio": 5000, "pirita": 3000}
);

-- Naves
CREATE TABLE ships (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255),
    base_stats JSONB, -- stats fijos
    bonuses JSONB -- bonos específicos
);

-- Módulos de Estación
CREATE TABLE station_modules (
    id SERIAL PRIMARY KEY,
    type VARCHAR(50),
    level INT,
    config JSONB -- configuraciones específicas del nivel
);
```

### 15.4 Caché y Sesiones

**Redis** (Evaluar necesidad)
- Cache de datos frecuentes
- Sesiones de usuario
- Queue backend
- Rate limiting

### 15.5 Containerización

**Docker + Docker Compose**

**Servicios:**
- `app`: Laravel application
- `web`: Nginx
- `db`: PostgreSQL
- `redis`: Redis (si se usa)
- `queue`: Laravel queue worker
- `scheduler`: Laravel scheduler

**Archivo docker-compose.yml base:**

```yaml
version: '3.8'
services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
    volumes:
      - .:/var/www/html
    depends_on:
      - db
      - redis

  web:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - .:/var/www/html
      - ./docker/nginx/nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - app

  db:
    image: postgres:15
    environment:
      POSTGRES_DB: vaxav
      POSTGRES_USER: vaxav
      POSTGRES_PASSWORD: secret
    volumes:
      - pgdata:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  redis:
    image: redis:alpine
    ports:
      - "6379:6379"

  queue:
    build:
      context: .
      dockerfile: Dockerfile
    command: php artisan queue:work
    depends_on:
      - db
      - redis

volumes:
  pgdata:
```

---

## 16. Estructura de Base de Datos (Preliminar)

### 16.1 Configuración del Juego

### Game Config

Almacena las configuraciones globales del juego, editables por administradores.

```sql
CREATE TABLE game_config (
    id BIGSERIAL PRIMARY KEY,
    config_key VARCHAR(100) UNIQUE NOT NULL,
    config_value TEXT NOT NULL,
    value_type VARCHAR(20) NOT NULL, -- 'integer', 'float', 'string', 'boolean', 'json'
    description TEXT,
    category VARCHAR(50), -- 'tick_system', 'economy', 'combat', 'social', etc.
    is_admin_editable BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Índice para búsquedas rápidas por clave
CREATE INDEX idx_game_config_key ON game_config(config_key);
CREATE INDEX idx_game_config_category ON game_config(category);

-- Datos iniciales de configuración
INSERT INTO game_config (config_key, config_value, value_type, description, category) VALUES
('tick_duration_minutes', '10', 'integer', 'Duración de cada tick en minutos', 'tick_system'),
('tick_enabled', 'true', 'boolean', 'Sistema de ticks activo', 'tick_system'),
('energy_recovery_offline_ticks', '2', 'integer', 'Cada cuántos ticks se recupera 1 energía offline', 'social'),
('nutrition_decay_ticks', '6', 'integer', 'Cada cuántos ticks se reduce 1 nutrición', 'social'),
('stress_change_ticks', '6', 'integer', 'Cada cuántos ticks se aplican cambios de estrés', 'social'),
('moral_daily_ticks', '144', 'integer', 'Ticks equivalentes a 1 día para cálculos de moral', 'social'),
('cooldown_unconscious_ticks', '6', 'integer', 'Ticks de cooldown al quedar inconsciente', 'social'),
('cooldown_clone_update_ticks', '144', 'integer', 'Ticks de cooldown para actualizar clon', 'game_mechanics'),
('cooldown_war_declaration_ticks', '144', 'integer', 'Ticks de cooldown para declarar guerra', 'corporations'),
('war_minimum_duration_ticks', '1008', 'integer', 'Duración mínima de guerra en ticks (~7 días)', 'corporations');
```

**Uso en Laravel:**

```php
// Helper para obtener configuración
function gameConfig(string $key, mixed $default = null): mixed {
    $config = Cache::remember("game_config_{$key}", 3600, function() use ($key) {
        return DB::table('game_config')
            ->where('config_key', $key)
            ->first();
    });

    if (!$config) return $default;

    return match($config->value_type) {
        'integer' => (int) $config->config_value,
        'float' => (float) $config->config_value,
        'boolean' => filter_var($config->config_value, FILTER_VALIDATE_BOOLEAN),
        'json' => json_decode($config->config_value, true),
        default => $config->config_value,
    };
}

// Ejemplo de uso:
$tickDuration = gameConfig('tick_duration_minutes', 10); // 10 minutos por defecto
```

### 16.2 Entidades Principales

### Users

```sql
CREATE TABLE users (
    id BIGSERIAL PRIMARY KEY,
    username VARCHAR(255) UNIQUE NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Pilots

```sql
CREATE TABLE pilots (
    id BIGSERIAL PRIMARY KEY,
    user_id BIGINT REFERENCES users(id) ON DELETE CASCADE,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    birthdate DATE NOT NULL, -- fecha de creación = cumpleaños ficticio
    career VARCHAR(50) NOT NULL, -- carrera inicial
    faction_id BIGINT REFERENCES factions(id),
    corporation_id BIGINT REFERENCES corporations(id) NULL,
    credits DECIMAL(20, 2) DEFAULT 0,
    current_location_type VARCHAR(50), -- 'station', 'space', 'orbit'
    current_location_id BIGINT,
    current_ship_id BIGINT REFERENCES ships(id) NULL,
    current_state VARCHAR(50) DEFAULT 'idle',

    -- Atributos del piloto
    energy INT DEFAULT 100 CHECK (energy >= 0 AND energy <= 100),
    nutrition INT DEFAULT 100 CHECK (nutrition >= 0 AND nutrition <= 100),
    morale INT DEFAULT 60 CHECK (morale >= 0 AND morale <= 100),
    stress INT DEFAULT 0 CHECK (stress >= 0 AND stress <= 100),
    last_ate_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_rested_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

    -- Reputación personal
    honorability INT DEFAULT 50 CHECK (honorability >= 0 AND honorability <= 100),
    combat_reliability INT DEFAULT 50 CHECK (combat_reliability >= 0 AND combat_reliability <= 100),
    trade_reputation INT DEFAULT 50 CHECK (trade_reputation >= 0 AND trade_reputation <= 100),

    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(user_id)
);
```

### Factions

```sql
CREATE TABLE factions (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    ideology TEXT,
    is_player_faction BOOLEAN DEFAULT FALSE,
    bonuses JSONB, -- {"fabrication_efficiency": 0.10}
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Corporations

```sql
CREATE TABLE corporations (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) UNIQUE NOT NULL,
    description TEXT,
    faction_id BIGINT REFERENCES factions(id),
    is_npc BOOLEAN DEFAULT TRUE,
    ceo_pilot_id BIGINT REFERENCES pilots(id) NULL,
    tax_rate DECIMAL(5, 2) DEFAULT 0,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Systems

```sql
CREATE TABLE solar_systems (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) UNIQUE NOT NULL,
    description TEXT,
    star_type VARCHAR(50), -- 'red_dwarf', 'yellow', 'giant'
    progress INT DEFAULT 0, -- barra de progreso
    is_procedural BOOLEAN DEFAULT FALSE,
    generation_seed VARCHAR(255) NULL,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Planets

```sql
CREATE TABLE planets (
    id BIGSERIAL PRIMARY KEY,
    system_id BIGINT REFERENCES solar_systems(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    orbit_position INT NOT NULL, -- 1, 2, 3...
    planet_type VARCHAR(50), -- 'rocky', 'gas', 'ice'
    resources JSONB, -- recursos disponibles
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Moons

```sql
CREATE TABLE moons (
    id BIGSERIAL PRIMARY KEY,
    planet_id BIGINT REFERENCES planets(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    orbit_position INT NOT NULL,
    resources JSONB,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Stations

```sql
CREATE TABLE stations (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    moon_id BIGINT REFERENCES moons(id) ON DELETE CASCADE,
    corporation_id BIGINT REFERENCES corporations(id),
    access_level VARCHAR(50) DEFAULT 'public', -- 'public', 'corporation', 'alliance', 'private'
    hangar_capacity_current INT DEFAULT 0,
    hangar_capacity_max INT DEFAULT 20,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Station Modules

```sql
CREATE TABLE station_modules (
    id BIGSERIAL PRIMARY KEY,
    station_id BIGINT REFERENCES stations(id) ON DELETE CASCADE,
    module_type VARCHAR(50) NOT NULL, -- 'command', 'hangar', 'laboratory', etc.
    level INT DEFAULT 1,
    status VARCHAR(50) DEFAULT 'operational', -- 'construction', 'operational', 'damaged', 'disabled'
    config JSONB, -- configuración específica del módulo
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Skills

```sql
CREATE TABLE skills (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) UNIQUE NOT NULL,
    description TEXT,
    multiplier INT NOT NULL, -- 1, 2, 3, 4, 5
    category VARCHAR(100), -- 'combat', 'industry', 'navigation', etc.
    max_level INT DEFAULT 5,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Skill Requirements

```sql
CREATE TABLE skill_requirements (
    id BIGSERIAL PRIMARY KEY,
    skill_id BIGINT REFERENCES skills(id) ON DELETE CASCADE,
    required_skill_id BIGINT REFERENCES skills(id) ON DELETE CASCADE,
    required_level INT NOT NULL
);
```

### Pilot Skills

```sql
CREATE TABLE pilot_skills (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    skill_id BIGINT REFERENCES skills(id) ON DELETE CASCADE,
    current_level INT DEFAULT 0, -- 0 significa inyectada pero no entrenada
    current_exp BIGINT DEFAULT 0,
    is_injected BOOLEAN DEFAULT FALSE, -- true si la habilidad fue inyectada
    injected_at TIMESTAMP NULL, -- fecha de inyección
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(pilot_id, skill_id)
);
```

### Pilot Discovered Skills

```sql
-- Habilidades que el piloto ha "descubierto" pero no ha inyectado
CREATE TABLE pilot_discovered_skills (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    skill_id BIGINT REFERENCES skills(id) ON DELETE CASCADE,
    discovered_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    discovery_source VARCHAR(100), -- 'laboratory', 'mission', 'item_inspection', etc.
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(pilot_id, skill_id)
);
```

### Skill Injectors (Items)

```sql
-- Los inyectores son items especiales
-- Se almacenan como items con type='skill_injector'
-- El metadata JSONB contiene: {"skill_id": 5, "skill_name": "Minería"}
-- Esta tabla es solo para referencia conceptual, se usan Items + metadata
```

### Laboratory Catalogs

```sql
-- Catálogo de inyectores disponibles en cada laboratorio
CREATE TABLE laboratory_catalogs (
    id BIGSERIAL PRIMARY KEY,
    station_module_id BIGINT REFERENCES station_modules(id) ON DELETE CASCADE,
    skill_id BIGINT REFERENCES skills(id),
    stock INT DEFAULT -1, -- -1 = infinito, >0 = stock limitado
    price_multiplier DECIMAL(5, 2) DEFAULT 1.0, -- multiplicador sobre precio base (afectado por nivel de lab)
    is_available BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(station_module_id, skill_id)
);
```

### Laboratory Specializations

```sql
-- Define qué tipo de laboratorio es cada módulo (minero, militar, comercial, etc.)
CREATE TABLE laboratory_specializations (
    id BIGSERIAL PRIMARY KEY,
    station_module_id BIGINT REFERENCES station_modules(id) ON DELETE CASCADE,
    specialization_type VARCHAR(50) NOT NULL, -- 'mining', 'military', 'commerce', 'research', 'exploration'
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Ship Templates (Blueprints)

```sql
CREATE TABLE ship_templates (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    class VARCHAR(50) NOT NULL, -- 'frigate', 'cruiser', etc.
    type VARCHAR(50), -- 'combat', 'mining', 'transport', etc.
    description TEXT,
    base_stats JSONB, -- {"shields": 500, "armor": 800, "structure": 600, "cargo": 5000, "speed": 15}
    slot_config JSONB, -- {"offensive": 1, "defensive": 2, "utility": 3}
    bonuses JSONB, -- bonos específicos
    skill_requirements JSONB, -- {"pilotaje_fragatas": 1, "mineria": 1}
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Ships (Instancias)

```sql
CREATE TABLE ships (
    id BIGSERIAL PRIMARY KEY,
    template_id BIGINT REFERENCES ship_templates(id),
    owner_id BIGINT REFERENCES pilots(id),
    name VARCHAR(255), -- nombre personalizado (opcional)
    current_shields DECIMAL(10, 2),
    current_armor DECIMAL(10, 2),
    current_structure DECIMAL(10, 2),
    location_type VARCHAR(50), -- 'hangar', 'space', 'orbit'
    location_id BIGINT,
    status VARCHAR(50) DEFAULT 'docked', -- 'docked', 'active', 'destroyed'
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Ship Module Templates

```sql
CREATE TABLE ship_module_templates (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    category VARCHAR(50) NOT NULL, -- 'offensive', 'defensive', 'utility'
    type VARCHAR(50), -- 'laser', 'shield_generator', 'cargo_expander', etc.
    tech_level INT DEFAULT 1, -- T1, T2, T3
    stats JSONB, -- stats del módulo
    skill_requirements JSONB,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Ship Modules (Fitted)

```sql
CREATE TABLE ship_modules (
    id BIGSERIAL PRIMARY KEY,
    ship_id BIGINT REFERENCES ships(id) ON DELETE CASCADE,
    module_template_id BIGINT REFERENCES ship_module_templates(id),
    slot_position INT NOT NULL,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Items

```sql
CREATE TABLE items (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    type VARCHAR(50), -- 'ore', 'mineral', 'component', 'module', 'blueprint', 'skill_injector', 'skill_accelerator', etc.
    volume DECIMAL(10, 2) DEFAULT 1, -- m³
    base_price DECIMAL(20, 2),
    stackable BOOLEAN DEFAULT TRUE,
    metadata JSONB, -- información específica del tipo
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);

-- Ejemplos de metadata para diferentes tipos:
-- type='skill_injector':
-- metadata: {"skill_id": 5, "skill_name": "Minería", "multiplier": 2}

-- type='skill_accelerator':
-- metadata: {"exp_amount": 10000, "applicable_categories": ["mining", "industry"]}

-- type='ore':
-- metadata: {"tier": 1, "refine_yield": {"tritanio": 100}}

-- type='blueprint':
-- metadata: {"item_id": 123, "runs": -1, "material_efficiency": 0, "time_efficiency": 0}
```

### Inventories

```sql
CREATE TABLE inventories (
    id BIGSERIAL PRIMARY KEY,
    owner_type VARCHAR(50) NOT NULL, -- 'pilot', 'ship', 'station', 'corporation'
    owner_id BIGINT NOT NULL,
    item_id BIGINT REFERENCES items(id),
    quantity BIGINT DEFAULT 0,
    location_type VARCHAR(50), -- 'ship_cargo', 'station_storage', 'hangar', 'market'
    location_id BIGINT,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Market Orders

```sql
CREATE TABLE market_orders (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    item_id BIGINT REFERENCES items(id),
    order_type VARCHAR(10) NOT NULL, -- 'buy' o 'sell'
    quantity INT NOT NULL,
    price DECIMAL(20, 2) NOT NULL,
    min_volume INT DEFAULT 1, -- mínimo a comprar/vender por transacción
    station_id BIGINT REFERENCES stations(id) NULL, -- NULL = regional
    range VARCHAR(20) DEFAULT 'station', -- 'station', 'system', 'regional'
    status VARCHAR(20) DEFAULT 'active', -- 'active', 'filled', 'cancelled', 'expired'
    quantity_remaining INT NOT NULL,
    issued_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    expires_at TIMESTAMP, -- duración de la orden (ej: 30 días)
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);

CREATE INDEX idx_market_orders_item ON market_orders(item_id, order_type, status);
CREATE INDEX idx_market_orders_station ON market_orders(station_id, status);
```

### Market Transactions

```sql
CREATE TABLE market_transactions (
    id BIGSERIAL PRIMARY KEY,
    buyer_id BIGINT REFERENCES pilots(id),
    seller_id BIGINT REFERENCES pilots(id),
    item_id BIGINT REFERENCES items(id),
    quantity INT NOT NULL,
    price DECIMAL(20, 2) NOT NULL,
    total_price DECIMAL(20, 2) NOT NULL,
    station_id BIGINT REFERENCES stations(id),
    buy_order_id BIGINT REFERENCES market_orders(id) NULL,
    sell_order_id BIGINT REFERENCES market_orders(id) NULL,
    transaction_type VARCHAR(20), -- 'instant_buy', 'instant_sell', 'order_filled'
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_market_transactions_item ON market_transactions(item_id, created_at DESC);
CREATE INDEX idx_market_transactions_pilot ON market_transactions(buyer_id, seller_id);
```

### Missions

```sql
CREATE TABLE missions (
    id BIGSERIAL PRIMARY KEY,
    agent_id BIGINT REFERENCES agents(id),
    name VARCHAR(255) NOT NULL,
    description TEXT,
    mission_type VARCHAR(50), -- 'mining', 'combat', 'transport', 'research'
    level INT NOT NULL,
    objectives JSONB, -- {"mine_tritanio": 1000, "location": "asteroid_field_5"}
    rewards JSONB, -- {"credits": 50000, "items": [], "faction_standing": 10}
    expires_at TIMESTAMP,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Pilot Missions

```sql
CREATE TABLE pilot_missions (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    mission_id BIGINT REFERENCES missions(id),
    status VARCHAR(50) DEFAULT 'active', -- 'active', 'completed', 'failed', 'abandoned'
    progress JSONB, -- {"mine_tritanio": 450}
    accepted_at TIMESTAMP,
    completed_at TIMESTAMP NULL,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Agents

```sql
CREATE TABLE agents (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    corporation_id BIGINT REFERENCES corporations(id),
    station_id BIGINT REFERENCES stations(id),
    agent_type VARCHAR(50), -- 'mining', 'combat', 'transport', 'research'
    level INT NOT NULL,
    created_at TIMESTAMP,
    updated_at TIMESTAMP
);
```

### Faction Standings (Relaciones)

```sql
CREATE TABLE faction_standings (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    faction_id BIGINT REFERENCES factions(id) ON DELETE CASCADE,
    standing DECIMAL(5, 2) DEFAULT 0, -- -100 a +100
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(pilot_id, faction_id)
);
```

### Actions (Tick Actions)

```sql
CREATE TABLE actions (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    action_type VARCHAR(50) NOT NULL, -- 'mining', 'travel', 'combat', 'fabrication'
    status VARCHAR(50) DEFAULT 'pending', -- 'pending', 'in_progress', 'completed', 'cancelled'
    ticks_required INT NOT NULL,
    ticks_completed INT DEFAULT 0,
    parameters JSONB, -- parámetros específicos de la acción
    result JSONB NULL, -- resultado al completar
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    completed_at TIMESTAMP NULL
);
```

### Pilot Relationships

```sql
-- Relaciones entre pilotos (amistad, enemistad)
CREATE TABLE pilot_relationships (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    target_pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    relationship_level INT DEFAULT 0 CHECK (relationship_level >= 0 AND relationship_level <= 100),
    last_interaction_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP,
    updated_at TIMESTAMP,
    UNIQUE(pilot_id, target_pilot_id)
);

CREATE INDEX idx_pilot_relationships_pilot ON pilot_relationships(pilot_id, relationship_level DESC);
```

### Social Activities Log

```sql
-- Log de actividades sociales para tracking
CREATE TABLE social_activities (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    target_pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE NULL,
    activity_type VARCHAR(50) NOT NULL, -- 'chat', 'trade', 'combat_together', 'gift', 'rescue', etc.
    relationship_change INT DEFAULT 0, -- cambio en la relación (+/-)
    metadata JSONB, -- información adicional
    created_at TIMESTAMP
);

CREATE INDEX idx_social_activities_pilot ON social_activities(pilot_id, created_at DESC);
```

### Pilot Attributes Log

```sql
-- Historial de cambios en atributos del piloto (para debugging y stats)
CREATE TABLE pilot_attributes_log (
    id BIGSERIAL PRIMARY KEY,
    pilot_id BIGINT REFERENCES pilots(id) ON DELETE CASCADE,
    attribute_type VARCHAR(50) NOT NULL, -- 'energy', 'nutrition', 'morale', 'stress'
    old_value INT NOT NULL,
    new_value INT NOT NULL,
    reason VARCHAR(255), -- 'combat', 'resting', 'eating', 'social', etc.
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE INDEX idx_pilot_attributes_log ON pilot_attributes_log(pilot_id, created_at DESC);
```

### Food Items

```sql
-- Items de comida (pueden estar en la tabla items general con type='food')
-- Esta es solo una referencia de metadata para items tipo 'food':
-- metadata: {
--   "nutrition_restored": 30,
--   "buffs": [{"type": "exp_boost", "value": 0.05, "duration_hours": 2}],
--   "stackable": true
-- }
```

---

## 17. Sistema de Ticks (Implementación)

### 17.1 Procesamiento de Ticks

**Laravel Scheduler** ejecuta comando cada X segundos/minutos.

**Comando:**

```php
php artisan game:process-tick
```

**Flujo:**
1. Obtener todas las acciones con status 'in_progress'
2. Para cada acción:
   - Incrementar ticks_completed
   - Si ticks_completed >= ticks_required:
     - Ejecutar lógica de completado
     - Actualizar status a 'completed'
     - Guardar resultado
     - Otorgar experiencia
3. Procesar eventos del sistema (respawn de NPCs, etc.)

### 17.2 Queue System

Usar **Laravel Queues** para procesamiento asíncrono de acciones pesadas.

**Jobs:**
- `ProcessMiningAction`
- `ProcessCombatTick`
- `ProcessFabrication`
- `ProcessTravelAction`

---

## 18. Extensibilidad y Escalabilidad

### 18.1 Sistema de Carreras

**Implementación:**

```php
// app/GameSystems/Careers/CareerInterface.php
interface CareerInterface {
    public function getName(): string;
    public function getDescription(): string;
    public function getInitialSkills(): array;
    public function getInitialShip(): int;
    public function getInitialModules(): array;
    public function getInitialCredits(): int;
}

// app/GameSystems/Careers/MinerCareer.php
class MinerCareer implements CareerInterface {
    // Implementación
}
```

### 18.2 Sistema de Módulos de Estación

```php
// app/GameSystems/StationModules/ModuleInterface.php
interface StationModuleInterface {
    public function getType(): string;
    public function getMaxLevel(): int;
    public function getLevelConfig(int $level): array;
    public function getAvailableActions(int $level): array;
}
```

### 18.3 Generación Procedural

```php
// app/GameSystems/ProceduralGeneration/SystemGenerator.php
class SystemGenerator {
    public function generate(string $seed): SolarSystem;
    public function generatePlanets(int $count): array;
    public function generateResources(): array;
}
```

---

## 22. Testing

### 22.1 Unit Tests

- Modelos
- Services
- Helpers de cálculo (skills, daño, etc.)

### 22.2 Feature Tests

- Endpoints
- Flujos de usuario
- Sistema de ticks
- Combate

### 22.3 Browser Tests (Laravel Dusk)

- Registro y login
- Navegación básica
- Acciones de juego

---

## Navegación

- [← Anterior: PRD-Interface.md](./PRD-Interface.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-SecurityAndQuality.md](./PRD-SecurityAndQuality.md)
