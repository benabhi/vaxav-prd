# Universo, Navegación y Estaciones

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 4. Sistema de Facciones

### 4.1 Facciones NPC Principales (4)

**1. Confederación Vaxav**
- **Ideología:** Orden, comercio regulado, expansión controlada
- **Especialidad:** Industria y comercio
- **Relaciones iniciales:**
  - Liga Libre: -20 (Hostil)
  - Sindicato Técnico: +30 (Neutral amistoso)
  - Flota Nómada: 0 (Neutral)
- **Estaciones iniciales:** 8
- **Corporaciones:** 12
- **Bonos de facción:** +10% eficiencia de fabricación

**2. Liga Libre**
- **Ideología:** Libertad individual, libre mercado, capitalismo extremo
- **Especialidad:** Comercio y piratería
- **Relaciones iniciales:**
  - Confederación Vaxav: -20 (Hostil)
  - Sindicato Técnico: +10 (Neutral amistoso)
  - Flota Nómada: +20 (Amistoso)
- **Estaciones iniciales:** 6
- **Corporaciones:** 10
- **Bonos de facción:** +10% beneficios de comercio

**3. Sindicato Técnico**
- **Ideología:** Progreso tecnológico, meritocracia, investigación
- **Especialidad:** Investigación y naves avanzadas
- **Relaciones iniciales:**
  - Confederación Vaxav: +30 (Neutral amistoso)
  - Liga Libre: +10 (Neutral amistoso)
  - Flota Nómada: -10 (Neutral hostil)
- **Estaciones iniciales:** 5
- **Corporaciones:** 8
- **Bonos de facción:** +15% velocidad de investigación

**4. Flota Nómada**
- **Ideología:** Exploración, supervivencia, independencia
- **Especialidad:** Exploración y combate
- **Relaciones iniciales:**
  - Confederación Vaxav: 0 (Neutral)
  - Liga Libre: +20 (Amistoso)
  - Sindicato Técnico: -10 (Neutral hostil)
- **Estaciones iniciales:** 4
- **Corporaciones:** 6
- **Bonos de facción:** +10% velocidad de viaje

### 4.2 Facciones NPC Secundarias

- **Piratas del Cinturón:** Hostiles a todos, controlan zonas peligrosas
- **Mercaderes Independientes:** Neutrales, proveen comercio
- **Culto de la Singularidad:** Misteriosos, tecnología alienígena
- **Salvadores del Vacío:** Rescate y recuperación

### 4.3 Facciones de Jugadores

- Las corporaciones de jugadores pueden formar facciones
- Requiere mínimo 5 corporaciones
- Pueden declarar guerra a otras facciones
- Controlan territorio y estaciones
- Sistema de diplomacia entre facciones

### 4.4 Sistema de Relación

**Escala de Relación:** -100 a +100

- **100 a -60:** Guerra (KOS - Kill on Sight)
- **59 a -20:** Hostil
- **19 a +19:** Neutral
- **+20 a +49:** Amistoso
- **+50 a +79:** Aliado
- **+80 a +100:** Leal

**Formas de Ganar/Perder Relación:**
- Completar misiones: +5 a +50
- Matar NPCs hostiles: +2 a +10
- Matar NPCs amistosos: -20 a -50
- Comerciar: +1 por cada 100,000 créditos
- Donar recursos: Variable

---

## 5. Sistema de Navegación y Ubicación

### 5.1 Jerarquía de Ubicaciones

```
Sistema Solar
├── Estrella
├── Planetas
│   ├── Lunas
│   │   └── Estaciones Espaciales
│   │       └── Módulos
├── Campos de Asteroides
├── Anomalías Espaciales
└── Stargates
```

### 5.2 Sistemas Solares

**Sistema Inicial: Vaxav**
- Sistema fijo, no procedural
- 1 Estrella (Vaxav)
- 8 Planetas predefinidos
- Múltiples lunas
- 15+ estaciones iniciales
- Campos de asteroides
- 0-4 Stargates (desbloqueables)

**Nomenclatura:**

```
Sistema: Vaxav
Estrella: Vaxav
Planeta: Vaxav I, Vaxav II, ..., Vaxav VIII
Luna: Vaxav I - Luna 1, Vaxav I - Luna 2
Estación: Vaxav I - Luna 1 - [Nombre Estación]
Ejemplo: Vaxav I - Luna 1 - Puerto Estelar Génesis
```

### 5.3 Progreso de Sistema

Barra de progreso que desbloquea contenido nuevo.

**Fuentes de Progreso:**
- Fabricación de objetos: +1 por item
- Completar misiones: +10 a +100
- Comercio: +1 por cada 500,000 créditos
- Combates: +5 a +50
- Exploración: +20 por descubrimiento
- Construcción de estaciones: +500

**Umbrales de Desbloqueo:**
- **1,000 puntos:** Primer Stargate
- **5,000 puntos:** Nuevas corporaciones NPC
- **10,000 puntos:** Segunda facción NPC secundaria
- **25,000 puntos:** Segundo Stargate
- **50,000 puntos:** Tercer Stargate
- **100,000 puntos:** Cuarto Stargate

### 5.4 Generación Procedural de Sistemas

Los sistemas nuevos se generan al cruzar Stargates.

**Parámetros de Generación:**
- Número de planetas: 3-12
- Tipo de estrella: Enana Roja, Amarilla, Gigante
- Recursos predominantes
- Dificultad de NPCs
- Número de lunas por planeta
- Estaciones NPC iniciales: 1-5

**Librería de Generación:**
- Sistema modular y extensible
- Seeds guardados en DB para reproducibilidad
- Validación de recursos equilibrados
- Nombres generados proceduralmente

### 5.5 Tipos de Planetas

Los planetas del universo VAXAV tienen 7 tipos distintos, cada uno con recursos específicos.

#### 5.5.1 Planeta Rocoso

**Características:**
- **Superficie:** Rocas áridas, cráteres, valles secos
- **Atmósfera:** Ninguna o muy tenue
- **Gravedad:** Media (0.8-1.2G)
- **Temperatura:** Extrema (según distancia estrella)

**Recursos Primarios:**
- Ferrita (abundante)
- Cobre Estelar (abundante)
- Silicatos (abundante)
- Titanita (común)
- Magnetita Pura (poco común)

**Recursos Secundarios:**
- Duralinio Espacial (raro en zonas específicas)
- Agua (escasa, hielo en polos)

**Método Extracción:**
- Escaneo planetario + instalación de extractores
- Skill requerida: Minería, Escaneo Planetario

**Ejemplo:** Planetas similares a Mercurio, Marte

#### 5.5.2 Planeta Volcánico

**Características:**
- **Superficie:** Lagos de lava, montañas volcánicas, cenizas
- **Atmósfera:** Tóxica (SO₂, CO₂)
- **Gravedad:** Media-Alta (1.0-1.5G)
- **Temperatura:** Muy alta

**Recursos Primarios:**
- Titanita (abundante)
- Magnetita Pura (abundante)
- Duralinio Espacial (común)
- Cristales de Zafiro (poco común, en cámaras magmáticas)

**Recursos Secundarios:**
- Ferrita (común)
- Silicatos (abundante)
- Adamantita (muy raro, núcleo profundo)

**Método Extracción:**
- Requiere extractores resistentes al calor
- Skill requerida: Minería, Escaneo Planetario (nivel 2+)

**Ejemplo:** Io (luna de Júpiter), Venus

#### 5.5.3 Planeta Joviano (Gigante Gaseoso)

**Características:**
- **Superficie:** No tiene, atmósfera gaseosa profunda
- **Atmósfera:** Hidrógeno, Helio, trazas metano/amoníaco
- **Gravedad:** Muy alta (2.0-3.0G en capas altas)
- **Temperatura:** Fría en capas altas, muy caliente en profundidad

**Recursos Primarios:**
- Hidrógeno (abundante)
- Helio (abundante)
- Deuterio (común)
- Nitrógeno (poco común)

**Recursos Secundarios:**
- Plasma (raro, en tormentas eléctricas)
- Xenón (muy raro, capas profundas)

**Método Extracción:**
- Recolección atmosférica con naves especializadas
- Skill requerida: Recolección de Gas (nivel 1+)

**Ejemplo:** Júpiter, Saturno, Urano

#### 5.5.4 Planeta Helado

**Características:**
- **Superficie:** Hielo, nieve, océanos congelados subsuperficiales
- **Atmósfera:** Tenue (nitrógeno, metano) o inexistente
- **Gravedad:** Baja-Media (0.3-0.9G)
- **Temperatura:** Muy baja (-150°C a -220°C)

**Recursos Primarios:**
- Agua (abundante, en forma de hielo)
- Hidrógeno (común, hielo de hidrógeno)
- Nitrógeno (abundante)
- Deuterio (poco común, hielo deuterado)

**Recursos Secundarios:**
- Biomasa (raro, si hay océanos subsuperficiales)
- Proteínas (muy raro, vida microbiana)
- Antimateria (trazas, en depósitos antiguos)

**Método Extracción:**
- Perforación de hielo con extractores criogénicos
- Skill requerida: Extracción Criogénica (nivel 1+), Escaneo Planetario

**Ejemplo:** Europa, Encélado, Plutón

#### 5.5.5 Planeta Oceánico

**Características:**
- **Superficie:** 90-100% océano líquido, islas pequeñas
- **Atmósfera:** Respirable o casi respirable (O₂, N₂)
- **Gravedad:** Media (0.9-1.1G)
- **Temperatura:** Templada (+5°C a +40°C)

**Recursos Primarios:**
- Agua (abundante)
- Biomasa (abundante, algas y plancton)
- Proteínas (abundante, vida marina)
- Algas (abundante)

**Recursos Secundarios:**
- Nanobots (poco común, si hay civilizaciones antiguas sumergidas)
- Cristales Vivos (raro, formaciones biológicas)
- Silicatos (común, en fondo marino)

**Método Extracción:**
- Extracción submarina, cultivo de algas
- Skill requerida: Bioprospección (nivel 1+), Escaneo Planetario

**Ejemplo:** Planetas hipotéticos tipo "mundo océano"

#### 5.5.6 Planeta Vital (Terrestre)

**Características:**
- **Superficie:** Continentes, océanos, ecosistemas diversos
- **Atmósfera:** Respirable (N₂, O₂)
- **Gravedad:** Media (0.8-1.2G)
- **Temperatura:** Templada (-10°C a +35°C)

**Recursos Primarios:**
- Biomasa (abundante)
- Agua (abundante)
- Proteínas (abundante)
- Algas (abundante)
- Nanobots (poco común, si hay civilizaciones)

**Recursos Secundarios:**
- Cristales Vivos (poco común, bosques cristalinos)
- Esporas (raro, hongos especiales)
- Genoma Alienígena (muy raro, vida inteligente extinta)
- Silicatos (común)
- Ferrita (poco común)

**Método Extracción:**
- Extracción superficial, agricultura espacial, bioprospección
- Skill requerida: Bioprospección (nivel 2+), Escaneo Planetario

**Ejemplo:** Tierra, planetas tipo "segunda Tierra"

#### 5.5.7 Planeta Fragmentado (Restos Planetarios)

**Características:**
- **Superficie:** Fragmentos planetarios, núcleo expuesto
- **Atmósfera:** Inexistente
- **Gravedad:** Baja (0.1-0.5G)
- **Temperatura:** Extrema

**Recursos Primarios:**
- Adamantita (común, núcleo expuesto)
- Neutronium (poco común, fragmentos del núcleo)
- Duralinio Espacial (abundante)
- Cristales de Zafiro (común)

**Recursos Secundarios:**
- Magnetita Pura (abundante)
- Titanita (abundante)
- Antimateria (raro, remanente de evento destructivo)
- Materia Oscura (muy raro, origen del evento)

**Método Extracción:**
- Minería de fragmentos flotantes
- Skill requerida: Minería (nivel 3+), Escaneo Planetario (nivel 3+)

**Ejemplo:** Cinturón de asteroides (si fuera un planeta destruido), Faetón

**Distribución de Planetas en Sistemas:**
- Cada sistema tiene 3-12 planetas
- Distribución típica: 30% Rocosos, 20% Jovianos, 15% Helados, 15% Volcánicos, 10% Oceánicos, 8% Vitales, 2% Fragmentados
- Los planetas Vitales y Fragmentados son los más raros

### 5.6 Sistema de Seguridad

Cada sistema solar tiene un **nivel de seguridad** decimal de 0.0 a 1.0 que determina la presencia de policía NPC, reglas de combate y recursos disponibles.

#### 5.6.1 Niveles de Seguridad

**Nivel 1.0 (Seguridad Máxima)**
- **Descripción:** Sistemas centrales de facciones principales
- **Policía NPC:** "Albatross" - Respuesta instantánea (1 tick)
- **Combate PvP:** Prohibido (atacar resulta en KOS instantáneo + intervención Albatross)
- **Consecuencias:** -100 standing con facción, pérdida de nave garantizada
- **Recursos:** Tier 1 únicamente (Ferrita, Cobre Estelar, Hidrógeno, Biomasa básica)
- **Características:**
  - Estaciones NPC seguras
  - Comercio protegido
  - Zona de aprendizaje para nuevos pilotos

**Nivel 0.5 - 0.9 (Seguridad Alta)**
- **Descripción:** Sistemas colonizados con presencia militar
- **Policía NPC:** Respuesta rápida (3-5 ticks)
- **Combate PvP:** Permitido con penalizaciones severas
  - Atacar: -50 standing con facción
  - Matar: -80 standing + marca criminal temporal (12 horas)
  - Albatross responde y destruye al atacante si continúa en zona
- **Recursos:** Tier 1-2 (Titanita, Magnetita, Deuterio, Proteínas)
- **Características:**
  - Cinturones de asteroides básicos
  - Algunos cinturones de hielo
  - Estaciones NPC frecuentes

**Nivel 0.1 - 0.4 (Seguridad Baja)**
- **Descripción:** Sistemas fronterizos, poco patrullados
- **Policía NPC:** Respuesta lenta (10-15 ticks) solo en estaciones
- **Combate PvP:** Permitido con penalizaciones leves
  - Atacar: -10 standing
  - Matar: -20 standing
  - Albatross NO interviene en espacio abierto, solo defiende estaciones
- **Recursos:** Tier 1-3 (Duralinio, Cristales de Zafiro, Plasma, Xenón, Nanobots)
- **Características:**
  - Cinturones de asteroides ricos
  - Cinturones de hielo con recursos raros
  - Nebulosas de gas (Tier 2-3)
  - Estaciones NPC escasas

**Nivel 0.0 (Null-Sec / Espacio Nulo)**
- **Descripción:** Territorio salvaje sin ley
- **Policía NPC:** Inexistente
- **Combate PvP:** Sin restricciones ni penalizaciones
- **Recursos:** Tier 1-4 (Adamantita, Neutronium, Antimateria, Materia Oscura, Genoma Alienígena)
- **Características:**
  - Cinturones de asteroides exóticos
  - Cinturones de hielo con Antimateria/Materia Oscura
  - Nebulosas de gas Tier 4
  - Planetas Fragmentados y Vitales más frecuentes
  - Estaciones solo de jugadores
  - Sitios de exploración legendarios
  - Control territorial por corporaciones

#### 5.6.2 Fuerza Policial "Albatross"

**Descripción:**
- Fuerza de seguridad NPC multifacción
- Opera en sistemas 0.5 - 1.0
- Naves: Fragatas (sec 0.5-0.7), Cruceros (sec 0.8-0.9), Acorazados (sec 1.0)

**Mecánica de Respuesta:**
1. **Detección:** Al iniciarse combate no consentido
2. **Alerta:** Mensaje de advertencia al agresor (5 segundos para detenerse)
3. **Intervención:** Albatross warp in y ataca al criminal
4. **Duración:** Hasta destruir al criminal o que escape del sistema

**Poder Relativo:**
- Sec 1.0: Albatross destruye fragata T1 en 2-3 ticks
- Sec 0.8: Albatross destruye fragata T1 en 5-7 ticks
- Sec 0.5: Albatross destruye fragata T1 en 10-12 ticks

**Evasión:**
- El agresor puede escapar saltando a otro sistema antes de ser destruido
- Marca criminal persiste entre sesiones
- Entrar a estación en sistema sec alto con marca criminal = Albatross ataca al desatracar

### 5.7 Cinturones de Asteroides

Los cinturones de asteroides existen en todos los sistemas y contienen recursos metálicos.

**Características:**
- **Ubicación:** Orbitan la estrella, entre planetas
- **Cantidad por sistema:** 1-5 cinturones
- **Asteroides por cinturón:** 50-200 (regeneran cada 48 horas)
- **Tipos de asteroides:** Según nivel de seguridad del sistema

**Distribución de Recursos por Seguridad:**
- **Sec 1.0:** Solo Ferrita, Cobre Estelar, Silicatos (Tier 1)
- **Sec 0.5-0.9:** Tier 1-2 (Titanita, Magnetita Pura)
- **Sec 0.1-0.4:** Tier 1-3 (Duralinio Espacial, Cristales de Zafiro)
- **Sec 0.0:** Tier 1-4 (Adamantita, Neutronium)

**Mecánica de Minería:**
1. Viajar al cinturón (acción de ticks)
2. Seleccionar asteroide
3. Iniciar minería (consume ticks según skill y equipo)
4. Recursos van al cargo de la nave
5. Asteroide se agota tras X extracciones

**Regeneración:**
- Los asteroides agotados desaparecen
- Cada 48 horas (288 ticks), nuevos asteroides aparecen
- La composición es aleatoria dentro del tier del sistema

### 5.8 Cinturones de Hielo

Los cinturones de hielo son zonas especiales con recursos volátiles congelados.

**Características:**
- **Ubicación:** Zonas exteriores del sistema, más allá de los planetas
- **Cantidad por sistema:** 0-2 cinturones (solo en sistemas con planetas Helados o Jovianos)
- **Bloques de hielo:** 20-100 por cinturón
- **Regeneración:** 72 horas (432 ticks)

**Tipos de Hielo:**
- **Hielo de Agua** (Tier 1): Agua, Hidrógeno básico
- **Hielo de Deuterio** (Tier 2): Deuterio, Nitrógeno
- **Hielo de Plasma** (Tier 3): Plasma congelado, Xenón
- **Hielo Exótico** (Tier 4): Antimateria, Materia Oscura (solo sec 0.0)

**Distribución por Seguridad:**
- **Sec 1.0:** No existen cinturones de hielo
- **Sec 0.5-0.9:** Hielo Tier 1-2
- **Sec 0.1-0.4:** Hielo Tier 2-3
- **Sec 0.0:** Hielo Tier 3-4

**Mecánica de Extracción:**
1. Requiere módulo "Extractor Criogénico" en la nave
2. Requiere skill "Extracción Criogénica" (nivel según tier)
3. Proceso similar a minería pero con ticks diferentes
4. Los bloques de hielo son más grandes (más recursos por bloque)

**Riesgo vs Recompensa:**
- Los cinturones de hielo en sec baja son objetivos de piratería
- Mayor riesgo = mejores recursos (Antimateria vale 100x más que Agua)

### 5.9 Nebulosas de Gas

Las nebulosas son nubes de gas cósmico donde se recolectan recursos gaseosos.

**Características:**
- **Ubicación:** Zonas aleatorias del sistema, pueden moverse lentamente
- **Cantidad por sistema:** 0-3 nebulosas
- **Tamaño:** Variable (pequeña 10km³, grande 100km³)
- **Visibilidad:** Reducida dentro de la nebulosa (-30% alcance sensores)
- **Regeneración:** 96 horas (576 ticks)

**Tipos de Nebulosas:**
- **Nebulosa de Hidrógeno** (Tier 1): Hidrógeno, Helio
- **Nebulosa de Nitrógeno** (Tier 2): Nitrógeno, Deuterio
- **Nebulosa de Plasma** (Tier 3): Plasma, Xenón
- **Nebulosa Oscura** (Tier 4): Antimateria, Materia Oscura

**Distribución por Seguridad:**
- **Sec 1.0:** No existen nebulosas
- **Sec 0.5-0.9:** Nebulosas Tier 1-2 (raras)
- **Sec 0.1-0.4:** Nebulosas Tier 2-3
- **Sec 0.0:** Nebulosas Tier 3-4

**Mecánica de Recolección:**
1. Requiere módulo "Recolector de Gas" en la nave
2. Requiere skill "Recolección de Gas" (nivel según tier)
3. La nave debe permanecer estacionaria durante la recolección
4. Rendimiento: X unidades de gas por tick (según skill y módulo)

**Peligros:**
- **Tormentas de Plasma:** Eventos aleatorios que dañan naves (cada 50 ticks, 10% probabilidad)
- **Visibilidad reducida:** Dificulta detectar enemigos
- **Piratas:** Las nebulosas son zonas de emboscada perfectas

**Ventaja Táctica:**
- Las naves con alto Sigilo pueden ocultarse en nebulosas
- Los piratas usan nebulosas para tender trampas

---

## 6. Estaciones Espaciales

### 6.1 Características Generales

- **Ubicación:** Siempre orbitan lunas
- **Propiedad:** NPC o Corporaciones de jugadores
- **Acceso:** Público, Corporación, Alianza, Privado
- **Capacidad:** Limitada por nivel de hangar

**Atributos de Estación:**

```json
{  "nombre": "Puerto Estelar Génesis",  "descripcion": "La primera y más grande estación del sistema Vaxav...",  "corporacion_id": 1,  "faccion_id": 1,  "sistema_id": 1,  "planeta_id": 1,  "luna_id": 1,  "nivel_acceso": "publico",  "estado": "operacional",  "hangar_capacidad_actual": 45,  "hangar_capacidad_maxima": 100,  "modulos": []}
```

### 6.2 Módulos de Estación

**Estructura de Módulo:**
- **Nivel:** 1-5
- **Estado:** Construcción, Operacional, Dañado, Deshabilitado
- **Energía requerida:** Sí/No
- **Costo de construcción:** Recursos + Créditos
- **Tiempo de construcción:** Ticks

### 6.2.1 Puente de Mando

**Obligatorio** - Módulo inicial de toda estación.

**Nivel 1:**
- Gestión básica de la estación
- Ver información de módulos
- Asignar permisos básicos

**Nivel 2:**
- Gestión de roles
- Ver tráfico de naves
- Logs de actividad

**Nivel 3:**
- Establecer impuestos de atracaje
- Gestión de defensa (torretas)
- Contratos de estación

**Nivel 4:**
- Sistema de alertas automático
- Gestión avanzada de energía
- Bloqueo de pilotos

**Nivel 5:**
- Transferencia de propiedad
- Sistema de seguridad IA
- Clonación de configuración a otras estaciones

### 6.2.2 Hangar

Almacenamiento y mantenimiento de naves.

**Nivel 1:**
- Capacidad: 20 naves
- Acciones: Atracar, Despegar, Ver nave

**Nivel 2:**
- Capacidad: 50 naves
- Acciones: +Reparación básica (casco)
- Costo reparación: -10%

**Nivel 3:**
- Capacidad: 100 naves
- Acciones: +Reparación completa (escudos, armadura)
- Reconfiguración de módulos

**Nivel 4:**
- Capacidad: 200 naves
- Acciones: +Reparación automática
- Mantenimiento preventivo

**Nivel 5:**
- Capacidad: 500 naves
- Acciones: +Mejoras de nave
- Velocidad de reparación +50%

### 6.2.3 Laboratorio

Centro de investigación, inyección de habilidades y clonación.

**Funcionalidades Principales:**
- **Catálogo de Inyectores:** Cada laboratorio tiene un inventario limitado de inyectores según su especialización
- **Inyección de Habilidades:** Proceso instantáneo que desbloquea una habilidad en nivel 0
- **Clonación:** Puntos de respawn para cuando el piloto muere
- **Investigación:** Mejora de Blueprints (niveles superiores)

**Nivel 1:**
- **Catálogo:** 5-8 inyectores básicos (x1, x2)
- Ejemplo estación minera: Minería, Refinamiento, Prospección, Pilotaje Fragatas
- Ejemplo estación militar: Armas Proyectiles, Armas Energía, Blindaje, Pilotaje Fragatas
- **Precio inyectores:** 100% del costo base
- 1 punto de clonación activo
- **Descubrimiento:** Visitar el laboratorio descubre todas las habilidades de su catálogo

**Nivel 2:**
- **Catálogo:** 10-15 inyectores (x1, x2, x3)
- **Precio inyectores:** 95% del costo base
- 3 puntos de clonación
- Ver árbol completo de habilidades con progreso
- Aceleradores de entrenamiento disponibles (+exp a skills)

**Nivel 3:**
- **Catálogo:** 15-25 inyectores (x1, x2, x3, x4)
- **Precio inyectores:** 90% del costo base
- 5 puntos de clonación
- Investigación de Blueprints (BPO)
- Atributos de la habilidad visible (bonificadores exactos)

**Nivel 4:**
- **Catálogo:** 25-40 inyectores (x1, x2, x3, x4, x5)
- **Precio inyectores:** 85% del costo base
- 10 puntos de clonación
- Mejora de Blueprints (BPO → BPC mejorado)
- Extracción de experiencia (+10% exp en todas las acciones mientras atracado)
- "Skill Planner" - Herramienta que muestra camino óptimo para alcanzar habilidad objetivo

**Nivel 5:**
- **Catálogo:** 40+ inyectores (todas las categorías, incluyendo raras)
- **Precio inyectores:** 80% del costo base
- Clonación instantánea (sin cooldown)
- Investigación avanzada (Blueprints T3)
- Transferencia de skills limitada (redistribuir exp entre skills similares, con pérdida)
- "Neural Backup" - Backup automático de skills cada 24h

**Especialización de Laboratorios por Tipo de Estación:**

**Estaciones Mineras/Industriales:**
- Inyectores: Minería, Refinamiento, Prospección, Geología, Ingeniería, Producción en Masa

**Estaciones Militares:**
- Inyectores: Armas (todas), Blindaje, Escudos, Tácticas, Sistemas de Defensa, Liderazgo

**Estaciones de Comercio:**
- Inyectores: Comercio, Negociación, Contabilidad, Pilotaje Cargueros, Logística

**Estaciones de Investigación (Sindicato Técnico):**
- Inyectores: Investigación, Ciencias, Ingeniería Avanzada, Cibernética, Astrofísica

**Estaciones de Exploración:**
- Inyectores: Navegación, Escaneo, Análisis Espacial, Cartografía, Supervivencia

**Importante:**
- No todos los inyectores están disponibles en todas las estaciones
- Los jugadores deben explorar y encontrar laboratorios especializados
- Los inyectores también se pueden comprar/vender en el **Mercado** entre jugadores (ver [PRD-Economy.md](./PRD-Economy.md))
- Algunos inyectores muy raros solo se obtienen como recompensa de misiones especiales

### 6.2.4 Habitáculos

Área de descanso y recuperación.

**Nivel 1:**
- 10 habitaciones
- Regeneración básica de "fatiga"
- Acceso a chat global

**Nivel 2:**
- 25 habitaciones
- Regeneración +25% más rápida
- Bonos temporales de descanso

**Nivel 3:**
- 50 habitaciones
- Regeneración +50% más rápida
- Sala de reuniones corporativa

**Nivel 4:**
- 100 habitaciones
- Bonos permanentes leves
- Sala de entrenamiento (+5% exp)

**Nivel 5:**
- 250 habitaciones
- Bonos permanentes moderados
- Centro social (mini-juegos, eventos)

### 6.2.5 Mercado

Compra y venta de bienes.

**Nivel 1:**
- 5 puestos de vendedor
- Órdenes de compra/venta básicas
- Comisión: 5%

**Nivel 2:**
- 15 puestos
- Órdenes avanzadas (límite de precio)
- Comisión: 4%
- Historial de precios

**Nivel 3:**
- 50 puestos
- Contratos de transporte
- Comisión: 3%
- Subastas

**Nivel 4:**
- 150 puestos
- Contratos de fabricación
- Comisión: 2%
- Sistema de intermediarios

**Nivel 5:**
- 500 puestos
- Mercado regional (conecta varias estaciones)
- Comisión: 1%
- Análisis de mercado IA

### 6.2.6 Astillero

Construcción de naves.

**Nivel 1:**
- Construcción de fragatas
- 1 bahía de construcción
- Velocidad base

**Nivel 2:**
- +Construcción de cruceros
- 2 bahías
- Velocidad +15%

**Nivel 3:**
- +Construcción de cargueros
- 3 bahías
- Velocidad +30%
- Descuento materiales 5%

**Nivel 4:**
- +Construcción de acorazados
- 5 bahías
- Velocidad +50%
- Descuento materiales 10%

**Nivel 5:**
- +Construcción de capitales
- 10 bahías
- Velocidad +75%
- Descuento materiales 20%
- Construcción simultánea

### 6.2.7 Sala de Ingeniería

Fabricación de módulos, items y componentes.

**Nivel 1:**
- Fabricación de módulos T1 (Tech 1)
- 2 líneas de producción
- Velocidad base

**Nivel 2:**
- +Módulos T2
- 5 líneas
- Velocidad +20%
- Reciclaje de items

**Nivel 3:**
- +Municiones y cargas
- 10 líneas
- Velocidad +40%
- Producción en masa

**Nivel 4:**
- +Módulos T3
- 20 líneas
- Velocidad +60%
- Reverse engineering

**Nivel 5:**
- +Módulos de estación
- 50 líneas
- Velocidad +100%
- Innovación (crear BPC mejorados)

### 6.2.8 Bodegas

Almacenamiento de recursos e items.

**Nivel 1:**
- Capacidad: 100,000 m³
- Acceso básico

**Nivel 2:**
- Capacidad: 500,000 m³
- Divisiones de almacén

**Nivel 3:**
- Capacidad: 2,000,000 m³
- Almacén corporativo
- Sistema de logs

**Nivel 4:**
- Capacidad: 10,000,000 m³
- Almacén de alianza
- Gestión automática

**Nivel 5:**
- Capacidad: 50,000,000 m³
- Refrigeración (items perecederos)
- Compresión de recursos

---

## 14. Sistema de Exploración

### 14.1 Escaneo de Naves

Desde cualquier ubicación espacial (no estación), los pilotos pueden escanear para detectar otras naves.

**Mecánica:**
- Depende de habilidad "Rastreo" del escaneador vs "Sigilo" del objetivo
- **Fórmula de detección:**

```
probabilidad_detectar = 50% + (nivel_rastreo × 10%) - (nivel_sigilo_objetivo × 8%)
```

- Si se detecta: Muestra nombre piloto, clase de nave, distancia aproximada
- Si NO se detecta: La nave permanece oculta
- **Cooldown:** 1 tick entre escaneos
- **Costo:** No consume recursos, pero la nave debe estar estacionaria

**Contramedidas:**
- Naves con módulos de "Camuflaje" aumentan Sigilo temporalmente
- Estar dentro de nebulosas otorga +20% Sigilo
- Moverse reduce Sigilo en -15%

### 14.2 Escaneo Planetario

Los pilotos pueden escanear planetas para descubrir recursos y generar "Datos de Exploración" vendibles.

**Requisitos:**
- Módulo: "Scanner Planetario" equipado en la nave
- Skill: "Escaneo Planetario" (nivel determina calidad del escaneo)
- Ubicación: Misma ubicación espacial que el planeta

**Proceso:**
1. El piloto selecciona un planeta sin escanear (o parcialmente escaneado)
2. Inicia el escaneo (consume 3-10 ticks según nivel skill y módulo)
3. Al completar, se genera un **Nivel de Exploración** (1-100)
4. Se crea un item "Datos de Exploración - [Nombre Planeta]" en el inventario

**Nivel de Exploración:**
- Determinado por: Skill + Módulo + Tipo de Planeta + Azar
- **Fórmula:**

```
nivel_exploracion = min(100,
  (skill_escaneo × 15) +
  (calidad_modulo × 10) +
  random(1, 20) -
  (dificultad_planeta × 5)
)
```

- **Dificultad por tipo de planeta:**
  - Rocoso, Joviano: 1
  - Volcánico, Helado: 2
  - Oceánico, Vital: 3
  - Fragmentado: 4

**Información Revelada por Nivel:**
- **Nivel 1-20:** Tipo de planeta, recursos Tier 1 presentes
- **Nivel 21-40:** + Recursos Tier 2, abundancia aproximada
- **Nivel 41-60:** + Recursos Tier 3, ubicaciones óptimas de extracción
- **Nivel 61-80:** + Recursos Tier 4, presencia de anomalías
- **Nivel 81-100:** + Datos completos, coordenadas exactas, posibles sitios arqueológicos

**Registro de Primer Descubridor:**
- Si el planeta NUNCA fue escaneado antes, el piloto queda registrado como "Primer Descubridor"
- El nombre del piloto aparece en la información pública del planeta
- Bonificación: +100 puntos de progreso del sistema
- El "Primer Descubridor" recibe un pequeño royalty (1%) sobre las ventas de Datos de Exploración de ese planeta

**Venta de Datos:**
- Los "Datos de Exploración" son items vendibles en el Mercado
- Precio sugerido: 5,000₡ - 500,000₡ según nivel de exploración y recursos presentes
- Los NPCs pueden comprarlos automáticamente
- Otros jugadores pueden comprarlos para establecer extractores sin escanear ellos mismos

### 14.3 Escaneo de Recursos en Asteroides

En cinturones de asteroides, cinturones de hielo y nebulosas.

**Mecánica:**
- Habilidad: "Prospección" (para asteroides y hielo) o "Recolección de Gas" (para nebulosas)
- Permite ver la composición exacta de un asteroide/hielo/nube antes de extraer
- **Sin prospección:** Solo se ven tipos generales ("Asteroide Metálico")
- **Con prospección:** Se ven minerales específicos y cantidad estimada

**Ejemplo:**
- Sin Prospección: "Asteroide Metálico - Desconocido"
- Prospección Nivel 1: "Asteroide Metálico - Ferrita (abundante)"
- Prospección Nivel 3: "Asteroide Metálico - Ferrita 250u, Titanita 50u, Duralinio 5u"
- Prospección Nivel 5: "Asteroide Metálico - Ferrita 247u (±10), Titanita 52u (±5), Duralinio 6u (±1)"

### 14.4 Sitios de Exploración Temporales

Sitios especiales que aparecen aleatoriamente en sistemas y desaparecen tras cierto tiempo o después de ser completados.

#### 14.4.1 Tipos de Sitios Temporales

**1. Sitios de Combate (Combat Sites)**
- **Descripción:** Naves NPC hostiles (piratas, drones rebeldes)
- **Tiers:** T1 (fácil) a T4 (muy difícil)
- **Recompensas:** Loot de naves destruidas, créditos, módulos raros
- **Duración:** 24-48 horas desde aparición
- **Detección:** Skill "Exploración" + Scanner de Combate

**2. Campos de Asteroides Ricos (Rich Ore Sites)**
- **Descripción:** Asteroides con recursos Tier 3-4
- **Recompensas:** Duralinio Espacial, Adamantita, Neutronium
- **Duración:** 12-24 horas (o hasta agotar asteroides)
- **Detección:** Skill "Prospección" (nivel 3+)

**3. Sitios Ancestrales (Ancestral Sites)**
- **Descripción:** Categoría unificada que reemplaza Relic y Data Sites. Cada instancia es uno de 4 tipos aleatorios de sitios de civilizaciones antiguas con mecánicas únicas
- **Subtipo desconocido:** Al detectar el sitio, aparece como "??? Sitio Ancestral [Tier X]" - el tipo exacto se revela al llegar
- **Tipos posibles:**
  1. **Complejo Precursor Abandonado** (30% probabilidad)
     - Estructuras militares/industriales/tecnológicas de civilización precursora
     - Mecánica: Explorar salas (3-7 salas conectadas), resolver puzzles ambientales
     - Recompensas: Fragmentos de Diseño (combinar para Chip de Diseño), Artefactos Precursores
     - Duración: 48-96 ticks (8-16 horas)
     - Requiere: Arqueología Espacial Nivel 2+

  2. **Derelicto Generacional** (25% probabilidad)
     - Naves coloniales gigantes abandonadas hace siglos
     - Mecánica: Hackear terminales (Puente, Motores, Bodegas, Criocámaras), evitar peligros
     - Recompensas: Núcleos de Datos (vendibles o descifrables en Laboratorio)
     - Duración: 36-72 ticks (6-12 horas)
     - Requiere: Hackeo Nivel 2+

  3. **Laboratorio de Investigación Perdido** (25% probabilidad)
     - Estaciones experimentales con IA corrupta
     - Mecánica: Negociar con IA (diplomacia/engaño/hackeo/ciencias), resolver minijuegos científicos
     - Recompensas: Prototipos Experimentales T3 (blueprints únicos), Documentos de Investigación
     - Duración: 48-120 ticks (8-20 horas)
     - Requiere: Ciencias Nivel 2+ (mejor opción) o Hackeo Nivel 5+

  4. **Campo de Escombros Alienígena** (20% probabilidad)
     - Tecnología de origen no-humano, diseño completamente ajeno
     - Mecánica: Recolectar Fragmentos Xeno, analizar con probabilidad creciente según cantidad
     - Recompensas: Esquemas Xenotecnología (blueprints exóticos), Fragmentos Xeno (vendibles), Materiales exóticos
     - Duración: 24-48 ticks (4-8 horas)
     - Requiere: Análisis Xenotecnológico Nivel 1+

- **Detección:** Skill "Exploración" (nivel 2+)
- **Tiers:** T1-T4 según seguridad del sistema
- **Sistema de fragmentos/núcleos:** Diferentes formas de obtener blueprints:
  - Chips de Diseño: Desbloquean blueprint inmediato
  - Núcleos de Datos: Vendibles o descifrables (12 ticks) para blueprint aleatorio
  - Prototipos Experimentales: Blueprints T3 únicos con stats ligeramente variables
  - Esquemas Xenotecnología: Blueprints exóticos con estética alienígena

**5. Nubes de Gas Exóticas (Gas Sites)**
- **Descripción:** Nebulosas temporales con gases Tier 3-4
- **Recompensas:** Plasma, Xenón, Antimateria, Materia Oscura
- **Duración:** 6-12 horas
- **Peligro:** Pueden contener NPCs o explotar al recolectar (daño AOE)
- **Detección:** Skill "Recolección de Gas" (nivel 3+)

**6. Agujeros de Gusano (Wormholes)**
- **Descripción:** Conexiones temporales a otros sistemas (incluso no descubiertos)
- **Mecánica:** Al atravesar, te lleva a un sistema aleatorio (puede ser sec 0.0)
- **Duración:** 1-6 horas, masa de naves limitada antes de colapsar
- **Peligro:** Puedes quedar atrapado lejos de casa
- **Detección:** Skill "Exploración" (nivel 4+)

**7. Mercados Negros Flotantes (Black Markets)**
- **Descripción:** Estaciones piratas temporales que aparecen solo en sistemas de baja seguridad (0.0-0.3)
- **Ubicación:** Solo sistemas sec 0.0-0.3
- **Duración:** 72-144 ticks (12-24 horas)
- **Detección:** Skill "Exploración" (nivel 3+) o información de NPCs piratas
- **Acceso:** Requiere standing neutral/positivo (+5) con facción "Piratas del Cinturón" O pagar entrada de 50,000₡

**Servicios ofrecidos:**

1. **Mercado Negro de Items**
   - **Módulos Overclocked:** +50% stats pero -50% durabilidad
   - **Munición Prohibida:** Daño AOE (daña aliados también)
   - **Drogas Sintéticas:** Buffs potentes (+25% todas las skills, 12 ticks) con debuffs posteriores (-15% skills, 24 ticks, -30 moral)
   - **Chips de Diseño Robados:** Blueprints obtenidos ilegalmente (más baratos, traceables)
   - **Transponder Falso:** Cambia identidad por 48 ticks
   - **Precios:** 1.5-3x más caros que mercado normal

2. **Contratos Ilegales**
   - Misiones que reducen standing con facciones lawful:
     - Sabotaje de estaciones (150,000₡, -25 standing Confederación)
     - Asesinato de pilotos específicos (250,000₡)
     - Contrabando de materiales prohibidos (80,000₡)
   - Paga: 2-5x más que misiones normales
   - Consecuencia: Standing negativo permanente con facciones lawful

3. **Modificaciones Ilegales de Naves**
   - **Quitar Transponder:** Stealth permanente, nave ilegal (200,000₡, NO reversible)
   - **Amplificador PG/CPU Ilegal:** +25% PG/CPU, Albatross ataca en sec 0.5+ (350,000₡, reversible 100,000₡)
   - **Reactor Black Hole:** Capacitor infinito, 5% chance explosión/tick en combate (1,000,000₡, reversible 250,000₡)
   - **Sistema Puntería Ilegal:** +40% tracking, +25% optimal range, nave ilegal (450,000₡, NO reversible)
   - Consecuencia: Naves flagged como ilegales, Albatross las ataca en sistemas de alta seguridad

4. **Información del Mercado**
   - Rumores de sitios de exploración (coordenadas de sitios ancestrales no descubiertos)
   - Intel de jugadores (ubicación de pilotos específicos, rutas comerciales)
   - Mapas de sistemas no descubiertos

**Riesgos:**
- **PvP Permitido Dentro:** Otros jugadores pueden atacarte mientras estás en el mercado negro sin consecuencias
- **Raids de Albatross:** 5% chance por hora de que Albatross raidee el mercado (todos los presentes flagged + combate forzado)
- **Items Trackeados:** Algunos items ilegales pueden ser "rastreados" por NPCs lawful (confiscación si detectado en sec 0.5+)
- **Standing Negativo:** Comerciar aquí reduce standing con facciones lawful (-1 por transacción)

**Economía:**
- Precios inflados (1.5-3x mercado normal)
- Standing con "Piratas del Cinturón" otorga descuentos (5-25% según standing)
- Los items ilegales NO pueden venderse en mercados normales (solo P2P o en otros mercados negros)

#### 14.4.2 Aparición de Sitios Temporales

**Frecuencia General:**
- Sistemas sec 1.0: 0-1 sitio cada 72 horas (solo T1, NO Sitios Ancestrales ni Mercados Negros)
- Sistemas sec 0.5-0.9: 1-3 sitios cada 48 horas (T1-T2, incluye Sitios Ancestrales T1-T2)
- Sistemas sec 0.1-0.4: 2-5 sitios cada 24 horas (T1-T3, incluye Sitios Ancestrales T2-T3)
- Sistemas sec 0.0: 3-10 sitios cada 12 horas (T1-T4, incluye Sitios Ancestrales T3-T4 + Mercados Negros)

**Frecuencia Específica - Sitios Ancestrales:**
- Sec 1.0: 0 sitios (NO spawneran)
- Sec 0.5-0.9: 1 sitio cada 96 horas (T1-T2)
- Sec 0.1-0.4: 2-3 sitios cada 48 horas (T1-T3)
- Sec 0.0: 3-6 sitios cada 24 horas (T2-T4)

**Distribución Aleatoria de Tipos (Sitios Ancestrales):**
- 30% Complejo Precursor
- 25% Derelicto Generacional
- 25% Laboratorio de Investigación
- 20% Campo de Escombros Alienígena

**Frecuencia Específica - Mercados Negros Flotantes:**
- Solo aparecen en sistemas sec 0.0-0.3
- Frecuencia: 1 mercado cada 72-144 horas en el sistema
- Duración: 72-144 ticks (12-24 horas)
- Máximo: 1 mercado negro activo por sistema simultáneamente

**Mecánica de Detección:**
1. El piloto usa "Escaneo de Anomalías" (acción de 1 tick)
2. Roll de probabilidad basado en skill "Exploración"
3. Si tiene éxito, aparece un sitio en su scanner con coordenadas
4. El sitio permanece visible solo para él (o puede compartir coordenadas)
5. El sitio desaparece tras completarlo o transcurrir su duración

**Compartir Coordenadas:**
- Los pilotos pueden guardar las coordenadas como "Bookmark"
- Pueden compartir bookmarks con corpmates o venderlos
- Los bookmarks expiran cuando el sitio desaparece

#### 14.4.3 Sistema de Recompensas

**Fórmula General:**

```
valor_recompensa = tier_sitio × dificultad × (1 + nivel_exploración × 0.05) × random(0.8, 1.2)
```

**Ejemplos:**
- Sitio Combate T1: 50,000₡ + loot
- Sitio Combate T4: 5,000,000₡ + blueprints T3
- Sitio Arqueológico T3: Artefacto único + 200,000 exp + posible inyector raro
- Agujero de Gusano a sistema virgen: Registro como "Primer Descubridor" del sistema completo

### 14.5 Escaneo de Anomalías Espaciales

Ubicaciones especiales permanentes o semi-permanentes.

**Tipos:**
- **Wreck Antiguo:** Restos de nave destruida hace tiempo, puede contener tecnología perdida
- **Estructura Abandonada:** Estación dañada o base militar olvidada
- **Fenómeno Espacial:** Pulsar, agujero negro lejano, estrella de neutrones (peligrosos pero con recursos únicos)

**Detección:**
- Habilidad: "Análisis Espacial" o "Exploración"
- Son más raros que sitios temporales pero permanecen indefinidamente
- Una vez descubiertos, quedan marcados en el mapa

---

## Navegación

- [← Anterior: PRD-GameDesign.md](./PRD-GameDesign.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-ShipsAndCombat.md](./PRD-ShipsAndCombat.md)
