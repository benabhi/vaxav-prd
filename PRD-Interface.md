# Interfaz de Usuario y Navegación

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 14. Sistema de Menús y Navegación

**NOTA IMPORTANTE:**
Todos los mockups mostrados en esta sección están en formato ASCII/texto **únicamente con fines ilustrativos** para comunicar la estructura de información, jerarquía de datos y funcionalidades de cada menú.

**La interfaz real será una GUI web moderna** con:
- Diseño visual profesional y atractivo
- Componentes interactivos (dropdowns, modals, tooltips)
- Animaciones y transiciones suaves
- Gráficos visuales (charts, progress bars, iconos)
- Responsive design para todos los dispositivos
- Paleta de colores sci-fi (ver Sección 15)

Los mockups sirven como wireframes funcionales que el equipo de diseño UI/UX utilizará para crear la interfaz visual real.

---

### 14.1 Menú Principal

Barra de navegación global siempre visible con acceso a todos los menús principales.

**Estructura del Menú:**

```
┌────────────────────────────────────────────────────────────────────────┐
│ VAXAV    [Licencia] [Registro] [Habilidades] [Nave] [Activos]        │
│          [Mercado] [Billetera] [Corporación] [Mapa] [Mensajería]      │
│                                                    [John Doe] [₡ 125K] │
└────────────────────────────────────────────────────────────────────────┘
```

### 14.2 Menús Principales

### 14.2.1 Licencia de Piloto

**Ruta:** `/pilot/license`

Información básica del personaje estilo "ID Card" o licencia oficial.

**Contenido:**

```
╔═══════════════════════════════════════════════════════════╗
║              LICENCIA DE PILOTO INTERESTELAR             ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║  NOMBRE:           John Doe                               ║
║  ID PILOTO:        #00012847                              ║
║  FECHA NACIMIENTO: 15 de Marzo, 2125                      ║
║  EDAD:             28 años                                ║
║                                                           ║
║  CORPORACIÓN:      Mineros del Vacío S.A.                ║
║  FACCIÓN:          Confederación Vaxav                   ║
║  RANGO:            Piloto Experimentado                   ║
║                                                           ║
║  ESTACIÓN BASE:    Vaxav I - Luna 1 - Puerto Génesis     ║
║  UBICACIÓN ACTUAL: Vaxav III - Órbita                    ║
║  NAVE ACTIVA:      Excavador MK-I "La Fortuna"           ║
║                                                           ║
║  ESTADO:           ⚫ En Línea                            ║
║  DESDE:            2025-11-27                             ║
║                                                           ║
║  REPUTACIÓN:                                              ║
║    Confederación Vaxav:  ████████░░  +45                 ║
║    Liga Libre:           ███░░░░░░░  -15                 ║
║    Sindicato Técnico:    ██████░░░░  +20                 ║
║    Flota Nómada:         █████░░░░░  0                   ║
║                                                           ║
╚═══════════════════════════════════════════════════════════╝

[Ver Perfil Completo] [Editar Bio] [Historial de Kills]
```

**Información Incluida:**
- Nombre y ID único del piloto
- Fecha de nacimiento (fecha creación de personaje)
- Corporación y facción actual
- Rango basado en experiencia/logros
- Estación base (última estación donde se atracó)
- Ubicación actual
- Nave activa
- Estado (online/offline)
- Barras de reputación con todas las facciones principales
- Estadísticas básicas (kills, muertes, misiones completadas)

### 14.2.2 Registro del Capitán

**Ruta:** `/pilot/registry`

Historial completo de actividades y logros del piloto.

**Secciones:**

**1. Historial de Combate:**

```
┌─────────────────────────────────────────────────────────────────┐
│ HISTORIAL DE COMBATE                                            │
├──────────────┬──────────────────────────┬───────────┬───────────┤
│ Fecha        │ Víctima/Atacante         │ Resultado │ Valor     │
├──────────────┼──────────────────────────┼───────────┼───────────┤
│ 2025-11-25   │ Pirata "Scar" (NPC)      │ Victoria  │ 5,000 ₡   │
│ 2025-11-23   │ Jane Smith               │ Derrota   │ -25,000 ₡ │
│ 2025-11-20   │ Bandido del Vacío (NPC)  │ Victoria  │ 2,500 ₡   │
└──────────────┴──────────────────────────┴───────────┴───────────┘
Victorias: 45 | Derrotas: 12 | Ratio: 3.75
```

**2. Historial de Viajes:**

```
┌─────────────────────────────────────────────────────────────────┐
│ ÚLTIMOS VIAJES                                                  │
├──────────────┬──────────────────────────┬──────────────────────┤
│ Fecha        │ Origen → Destino         │ Duración             │
├──────────────┼──────────────────────────┼──────────────────────┤
│ 2025-11-27   │ Vaxav I → Vaxav III      │ 45 ticks (22 min)    │
│ 2025-11-26   │ Vaxav III → Vaxav I      │ 45 ticks (22 min)    │
└──────────────┴──────────────────────────┴──────────────────────┘
Saltos totales: 1,247 | Distancia total: 2,847,392 AU
```

**3. Historial de Misiones:**

```
┌─────────────────────────────────────────────────────────────────┐
│ MISIONES RECIENTES                                              │
├──────────────┬─────────────────┬────────┬─────────┬────────────┤
│ Fecha        │ Misión          │ Tipo   │ Estado  │ Recompensa │
├──────────────┼─────────────────┼────────┼─────────┼────────────┤
│ 2025-11-26   │ Minar Tritanio  │ Minería│ ✓       │ 15,000 ₡   │
│ 2025-11-24   │ Escoltar Convoy │ Combate│ ✓       │ 35,000 ₡   │
│ 2025-11-22   │ Recuperar Datos │ Explor.│ ✗ Falló │ 0 ₡        │
└──────────────┴─────────────────┴────────┴─────────┴────────────┘
Completadas: 87 | Fallidas: 5 | Ratio éxito: 94.6%
```

**4. Logros y Hitos:**

```
╔═══════════════════════════════════════════════════════════╗
║ LOGROS DESBLOQUEADOS                              23/150  ║
╠═══════════════════════════════════════════════════════════╣
║ ⭐ Primer Salto                    Desbloqueado 2025-11-01║
║ ⭐ Minero Novato (1K minerales)    Desbloqueado 2025-11-05║
║ ⭐ Millonario (1M créditos)        Desbloqueado 2025-11-15║
║ ⭐ Asesino Despiadado (10 kills)   Desbloqueado 2025-11-20║
║ 🔒 Magnate (100M créditos)         Bloqueado              ║
║ 🔒 Explorador (Visitar 10 sistemas) Bloqueado            ║
╚═══════════════════════════════════════════════════════════╝
```

**5. Línea de Tiempo:**

```
═══════════════════════════ LÍNEA DE VIDA ═══════════════════════════
│
├─ 2025-11-01  🎂 Nacimiento en Puerto Estelar Génesis
├─ 2025-11-01  🎓 Carrera iniciada: Minero
├─ 2025-11-02  ⚔️  Primera muerte
├─ 2025-11-05  🏭 Primera fabricación exitosa
├─ 2025-11-10  🏢 Unión a corporación "Mineros del Vacío"
├─ 2025-11-15  💰 Alcanzado 1M créditos
├─ 2025-11-20  🚀 Primera nave Crucero adquirida
└─ 2025-11-27  📍 Ubicación actual
```

### 14.2.3 Habilidades

**Ruta:** `/pilot/skills`

Sistema completo de gestión de habilidades (ver [PRD-GameDesign.md](./PRD-GameDesign.md) para detalles completos).

**Vistas:**
- **Árbol de Habilidades:** Vista jerárquica con dependencias
- **Habilidades Inyectadas:** Solo las que el piloto posee
- **Habilidades Descubiertas:** No inyectadas pero visibles
- **Buscar en Mercado:** Integración directa con mercado

### 14.2.4 Nave

**Ruta:** `/ship/current` o `/ship/{ship_id}`

Menú dedicado a la nave activa con submenús.

**Submenús:**

**1. Vista General:**

```
╔═══════════════════════════════════════════════════════════╗
║  EXCAVADOR MK-I "La Fortuna"                              ║
║  Fragata Minera                                           ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║  ⚡ ESTADO DE SISTEMAS                                    ║
║    Escudos:     ████████░░  450/500  (90%)               ║
║    Armadura:    ██████████  800/800  (100%)              ║
║    Estructura:  ██████████  600/600  (100%)              ║
║    Energía:     ███████░░░  700/1000 (70%)               ║
║                                                           ║
║  📦 CARGA                                                 ║
║    Usado:       3,250/5,000 m³  (65%)                    ║
║                                                           ║
║  ⚙️  MÓDULOS ACTIVOS                                      ║
║    ● Láser de Minería Básico     [ACTIVO]                ║
║    ● Expansor de Carga I         [PASIVO]                ║
║    ○ Escudo Básico              [OFFLINE]                ║
║                                                           ║
║  📍 UBICACIÓN                                             ║
║    Vaxav III - Campo de Asteroides Alpha                 ║
║                                                           ║
╚═══════════════════════════════════════════════════════════╝

[Gestionar Módulos] [Ver Carga] [Reparar] [Cambiar Nave]
```

**2. Fitting (Módulos):**

```
┌───────────────────────────────────────────────────────────┐
│ CONFIGURACIÓN DE MÓDULOS                                  │
├───────────────────────────────────────────────────────────┤
│                                                           │
│ SISTEMAS OFENSIVOS (1/1 usado)                           │
│  [█] Slot 1: Láser de Minería Básico                     │
│                                                           │
│ SISTEMAS DEFENSIVOS (1/2 usado)                          │
│  [█] Slot 1: Escudo Básico                               │
│  [ ] Slot 2: Vacío                                       │
│                                                           │
│ SISTEMAS DE UTILIDAD (1/3 usado)                         │
│  [█] Slot 1: Expansor de Carga I                         │
│  [ ] Slot 2: Vacío                                       │
│  [ ] Slot 3: Vacío                                       │
│                                                           │
└───────────────────────────────────────────────────────────┘

[Equipar Módulo] [Desequipar] [Guardar Fitting] [Cargar Fitting]
```

**3. Carga/Inventario:**

```
┌───────────────────────────────────────────────────────────┐
│ BODEGA DE CARGA - 3,250/5,000 m³                         │
├─────────────────────┬──────────┬───────────┬─────────────┤
│ Item                │ Cantidad │ Volumen   │ Total m³    │
├─────────────────────┼──────────┼───────────┼─────────────┤
│ Tritanio Crudo      │ 1,500    │ 1 m³      │ 1,500 m³    │
│ Pirita Cruda        │ 800      │ 1.5 m³    │ 1,200 m³    │
│ Munición Estándar   │ 500      │ 0.1 m³    │ 50 m³       │
│ Escudo Mejorado I   │ 1        │ 500 m³    │ 500 m³      │
└─────────────────────┴──────────┴───────────┴─────────────┘

[Transferir a Estación] [Desechar] [Ver Todo]
```

### 14.2.5 Activos

**Ruta:** `/pilot/assets`

Vista global de todos los items, naves y recursos del piloto dispersos por el universo.

```
╔═══════════════════════════════════════════════════════════╗
║ ACTIVOS TOTALES                         Valor: 2.5M ₡     ║
╠═══════════════════════════════════════════════════════════╣

📍 VAXAV I - LUNA 1 - PUERTO ESTELAR GÉNESIS
├─ 🚀 Naves (2)
│  ├─ Excavador MK-I "La Fortuna"        [EN USO]
│  └─ Fragata de Combate "Venganza"      250,000 ₡
├─ 📦 Items en Hangar (45 items)         125,000 ₡
│  ├─ Tritanio Puro (5,000 unidades)
│  ├─ Láser de Minería Avanzado (x2)
│  └─ ... [Ver más]
└─ 📦 Items en Bodega Estación (120)     450,000 ₡

📍 VAXAV III - LUNA 2 - ESTACIÓN MARTE
├─ 🚀 Naves (1)
│  └─ Carguero Ligero "Mercante"         300,000 ₡
└─ 📦 Items en Hangar (12 items)          75,000 ₡

📍 EN ÓRDENES DE MERCADO
├─ 💹 Órdenes de Venta (5)
│  ├─ Inyector de Minería x3            @ 20,000 ₡
│  ├─ Pirita Refinada x5000             @ 15,000 ₡
│  └─ ... [Ver más]
└─ Valor total bloqueado:                 250,000 ₡

═══════════════════════════════════════════════════════════
RESUMEN:
  Naves:              3           (800,000 ₡)
  Items:              177         (1,200,000 ₡)
  En mercado:         5 órdenes   (250,000 ₡)
  Créditos líquidos:  ──          (250,000 ₡)
  ─────────────────────────────────────────────
  TOTAL:                          2,500,000 ₡
```

**Filtros disponibles:**
- Por ubicación
- Por tipo (naves, módulos, minerales, etc.)
- Por valor
- Items en venta vs. almacenados

**Acciones:**
- Ver detalle de item/nave
- Contratar transporte de items
- Vender rápido
- Empaquetar todo en estación

### 14.2.6 Mercado

**Ruta:** `/market`

Sistema completo de comercio (ver [PRD-Economy.md](./PRD-Economy.md) para mecánicas completas).

**Secciones:**

**1. Explorar Mercado:**

```
┌───────────────────────────────────────────────────────────┐
│ MERCADO - Puerto Estelar Génesis                         │
├───────────────────────────────────────────────────────────┤
│                                                           │
│ [🔍 Buscar...]                    [Filtros ▼] [Vista: 📋]│
│                                                           │
│ Categorías:                                               │
│   ⛏️  Minerales y Recursos                                │
│   🔧 Módulos de Nave                                      │
│   🚀 Naves                                                │
│   💉 Inyectores de Habilidad                              │
│   📘 Blueprints                                           │
│   🔋 Municiones y Cargas                                  │
│   📦 Otros                                                │
│                                                           │
└───────────────────────────────────────────────────────────┘
```

**2. Vista de Item:**

```
╔═══════════════════════════════════════════════════════════╗
║ TRITANIO REFINADO                                         ║
╠═══════════════════════════════════════════════════════════╣
║ Mineral refinado básico usado en construcción de naves   ║
║ y módulos. El material más común en el universo.         ║
║                                                           ║
║ Volumen: 1 m³ | Precio Base: 100 ₡                       ║
╚═══════════════════════════════════════════════════════════╝

ÓRDENES DE VENTA (Comprar)
┌──────────┬──────────┬───────────────────────────┬──────────┐
│ Precio   │ Cantidad │ Ubicación                 │ Rango    │
├──────────┼──────────┼───────────────────────────┼──────────┤
│ 95 ₡     │ 50,000   │ Puerto Estelar Génesis    │ Estación │
│ 98 ₡     │ 120,000  │ Puerto Estelar Génesis    │ Estación │
│ 102 ₡    │ 80,000   │ Estación Marte            │ 5 saltos │
└──────────┴──────────┴───────────────────────────┴──────────┘

ÓRDENES DE COMPRA (Vender)
┌──────────┬──────────┬───────────────────────────┬──────────┐
│ Precio   │ Cantidad │ Ubicación                 │ Rango    │
├──────────┼──────────┼───────────────────────────┼──────────┤
│ 92 ₡     │ 30,000   │ Puerto Estelar Génesis    │ Estación │
│ 90 ₡     │ 75,000   │ Puerto Estelar Génesis    │ Regional │
│ 88 ₡     │ 100,000  │ Cualquiera                │ Regional │
└──────────┴──────────┴───────────────────────────┴──────────┘

[📈 Ver Gráfico] [Comprar Ahora] [Vender Ahora] [Crear Orden]
```

**3. Historial de Precios:**

```
HISTORIAL - TRITANIO REFINADO (Últimos 30 días)

Precio ₡
  110│                                    ╱╲
     │                                  ╱    ╲
  100│                        ╱╲      ╱      ╲
     │              ╱╲      ╱    ╲  ╱          ╲
   90│    ╱╲      ╱  ╲    ╱      ╲╱            ╲╱╲
     │  ╱    ╲  ╱      ╲╱
   80│╱        ╲╱
     └────────────────────────────────────────────────> Días
      30      25      20      15      10       5       0

Promedio 30d: 95 ₡
Máximo:      112 ₡  (hace 18 días)
Mínimo:       82 ₡  (hace 28 días)
Volumen 24h:  2.5M unidades
```

**4. Mis Órdenes:**

```
┌───────────────────────────────────────────────────────────┐
│ MIS ÓRDENES ACTIVAS                                  (8)  │
├──────┬─────────────┬────────┬──────────┬─────────┬────────┤
│ Tipo │ Item        │ Precio │ Cantidad │ Restante│ Expira │
├──────┼─────────────┼────────┼──────────┼─────────┼────────┤
│ SELL │ Tritanio    │ 98 ₡   │ 10,000   │ 7,500   │ 15d    │
│ BUY  │ Iny. Minería│ 18K ₡  │ 1        │ 1       │ 22d    │
│ SELL │ Pirita      │ 150 ₡  │ 5,000    │ 5,000   │ 8d     │
└──────┴─────────────┴────────┴──────────┴─────────┴────────┘

[Cancelar Orden] [Modificar] [Ver Historial]
```

### 14.2.7 Billetera

**Ruta:** `/wallet`

Gestión financiera completa del piloto.

```
╔═══════════════════════════════════════════════════════════╗
║ BILLETERA                                                 ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║  💰 BALANCE PERSONAL                                      ║
║     Créditos:  250,450 ₡                                  ║
║                                                           ║
║  🏢 BALANCE CORPORATIVO (Mineros del Vacío S.A.)         ║
║     Créditos:  1,250,000 ₡                                ║
║     Tu acceso: Solo lectura                               ║
║                                                           ║
╚═══════════════════════════════════════════════════════════╝

TRANSACCIONES RECIENTES
┌──────────────┬──────────────────────┬───────────┬──────────┐
│ Fecha        │ Descripción          │ Monto     │ Balance  │
├──────────────┼──────────────────────┼───────────┼──────────┤
│ 2025-11-27   │ Venta: Tritanio x500 │ +47,500 ₡ │ 250,450₡ │
│ 2025-11-27   │ Compra: Iny. Escudos │ -30,000 ₡ │ 202,950₡ │
│ 2025-11-26   │ Misión completada    │ +15,000 ₡ │ 232,950₡ │
│ 2025-11-26   │ Reparación de nave   │ -5,250 ₡  │ 217,950₡ │
│ 2025-11-25   │ Impuesto corporativo │ -2,500 ₡  │ 223,200₡ │
└──────────────┴──────────────────────┴───────────┴──────────┘

[Ver Histórico Completo] [Transferir] [Estadísticas]

ESTADÍSTICAS DEL MES
  Ingresos totales:     +450,000 ₡
  Gastos totales:       -285,000 ₡
  Balance neto:         +165,000 ₡

  Fuente principal:     Comercio (45%)
  Gasto principal:      Mejoras de nave (32%)
```

**Filtros:**
- Por tipo (compras, ventas, misiones, etc.)
- Por rango de fechas
- Por monto mínimo/máximo

### 14.2.8 Corporación

**Ruta:** `/corporation/{corp_id}`

Panel de gestión de corporación (ver [PRD-GameDesign.md](./PRD-GameDesign.md) para mecánicas completas).

**Vista para Miembros:**

```
╔═══════════════════════════════════════════════════════════╗
║ MINEROS DEL VACÍO S.A.                                    ║
║ Facción: Confederación Vaxav                              ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║  CEO: Marcus Steel                                        ║
║  Miembros: 45                                             ║
║  Fundada: 2025-10-15                                      ║
║  Cuartel General: Puerto Estelar Génesis                  ║
║                                                           ║
║  Impuesto: 5%                                             ║
║  Balance: 1,250,000 ₡                                     ║
║                                                           ║
╚═══════════════════════════════════════════════════════════╝

MIEMBROS ONLINE (12/45)
┌────────────────────┬──────────────┬─────────────────────┐
│ Piloto             │ Rango        │ Ubicación           │
├────────────────────┼──────────────┼─────────────────────┤
│ ⚫ Marcus Steel    │ CEO          │ Vaxav I             │
│ ⚫ John Doe        │ Minero       │ Vaxav III           │
│ ⚫ Jane Smith      │ Director     │ Vaxav II            │
│ ⚫ Bob Johnson     │ Minero       │ Vaxav I             │
└────────────────────┴──────────────┴─────────────────────┘

[Chat Corporativo] [Solicitar Fondos] [Ver Hangares] [Diplomacia]
```

**Vista para CEO/Directores:**
- Gestión de miembros
- Configuración de impuestos
- Roles y permisos
- Declaraciones de guerra
- Gestión de estaciones corporativas
- Finanzas detalladas

### 14.2.9 Mapa

**Ruta:** `/map`

Representación textual del universo (ver [PRD-Universe.md](./PRD-Universe.md) para detalles del sistema).

**Vista de Sistema Solar:**

```
════════════════════ SISTEMA VAXAV ════════════════════

                         ☀️ VAXAV (Estrella)
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
        🌑 I              🌍 II              🔴 III
      (2 lunas)         (1 luna)          (3 lunas)
          │                   │                   │
    ┌─────┴─────┐            │            ┌──────┼──────┐
    │           │            │            │      │      │
  Luna 1     Luna 2       Luna 1       Luna 1  Luna 2  Luna 3
   [3]        [1]          [2]          [2]    [1]     [0]

[Número] = Estaciones en la luna

📍 TU UBICACIÓN: Vaxav III - Órbita

════════════════════════════════════════════════════════

🚪 STARGATES DISPONIBLES (1/4 desbloqueados)
  → Stargate Alpha (destino: Sistema Kepler-442)

⚠️ Progreso de Sistema: ████████░░ 12,450/25,000
   Próximo desbloqueo: Stargate Beta (12,550 puntos más)

[Ver Planetas] [Ver Estaciones] [Saltar a Sistema] [Anomalías]
```

**Vista de Planeta:**

```
🌍 VAXAV II
Tipo: Planeta Rocoso
Gravedad: 1.2 G
Atmósfera: Tóxica

LUNA 1
├─ 📡 Estación "Observatorio Kepler"      [NPC - Sindicato Técnico]
└─ 📡 Estación "Puesto Científico 7"      [NPC - Sindicato Técnico]

RECURSOS CONOCIDOS:
  ⛏️  Isógeno (abundante)
  ⛏️  Megacita (raro)

ANOMALÍAS CERCANAS:
  ❓ Señal desconocida (escaneo requerido)

[Viajar] [Escanear] [Ver Estaciones]
```

**Vista Galáctica:**

```
═══════════════ GALAXIA CONOCIDA ═══════════════

    [Vaxav] ═══════════> [Kepler-442]
       │
       ╚═══════════> [???] (Stargate Beta - Bloqueado)

Sistemas explorados: 2/∞
Distancia total mapeada: 42 años luz

[Expandir Sistema] [Ver Rutas] [Stargates]
```

### 14.2.10 Mensajería

**Ruta:** `/messages`

Sistema de mensajes tipo email entre jugadores.

```
╔═══════════════════════════════════════════════════════════╗
║ MENSAJES                                     Nuevos: 3    ║
╠═══════════════════════════════════════════════════════════╣

[Nuevo Mensaje] [Actualizar]

BANDEJA DE ENTRADA
┌────────────────────────────────────────────────────────┐
│ ● Marcus Steel          [Corp] Reunión mañana          │
│   Hace 2 horas                                         │
│                                                        │
│ ● Jane Smith            RE: Venta de Tritanio          │
│   Hace 5 horas                                         │
│                                                        │
│ ● Sistema Vaxav         [Auto] Misión disponible       │
│   Hace 1 día                                           │
│                                                        │
│   Bob Johnson           Propuesta de comercio          │
│   Hace 2 días                                          │
│                                                        │
│   Agente NPC            Misión completada              │
│   Hace 3 días                                          │
└────────────────────────────────────────────────────────┘

[Enviados] [Archivados] [Papelera]
```

**Vista de Mensaje:**

```
╔═══════════════════════════════════════════════════════════╗
║ De: Marcus Steel (CEO - Mineros del Vacío S.A.)          ║
║ Para: Todos los miembros                                  ║
║ Asunto: [Corp] Reunión mañana                             ║
║ Fecha: 2025-11-27 14:30                                   ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║ Equipo,                                                   ║
║                                                           ║
║ Mañana a las 20:00 hora del servidor tendremos una       ║
║ reunión corporativa para discutir la expansión al        ║
║ sistema Kepler-442. Todos están invitados.               ║
║                                                           ║
║ La reunión será en el chat corporativo.                  ║
║                                                           ║
║ Saludos,                                                  ║
║ Marcus                                                    ║
║                                                           ║
╚═══════════════════════════════════════════════════════════╝

[Responder] [Responder a Todos] [Archivar] [Eliminar]
```

**Tipos de mensajes:**
- Mensajes de jugadores
- Notificaciones del sistema
- Alertas de corporación
- Confirmaciones de transacciones
- Notificaciones de combate
- Alertas de mercado (opcional)

### 14.3 Menús Adicionales y Secundarios

### 14.3.1 Contratos

**Ruta:** `/contracts`

Sistema de contratos entre jugadores (transporte, fabricación, misiones privadas).

```
╔═══════════════════════════════════════════════════════════╗
║ CONTRATOS                                                 ║
╠═══════════════════════════════════════════════════════════╣

CONTRATOS DISPONIBLES (Públicos)
┌──────────────────────────────────────────────────────────┐
│ Tipo: Transporte                                         │
│ De: Marcus Steel → Destino: Estación Marte (5 saltos)   │
│ Carga: 5,000 m³ de Tritanio Refinado                    │
│ Pago: 25,000 ₡ | Colateral: 50,000 ₡                    │
│ Expira en: 3 días                                        │
│ [Aceptar Contrato]                                       │
└──────────────────────────────────────────────────────────┘

MIS CONTRATOS ACTIVOS (2)
┌──────────────────────────────────────────────────────────┐
│ Tipo: Fabricación                                        │
│ Cliente: Jane Smith                                      │
│ Item: 10x Láser de Minería Básico                       │
│ Progreso: 7/10 completado                               │
│ Plazo: 2 días restantes                                 │
└──────────────────────────────────────────────────────────┘

[Crear Contrato] [Mis Contratos] [Historial]
```

**Tipos de Contratos:**
- **Transporte:** Mover items de A a B
- **Fabricación:** Crear items específicos
- **Courier:** Entrega de paquetes (el contenido está sellado)
- **Compra/Venta:** Intercambio de items por precio fijo
- **Préstamo:** Préstamo de créditos con intereses

### 14.3.2 Industria

**Ruta:** `/industry`

Panel centralizado para gestionar todas las actividades de producción.

```
╔═══════════════════════════════════════════════════════════╗
║ INDUSTRIA                                                 ║
╠═══════════════════════════════════════════════════════════╣

TRABAJOS EN CURSO (3)
┌───────────────┬──────────────────┬──────────┬────────────┐
│ Tipo          │ Item             │ Progreso │ Termina en │
├───────────────┼──────────────────┼──────────┼────────────┤
│ Fabricación   │ Escudo Básico x5 │ ███░░░░  │ 45 ticks   │
│ Refinamiento  │ Tritanio Puro    │ ████░░░  │ 12 ticks   │
│ Investigación │ BPO Láser T2     │ ██░░░░░  │ 250 ticks  │
└───────────────┴──────────────────┴──────────┴────────────┘

MIS BLUEPRINTS (25)
  🔷 Fragata Minera MK-I (BPO) - Material Eff: 5%, Time Eff: 0%
  🔶 Láser de Minería Básico (BPC) - 10 runs restantes
  🔶 Escudo Básico (BPC) - 5 runs restantes

[Nueva Producción] [Blueprints] [Investigación] [Instalaciones]
```

### 14.3.3 Flotas

**Ruta:** `/fleets`

Sistema para organizar flotas de jugadores (PvE/PvP cooperativo).

```
╔═══════════════════════════════════════════════════════════╗
║ FLOTAS                                                    ║
╠═══════════════════════════════════════════════════════════╣

INVITACIONES (1)
  ● Marcus Steel te invita a "Operación Minería Vaxav III"
    Miembros: 5/10 | Objetivo: Minería masiva
    [Aceptar] [Rechazar]

MI FLOTA ACTUAL
  Nombre: Operación Minería Vaxav III
  Líder: Marcus Steel ⭐
  Miembros: 6/10

  ┌────────────────┬──────────────────┬────────────┐
  │ Piloto         │ Nave             │ Estado     │
  ├────────────────┼──────────────────┼────────────┤
  │ Marcus Steel ⭐│ Excavador MK-I   │ ⚫ Minando  │
  │ John Doe       │ Excavador MK-I   │ ⚫ Minando  │
  │ Jane Smith     │ Carguero Ligero  │ ⚫ Orbitando│
  │ Bob Johnson    │ Fragata Combate  │ ⚫ Escolta  │
  └────────────────┴──────────────────┴────────────┘

  Recursos totales minados: 15,250 unidades

  [Chat de Flota] [Salir de Flota] [Opciones]

[Crear Flota] [Flotas Públicas]
```

### 14.3.4 Notificaciones

**Ruta:** `/notifications`

Centro de notificaciones del juego.

```
╔═══════════════════════════════════════════════════════════╗
║ NOTIFICACIONES                            No leídas: 5    ║
╠═══════════════════════════════════════════════════════════╣

HOY
● [Mercado] Tu orden de venta de Tritanio se completó
  +47,500 ₡ recibidos                        Hace 15 min

● [Combate] Tu nave fue atacada en Vaxav III
  Resultado: Victoria - Loot disponible     Hace 2 horas

  [Sistema] Misión "Minar Tritanio" expiró
  Sin penalización                           Hace 3 horas

AYER
● [Corporación] Marcus Steel depositó 100K ₡ en el tesoro
                                              Hace 1 día

  [Habilidades] Minería alcanzó nivel 3
  Nuevas capacidades desbloqueadas          Hace 1 día

[Marcar todo como leído] [Configurar Alertas]
```

**Configuración de Notificaciones:**
- Email para eventos importantes
- Notificaciones en juego
- Alertas de mercado (precio objetivo)
- Alertas de combate
- Notificaciones de corporación

### 14.3.5 Configuración

**Ruta:** `/settings`

Panel de configuración del juego.

```
╔═══════════════════════════════════════════════════════════╗
║ CONFIGURACIÓN                                             ║
╠═══════════════════════════════════════════════════════════╣

CUENTA
  Email: johndoe@example.com          [Cambiar]
  Contraseña: ••••••••                [Cambiar]
  Autenticación 2FA: ✗ Deshabilitada  [Habilitar]

INTERFAZ
  Tema: [x] Oscuro  [ ] Claro  [ ] Auto
  Idioma: Español ▼
  Zona horaria: UTC-3 ▼
  Formato de números: 1,234.56 ▼

NOTIFICACIONES
  [x] Alertas de combate
  [x] Alertas de mercado
  [x] Mensajes de corporación
  [ ] Mensajes de jugadores (solo amigos)
  [ ] Email para eventos críticos

PRIVACIDAD
  Perfil visible: [x] Público  [ ] Solo corporación  [ ] Privado
  Ubicación visible: [x] Todos  [ ] Corporación  [ ] Nadie
  Inventario visible: [ ] Todos  [x] Corporación  [ ] Nadie

JUEGO
  Confirmar acciones peligrosas: [x] Activado
  Auto-rechazar duelos PvP: [ ] Activado
  Vista de nave por defecto: General ▼

[Guardar Cambios] [Restaurar Defaults]
```

### 14.3.6 Amigos y Contactos

**Ruta:** `/contacts`

Gestión de amigos, contactos y bloqueos.

```
╔═══════════════════════════════════════════════════════════╗
║ CONTACTOS                                                 ║
╠═══════════════════════════════════════════════════════════╣

AMIGOS ONLINE (8/24)
┌────────────────────┬────────────────────────┬────────────┐
│ Piloto             │ Ubicación              │ Estado     │
├────────────────────┼────────────────────────┼────────────┤
│ ⚫ Marcus Steel    │ Vaxav I                │ Minando    │
│ ⚫ Jane Smith      │ Vaxav III              │ Combate    │
│ ⚫ Bob Johnson     │ Kepler-442             │ Explorando │
└────────────────────┴────────────────────────┴────────────┘

[Agregar Amigo] [Solicitudes Pendientes (2)]

LISTAS
  📋 Amigos (24)
  📋 Corporación (45)
  ⭐ Favoritos (5)
  ⚠️  Vigilar (3)
  🚫 Bloqueados (1)

[Mensaje] [Invitar a Flota] [Ver Licencia]
```

### 14.3.7 Leaderboards / Rankings

**Ruta:** `/rankings`

Clasificaciones y estadísticas del servidor.

```
╔═══════════════════════════════════════════════════════════╗
║ CLASIFICACIONES - SERVIDOR VAXAV                          ║
╠═══════════════════════════════════════════════════════════╣

MÁS RICOS (Por Créditos)
┌─────┬────────────────────┬──────────────┬───────────────┐
│ #   │ Piloto             │ Corporación  │ Fortuna       │
├─────┼────────────────────┼──────────────┼───────────────┤
│ 1   │ 👑 Richard Branson │ Mercaderes   │ 1,250,000,000₡│
│ 2   │ Sarah Connor       │ Liga Libre   │ 845,000,000 ₡ │
│ 3   │ Marcus Steel       │ Min. Vacío   │ 523,000,000 ₡ │
│...  │ ...                │ ...          │ ...           │
│ 847 │ ► John Doe (TÚ)    │ Min. Vacío   │ 250,450 ₡     │
└─────┴────────────────────┴──────────────┴───────────────┘

OTRAS CLASIFICACIONES:
  🏆 PvP Kills
  ⛏️  Recursos Minados
  🏭 Items Fabricados
  🚀 Naves Destruidas
  📊 Volumen de Comercio
  🎯 Misiones Completadas
  🌌 Sistemas Explorados

[Ver Mi Posición] [Filtrar por Corporación]
```

### 14.3.8 Panel de Administración

**Ruta:** `/admin` (Solo accesible para administradores)

Panel de administración del juego para configurar parámetros globales.

```
╔═══════════════════════════════════════════════════════════╗
║ PANEL DE ADMINISTRACIÓN                                   ║
╠═══════════════════════════════════════════════════════════╣

CONFIGURACIÓN DEL SISTEMA DE TICKS
┌───────────────────────────────────────────────────────────┐
│ Duración del Tick (minutos)                              │
│ ┌──────┐                                                  │
│ │  10  │ minutos  [Actualizar]                           │
│ └──────┘                                                  │
│                                                            │
│ Estado del Sistema: ✓ Activo                             │
│ Último tick ejecutado: Hace 3 minutos                     │
│ Próximo tick en: 7 minutos                               │
│                                                            │
│ ⚠️ ADVERTENCIA: Cambiar la duración del tick afectará    │
│    todos los cálculos del juego. Los jugadores verán     │
│    tiempos actualizados automáticamente.                 │
│                                                            │
│ [Ejecutar Tick Manualmente] [Ver Historial de Ticks]     │
└───────────────────────────────────────────────────────────┘

CONFIGURACIÓN SOCIAL
┌───────────────────────────────────────────────────────────┐
│ Recuperación de energía offline (cada X ticks)           │
│ ┌──────┐ ticks = 1 punto de energía                      │
│ │  2   │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Degradación de nutrición (cada X ticks)                  │
│ ┌──────┐ ticks = -1 nutrición                            │
│ │  6   │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Cambio de estrés (cada X ticks)                          │
│ ┌──────┐ ticks para aplicar cambios de estrés            │
│ │  6   │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Ticks por día (para cálculos de moral/relaciones)        │
│ ┌──────┐ ticks = 1 día de juego                          │
│ │ 144  │                                                  │
│ └──────┘                                                  │
│                                                            │
│ [Guardar Cambios] [Restaurar Defaults]                   │
└───────────────────────────────────────────────────────────┘

COOLDOWNS DEL JUEGO
┌───────────────────────────────────────────────────────────┐
│ Cooldown al quedar inconsciente                          │
│ ┌──────┐ ticks (~1 hora por defecto)                     │
│ │  6   │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Cooldown actualización de clon                           │
│ ┌──────┐ ticks (~24 horas por defecto)                   │
│ │ 144  │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Cooldown declaración de guerra                           │
│ ┌──────┐ ticks (~24 horas por defecto)                   │
│ │ 144  │                                                  │
│ └──────┘                                                  │
│                                                            │
│ Duración mínima de guerra                                │
│ ┌──────┐ ticks (~7 días por defecto)                     │
│ │ 1008 │                                                  │
│ └──────┘                                                  │
│                                                            │
│ [Guardar Cambios] [Restaurar Defaults]                   │
└───────────────────────────────────────────────────────────┘

OTRAS SECCIONES DE ADMINISTRACIÓN:
  👥 Gestión de Usuarios
  🏢 Gestión de Corporaciones
  🌌 Gestión del Universo (Sistemas, Estaciones)
  💰 Economía Global (Precios base, Inflación)
  📊 Estadísticas del Servidor
  📝 Logs de Actividad
  🛠️ Mantenimiento (Backup, Reset de ticks)

[Aplicar Todos los Cambios] [Exportar Configuración]
```

**Características del Panel de Admin:**
- Todas las configuraciones se guardan en la tabla `game_config`
- Los cambios se aplican inmediatamente y se propagan con cache invalidation
- Historial de cambios de configuración con usuario y timestamp
- Validaciones para evitar valores inválidos (ej: tick duration < 1 minuto)
- Botón de "Restaurar Defaults" para valores por defecto del sistema
- Cálculos automáticos de equivalencias en tiempo real (ej: "144 ticks = 24h con tick de 10 min")

### 14.4 Menú Contextual de Ubicación

Dependiendo de dónde está el jugador, se muestran acciones específicas.

**En Estación:**

```
Módulos disponibles:
  [Hangar] [Laboratorio] [Mercado] [Habitáculos]
  [Astillero] [Sala Ingeniería] [Bodegas] [Agentes]

Acciones:
  [Despegar] [Ver Nave] [Reparar] [Recargar]
```

**En Espacio (Órbita):**

```
Ubicación actual: Vaxav III - Órbita (Estación Marte)

Acciones:
  [Atracar en Estación] [Viajar a...] [Escanear]
  [Ver Naves Cercanas] [Activar Módulos]
```

**En Campo de Asteroides:**

```
Ubicación actual: Vaxav III - Campo de Asteroides Alpha

Recursos detectados:
  ⛏️ Tritanio (abundante)
  ⛏️ Pirita (común)

Acciones:
  [Minar] [Escanear Asteroides] [Ver Naves] [Viajar]
```

---

## 15. Interfaz de Usuario (GUI)

### 15.1 Visión General de la Interfaz

**ACLARACIÓN IMPORTANTE:**
Vaxav NO es un juego ASCII ni de terminal. Es un **juego web moderno con una interfaz gráfica hermosa y profesional**. Todos los mockups en formato ASCII/texto mostrados en este documento son **puramente ilustrativos** para comunicar la estructura de información y funcionalidades.

**La interfaz real será:**
- 🎨 **Moderna y elegante** con diseño sci-fi/futurista
- 📊 **Rica en información** pero organizada visualmente
- 🖥️ **Completamente responsive** (desktop, tablet, móvil)
- ⚡ **Interactiva y dinámica** con transiciones suaves
- 🎯 **Optimizada para mostrar datos** de forma clara y atractiva
- 🌌 **Identidad visual única** inspirada en EVE Online pero con estilo propio

**Referentes visuales:**
- EVE Online (UI limpia, datos organizados)
- Popmundo (presentación de información textual elegante)
- OGame (diseño espacial, menús claros)
- Interfaces sci-fi modernas (Cyberpunk, Halo, Mass Effect)

### 15.2 Principios de Diseño

### Diseño Visual:

- **Paleta de colores:** Tonos oscuros (negro, gris oscuro, azul oscuro) con acentos brillantes (cyan, naranja, verde neón)
- **Tipografía:** Fuentes modernas y legibles (sans-serif), posiblemente monoespaciadas para números/stats
- **Espaciado:** Generoso uso de whitespace para evitar saturación
- **Íconos:** Sistema de iconografía consistente para acciones, recursos, estados
- **Animaciones:** Sutiles y funcionales (no distractoras)
- **Feedback visual:** Estados de hover, loading, success, error claramente diferenciados

### Organización de Información:

- **Jerarquía visual clara:** Títulos, subtítulos, datos, acciones bien diferenciados
- **Cards/Paneles:** Información agrupada en contenedores visuales
- **Tablas modernas:** Headers sticky, zebra striping, sorting visual
- **Gráficos:** Uso de charts.js o similar para datos complejos (precios de mercado, estadísticas)
- **Progress bars:** Visuales y animadas (energía, nutrición, skills, etc.)
- **Badges/Tags:** Para estados, categorías, niveles

### Navegación:

- **Menú principal:** Sticky header con acceso a todas las secciones
- **Breadcrumbs:** Siempre visibles con navegación rápida
- **Sidebar colapsable:** Para acciones contextuales según ubicación
- **Notificaciones:** Badge counter, toast messages para eventos
- **Quick actions:** Botones flotantes para acciones frecuentes

### Técnico:

- **Server-side rendering:** Laravel Blade para SEO y performance
- **Tailwind CSS:** Framework utility-first para diseño consistente
- **Alpine.js:** JavaScript reactivo mínimo para interactividad
- **Componentes reutilizables:** Sistema de componentes Blade bien estructurado
- **Progressive enhancement:** Funcional sin JS, mejorado con JS
- **Optimización móvil:** Touch-friendly, gestos, menús adaptados

### 15.3 Tema Visual: "Void Command"

**Concepto:**
Interfaz de comando espacial moderna, como si estuvieras en el puente de una nave estelar.

**Elementos visuales:**
- **Fondo:** Gradiente oscuro sutil con efecto de partículas estelares (canvas/CSS)
- **Paneles:** Bordes con glow sutil, fondos semi-transparentes
- **Botones:** Estilo sci-fi con estados hover/active animados
- **Inputs:** Border glow al focus, placeholder text sugerente
- **Modals:** Overlay oscuro, panel central con animación de entrada
- **Stats/Barras:** Gradientes de color según valor (rojo=bajo, verde=alto)

**Ejemplo conceptual de un panel:**

```
┌─────────────────────────────────────────────┐
│ ⚡ ENERGÍA                          85/100  │ ← Header con ícono
│ ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓░░░ (+5% eficiencia)      │ ← Barra visual + estado
│                                             │
│ 🍖 NUTRICIÓN                        60/100  │
│ ▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░ (Normal)               │
│ [!] Comer pronto                            │ ← Alerta visual
└─────────────────────────────────────────────┘
```

*Esto sería renderizado con divs, CSS, gradientes, no con caracteres ASCII.*

### 15.4 Componentes Principales

### 15.4.1 Breadcrumb Dinámico

Siempre visible, muestra ubicación actual.

**Ejemplo:**

```
Vaxav > Vaxav III > Luna 2 > Puerto Estelar Génesis > Hangar
```

### 15.4.2 Panel de Información de Piloto

Header persistente:
- Nombre del piloto
- Créditos actuales
- Estado actual
- Nave actual (si aplica)
- Ubicación actual

### 15.4.3 Vistas de Ubicación

Componente reutilizable según tipo de ubicación.

**Estructura:**
- **Encabezado:** Nombre y descripción
- **Información contextual:** Específico de la ubicación
- **Acciones disponibles:** Botones/links
- **Entidades presentes:** Otras naves, jugadores, etc.

### 15.4.4 Panel de Acciones

Lista clara de acciones disponibles según ubicación.

**Ejemplo en Campo de Asteroides:**
- [ Minar ] - Láser de Minería Básico (15 ticks)
- [ Escanear ] - Buscar nuevos asteroides
- [ Ver Naves ] - Listar otras naves presentes
- [ Viajar ] - Ir a otra ubicación

### 15.4.5 Contador de Ticks

Muestra acciones en progreso.

**Ejemplo:**

```
⏳ Minando Tritanio... [████████░░] 8/10 ticks
   Estimado: 120 segundos restantes
```

### 15.5 Esquema de URLs

URLs RESTful y descriptivas.

**Ejemplos:**

```
/dashboard
/pilot/profile
/pilot/skills
/pilot/skills/tree                    # Árbol completo de habilidades
/pilot/skills/discovered              # Habilidades descubiertas no inyectadas
/pilot/skills/injected                # Habilidades inyectadas

/system/{system_id}
/system/{system_id}/planet/{planet_id}
/system/{system_id}/planet/{planet_id}/moon/{moon_id}

/station/{station_id}
/station/{station_id}/module/{module_type}
/station/{station_id}/hangar
/station/{station_id}/laboratory      # Vista del laboratorio
/station/{station_id}/laboratory/catalog  # Catálogo de inyectores
/station/{station_id}/laboratory/inject   # Inyectar habilidad
/station/{station_id}/market

/ship/{ship_id}
/ship/{ship_id}/modules
/ship/{ship_id}/cargo

/corporation/{corp_id}
/corporation/{corp_id}/members

/market/browse
/market/browse/injectors              # Mercado de inyectores
/market/browse/injectors/{skill_id}   # Órdenes de un inyector específico
/market/orders
/market/orders/my                     # Mis órdenes activas
/market/history

/missions
/missions/{mission_id}
```

### 15.6 Bibliotecas y Herramientas UI Recomendadas

Para implementar la interfaz moderna:

**Gráficos y Visualización:**
- **Chart.js** o **ApexCharts** - Gráficos de precios de mercado, estadísticas
- **ProgressBar.js** - Barras de progreso animadas (energía, skills, etc.)

**Componentes UI:**
- **Headless UI** (by Tailwind) - Componentes accesibles sin estilos
- **Alpine.js Components** - Dropdowns, modals, tabs, tooltips
- **Heroicons** - Sistema de íconos consistente

**Efectos Visuales:**
- **Particles.js** o **tsParticles** - Efecto de estrellas en el fondo
- **GSAP** - Animaciones complejas si son necesarias
- **AOS (Animate On Scroll)** - Animaciones de entrada suaves

**Utilidades:**
- **Moment.js** o **Day.js** - Formateo de fechas/tiempos
- **Numeral.js** - Formateo de números grandes (créditos, cantidades)
- **Tippy.js** - Tooltips elegantes y configurables

---

## Navegación

- [← Anterior: PRD-SocialSystem.md](./PRD-SocialSystem.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-TechnicalArchitecture.md](./PRD-TechnicalArchitecture.md)
