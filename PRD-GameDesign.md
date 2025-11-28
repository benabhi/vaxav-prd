# Game Design & Mecánicas Core

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 2. Mecánicas Core del Juego

### 2.1 Sistema de Ticks/Pulsos

El juego opera en ciclos de tiempo llamados "ticks" o "pulsos" ejecutados por el servidor mediante Laravel Scheduler.

**Duración del Tick:**
- **Valor por defecto:** 10 minutos
- **Configurable:** El administrador puede cambiar la duración del tick desde el panel de administración
- **Almacenado en:** Base de datos (tabla `game_config`)
- **Ejecutado por:** `php artisan game:process-tick` cada X minutos según configuración

**Características:**
- Las acciones se programan y ejecutan en ticks específicos
- Acciones instantáneas: navegación entre módulos de estación, compras simples
- Acciones de tick: minería, combate, fabricación, viajes espaciales
- El tiempo de tick depende de habilidades, equipo y bonificaciones
- Los jugadores pueden ver contadores de ticks en curso
- **Todos los sistemas del juego funcionan en base a ticks** (atributos sociales, cooldowns, regeneración, etc.)

**Cálculo de Ticks para Acciones:**

```
ticks_requeridos = base_ticks / (skill_multiplier × ship_bonus × module_bonus)
```

**Ejemplos de tiempos con tick de 10 minutos:**
- Minar asteroide básico: 6 ticks = 60 minutos
- Viajar 3 saltos: 3 ticks = 30 minutos
- Fabricar componente T1: 12 ticks = 2 horas
- Construir módulo estación nivel 2: 144 ticks = 24 horas
- Combate promedio: 5-8 ticks = 50-80 minutos

**Nota:** Si el administrador cambia la duración del tick (por ejemplo a 5 o 15 minutos), todos los tiempos se ajustan proporcionalmente de forma automática.

### 2.2 Sistema de Habilidades (Skills)

**Estructura de Habilidades:**
- Cada habilidad tiene 5 niveles máximo
- Multiplicadores: x1, x2, x3, x4, x5
- Habilidades más poderosas tienen multiplicadores más altos
- Las habilidades pueden tener dependencias (árbol de habilidades)

**Progresión de Experiencia:**

```
exp_requerida_nivel = base_exp × multiplicador_habilidad × nivel
```

**Ejemplos de Habilidades:**
- **Minería** (x2): Extracción de recursos de asteroides
  - Nivel 1: Minería básica
  - Nivel 5: Minería avanzada, acceso a minerales raros

- **Pilotaje de Fragatas** (x1): Permite usar naves clase Fragata
  - Dependencia: Ninguna
- **Pilotaje de Cruceros** (x3): Permite usar naves clase Crucero
  - Dependencia: Pilotaje de Fragatas Nivel 3
- **Armas de Energía** (x2): Uso de armas láser y plasma
- **Blindaje** (x2): Mejora armadura de la nave
- **Escudos** (x3): Mejora capacidad de escudos
- **Ingeniería** (x4): Fabricación de componentes
- **Comercio** (x2): Mejores precios en mercados
- **Negociación** (x3): Reducción de tarifas y mejores contratos
- **Liderazgo** (x5): Bonos a corporación
- **Investigación** (x4): Blueprints mejorados

**Ganancia de Experiencia:**
- Al completar acciones exitosamente
- Habilidad principal: 100% experiencia
- Habilidades secundarias: 30-50% experiencia
- Misiones otorgan experiencia fija
- Combate otorga experiencia según dificultad

**Sistema de Inyección de Habilidades:**

Los pilotos NO comienzan con todas las habilidades disponibles. Deben adquirirlas e inyectarlas primero.

**Estado de Habilidades:**
- **No Descubierta:** El piloto no la ha visto aún
- **Descubierta (No Inyectada):** Visible en el árbol de habilidades pero no entrenada. Se puede ver en la interfaz con estado "No Inyectada"
- **Inyectada Nivel 0:** La habilidad está en el cerebro del piloto pero sin entrenar
- **Inyectada Nivel 1-5:** Habilidad entrenada activamente

**Adquisición de Inyectores:**
- Los **Inyectores de Habilidad** son items que se compran con Créditos
- Cada inyector corresponde a una habilidad específica (ej: "Inyector de Minería")
- Solo pueden inyectarse en **Laboratorios** de estaciones
- Cada laboratorio tiene un **catálogo limitado** de inyectores disponibles
- Ejemplo: Un laboratorio en una estación minera tendrá inyectores de Minería, Refinamiento, Prospección
- Un laboratorio militar tendrá inyectores de Armas, Blindaje, Tácticas
- Los jugadores deben **viajar entre estaciones** para encontrar inyectores específicos
- Los inyectores también se pueden encontrar en el **Mercado** (vendidos por otros jugadores o NPCs)

**Proceso de Inyección:**
1. Comprar el inyector (de laboratorio o mercado)
2. Ir a un Laboratorio de cualquier estación
3. Inyectar la habilidad (instantáneo, consume el inyector)
4. La habilidad queda en nivel 0, lista para entrenar

**Entrenamiento de Niveles (1-5):**
- Una vez inyectada, se puede entrenar hasta nivel 5
- Cada nivel requiere **experiencia** ganada al usar la habilidad
- Alternativamente, se pueden comprar **"Aceleradores de Entrenamiento"** (items que otorgan exp directa)
- Requisitos de nivel:
  - Para entrenar nivel 1: Tener la habilidad inyectada (nivel 0)
  - Para nivel 2-5: Tener el nivel anterior completado + habilidades dependientes

**Costo de Inyectores:**
Basado en el multiplicador de la habilidad:

```
costo_inyector = base_cost × multiplicador_habilidad
```

Ejemplos:
- Inyector de Pilotaje de Fragatas (x1): 10,000 Créditos
- Inyector de Minería (x2): 20,000 Créditos
- Inyector de Escudos (x3): 30,000 Créditos
- Inyector de Ingeniería (x4): 40,000 Créditos
- Inyector de Liderazgo (x5): 50,000 Créditos

**Interfaz de Habilidades:**
Los jugadores pueden ver en su "Árbol de Habilidades":
- ✓ Habilidades inyectadas y su nivel actual
- 🔒 Habilidades descubiertas pero no inyectadas (con opción de buscar en mercado)
- ❓ Habilidades no descubiertas (se revelan al explorar estaciones o cumplir requisitos)

**Descubrimiento de Habilidades:**
- Al visitar un Laboratorio por primera vez, se "descubren" las habilidades de su catálogo
- Al leer descripciones de naves/módulos, se descubren sus requisitos
- Al hablar con agentes NPC o completar misiones especiales

### 2.3 Sistema de Acciones

**Tipos de Acciones:**

**Acciones Instantáneas:**
- Moverse entre módulos de estación
- Ver información de objetos
- Acceder a mercados
- Gestión de inventario
- Comunicación con otros jugadores

**Acciones de Tick:**
- Minería
- Combate
- Fabricación
- Refinamiento
- Viajes espaciales
- Reparaciones

**Características:**
- Todas las acciones están determinadas por la ubicación del piloto
- Requieren habilidades específicas
- Tienen porcentaje de éxito basado en skills
- Pueden tener acciones secundarias simultáneas
- Se pueden cancelar (perdiendo progreso)

**Cálculo de Éxito:**

```
chance_exito = base_chance × (1 + skill_level × 0.15) × ship_bonus × module_bonus
```

---

## 3. Creación de Cuenta y Piloto

### 3.1 Registro de Cuenta

**Campos Requeridos:**
- Nombre de usuario (único)
- Email (único, verificado)
- Contraseña (mínimo 8 caracteres, hash seguro)

**Restricciones:**
- Un piloto por cuenta
- La cuenta es permanente
- No se pueden eliminar cuentas con actividad reciente

### 3.2 Creación de Piloto

**Paso 1: Generación de Nombre**
- El sistema genera nombre y apellido aleatorios
- No puede ser elegido por el jugador
- Combinación de nombres de base de datos predefinida
- Formato: "[Nombre] [Apellido]"
- La fecha de creación es el "cumpleaños" del piloto

**Paso 2: Selección de Carrera Inicial**
Sistema extensible que define el punto de partida del jugador.

**Carreras Disponibles (Inicial):**

1. **Minero**
   - Habilidades iniciales:
     - Minería: Nivel 2
     - Pilotaje de Fragatas: Nivel 1
     - Refinamiento: Nivel 1
   - Nave inicial: Fragata Minera "Excavador MK-I"
   - Módulos iniciales:
     - 1x Láser de Minería Básico
     - 1x Expansor de Carga
   - Créditos iniciales: 50,000

2. **Contrabandista**
   - Habilidades iniciales:
     - Pilotaje de Fragatas: Nivel 2
     - Evasión: Nivel 2
     - Comercio: Nivel 1
   - Nave inicial: Fragata Rápida "Sombra"
   - Módulos iniciales:
     - 1x Propulsor Mejorado
     - 1x Camuflaje Básico
   - Créditos iniciales: 75,000

3. **Cazador de Recompensas**
   - Habilidades iniciales:
     - Pilotaje de Fragatas: Nivel 2
     - Armas de Proyectiles: Nivel 2
     - Rastreo: Nivel 1
   - Nave inicial: Fragata de Combate "Depredador"
   - Módulos iniciales:
     - 2x Cañón Automático Ligero
     - 1x Scanner de Combate
   - Créditos iniciales: 40,000

4. **Transportista**
   - Habilidades iniciales:
     - Pilotaje de Cargueros: Nivel 2
     - Navegación: Nivel 2
     - Comercio: Nivel 1
   - Nave inicial: Carguero Ligero "Mercante"
   - Módulos iniciales:
     - 2x Expansor de Carga
     - 1x Escudo Básico
   - Créditos iniciales: 60,000

**Paso 3: Selección de Facción de Origen**
Define relaciones iniciales y ubicación de inicio.

> Para más información sobre facciones, ver [PRD-Universe.md - Sistema de Facciones](./PRD-Universe.md#4-sistema-de-facciones)

---

## 25. Glosario

**BPO:** Blueprint Original - Plano de fabricación con usos infinitos
**BPC:** Blueprint Copy - Copia de plano con usos limitados
**DPS:** Damage Per Second - Daño por segundo
**KOS:** Kill On Sight - Matar a la vista
**NPC:** Non-Player Character - Personaje no jugador
**Tick:** Ciclo de tiempo del servidor donde se procesan acciones
**Wreck:** Restos de nave destruida
**m³:** Metro cúbico - Unidad de volumen en el juego
**T1/T2/T3:** Tech Level 1/2/3 - Nivel tecnológico de un item

---

## Navegación

- [← Anterior: PRD-Master.md](./PRD-Master.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-Universe.md](./PRD-Universe.md)
