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

### 13.1 Escaneo

Desde cualquier ubicación espacial (no estación), los pilotos pueden escanear.

**Tipos de Escaneo:**

**Escaneo de Naves:**
- Detecta otras naves en la ubicación
- Depende de habilidad "Rastreo" vs "Sigilo" del objetivo
- Muestra: Nombre piloto, clase de nave (si se detecta)

**Escaneo de Recursos:**
- En campos de asteroides
- Detecta tipos de minerales
- Habilidad: Prospección

**Escaneo de Anomalías:**
- Detecta anomalías espaciales ocultas
- Puede revelar sitios de combate, wrecks, etc.
- Habilidad: Análisis Espacial

### 13.2 Anomalías Espaciales

Ubicaciones especiales que aparecen proceduralmente.

**Tipos:**
- **Sitio de Combate:** NPCs hostiles, buen loot
- **Campo de Asteroides Rico:** Minerales raros
- **Wreck Antiguo:** Posible tecnología perdida
- **Agujero de Gusano:** Conexión temporal a otro sistema

---

## Navegación

- [← Anterior: PRD-GameDesign.md](./PRD-GameDesign.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-ShipsAndCombat.md](./PRD-ShipsAndCombat.md)
