# Naves, Combate y Estados

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 7. Naves

### 7.1 Características Generales

**Atributos Base:**
- **Nombre:** Identificación única de la nave
- **Clase:** Fragata, Crucero, Acorazado, etc.
- **Escudos:** Puntos de escudo (primera línea de defensa)
- **Armadura:** Puntos de armadura (segunda línea)
- **Estructura:** Puntos de estructura (última línea)
- **Carga:** Capacidad de bodega en m³
- **Velocidad:** Unidades de movimiento por tick
- **Slots de módulos:**
  - Sistemas Ofensivos: 1-5 slots
  - Sistemas Defensivos: 1-5 slots
  - Sistemas de Utilidad: 1-5 slots
- **Bonos de nave:** Modificadores específicos
- **Requerimientos:** Habilidades necesarias

### 7.2 Clases de Naves

### 7.2.1 Fragatas

**Características:**
- Naves pequeñas y versátiles
- Bajo costo de entrada
- Rápidas y maniobrables

**Ejemplo - Excavador MK-I (Fragata Minera):**

```json
{  "nombre": "Excavador MK-I",  "clase": "Fragata",  "tipo": "Minera",  "escudos": 500,  "armadura": 800,  "estructura": 600,  "carga": 5000,  "velocidad": 15,  "slots_ofensivos": 1,  "slots_defensivos": 2,  "slots_utilidad": 3,  "bonos": {    "mineria_tick_reduction": 0.15,    "carga_minerales": 1.25  },  "requerimientos": {    "pilotaje_fragatas": 1,    "mineria": 1  }}
```

**Ejemplo - Depredador (Fragata de Combate):**

```json
{  "nombre": "Depredador",  "clase": "Fragata",  "tipo": "Combate",  "escudos": 800,  "armadura": 600,  "estructura": 500,  "carga": 200,  "velocidad": 20,  "slots_ofensivos": 3,  "slots_defensivos": 2,  "slots_utilidad": 2,  "bonos": {    "danio_proyectiles": 1.10,    "rastreo": 1.15  },  "requerimientos": {    "pilotaje_fragatas": 2  }}
```

### 7.2.2 Cruceros

Naves medianas, equilibrio entre poder y costo.

**Slots típicos:** 4 ofensivos, 4 defensivos, 3 utilidad
**Requerimientos:** Pilotaje de Cruceros (requiere Fragatas Lvl 3)

### 7.2.3 Acorazados

Naves pesadas, gran poder de fuego.

**Slots típicos:** 5 ofensivos, 5 defensivos, 3 utilidad
**Requerimientos:** Pilotaje de Acorazados (requiere Cruceros Lvl 4)

### 7.2.4 Cargueros

Especializados en transporte.

**Variantes:**
- Ligero: 50,000 m³
- Mediano: 200,000 m³
- Pesado: 1,000,000 m³

### 7.2.5 Naves Capitales

Las más grandes y poderosas (end-game).

**Tipos:**
- Portanaves
- Dreadnoughts
- Titans

### 7.2.6 Sistema de Tiers de Naves

Todas las naves (excepto algunas únicas) vienen en 3 niveles tecnológicos (Tech Levels o Tiers).

**Tech 1 (T1) - Naves Estándar:**
- **Disponibilidad:** Común, fácil de fabricar
- **Costo:** Bajo (500,000₡ - 5,000,000₡ según clase)
- **Bonos:** Sin bonos especiales
- **Características:** Naves funcionales básicas
- **Ejemplo:** Excavador MK-I (Fragata T1)
- **Recursos fabricación:** Tier 1-2 (Ferrita, Cobre Estelar, Titanita)

**Tech 2 (T2) - Naves Avanzadas:**
- **Disponibilidad:** Poco común, requiere Blueprint mejorado
- **Costo:** Medio (2,000,000₡ - 20,000,000₡)
- **Bonos:** +15% a estadísticas base (HP, daño, velocidad)
- **Características:** Especializaciones marcadas (minería T2 tiene +25% eficiencia minería)
- **Ejemplo:** Excavador MK-II (Fragata T2)
- **Recursos fabricación:** Tier 2-3 (Duralinio Espacial, Magnetita Pura, Cristales de Zafiro)
- **Requisito skill:** +1 nivel más que T1 (ej: Pilotaje Fragatas nivel 3 para T2)

**Tech 3 (T3) - Naves Experimentales:**
- **Disponibilidad:** Rara, Blueprints solo de exploración avanzada o investigación nivel 5
- **Costo:** Alto (10,000,000₡ - 100,000,000₡)
- **Bonos:** +30% estadísticas base + habilidad especial única
- **Habilidades Especiales:**
  - Fragatas T3: Pueden equipar módulo de camuflaje avanzado
  - Cruceros T3: Resistencia +20% a todos los tipos de daño
  - Cargueros T3: Warp instantáneo (sin tiempo de carga)
- **Ejemplo:** Excavador MK-III (Fragata T3) - Puede minar asteroides T4 sin penalización
- **Recursos fabricación:** Tier 3-4 (Adamantita, Neutronium, Plasma, Xenón)
- **Requisito skill:** +2 niveles más que T1 (ej: Pilotaje Fragatas nivel 4 para T3)

**Balance:**
- T2 es 30-40% más poderosa que T1, pero cuesta 4-5x más
- T3 es 60-80% más poderosa que T1, pero cuesta 20-30x más y es difícil de obtener
- La progresión NO es obligatoria: T1 bien equipado puede competir en muchos escenarios
- T3 es más "side-grade" que "upgrade" directo (especialización extrema)

### 7.3 Fitting System (Sistema de Equipamiento)

Las naves tienen recursos limitados que los módulos consumen. El jugador debe balancear qué módulos equipar.

#### 7.3.1 Recursos de Fitting

Cada nave tiene 3 recursos limitados:

**1. Powergrid (PG) - Red de Energía:**
- **Descripción:** Energía total que la nave puede suministrar a los módulos
- **Unidad:** Megawatts (MW)
- **Uso:** Módulos activos (armas, escudos, propulsores) consumen PG
- **Ejemplo:**
  - Excavador MK-I (Fragata T1): 50 MW
  - Crucero T1: 150 MW
  - Acorazado T1: 400 MW

**2. CPU - Procesamiento:**
- **Descripción:** Capacidad de procesamiento para controlar módulos complejos
- **Unidad:** Teraflops (TF)
- **Uso:** Módulos tecnológicos (scanners, sistemas de targeting, computadoras) consumen CPU
- **Ejemplo:**
  - Excavador MK-I (Fragata T1): 200 TF
  - Crucero T1: 500 TF
  - Acorazado T1: 1000 TF

**3. Capacitor - Condensador:**
- **Descripción:** Batería que regenera energía para módulos activos durante combate/operaciones
- **Unidad:** Gigajoules (GJ)
- **Regeneración:** X GJ por tick (varía según nave)
- **Uso:** Módulos activos consumen capacitor al activarse (armas, reparadores, propulsores)
- **Ejemplo:**
  - Excavador MK-I (Fragata T1): 500 GJ, regenera 25 GJ/tick
  - Crucero T1: 2000 GJ, regenera 80 GJ/tick
  - Acorazado T1: 5000 GJ, regenera 150 GJ/tick

**Diferencia PG vs Capacitor:**
- **PG:** Límite estático de fitting (no puedes equipar más módulos si excedes PG)
- **Capacitor:** Recurso dinámico durante operaciones (puedes quedarte sin capacitor en combate)

#### 7.3.2 Consumo de Módulos

Cada módulo tiene requisitos de fitting.

**Ejemplo - Cañón Automático Ligero T1:**

```json
{
  "nombre": "Cañón Automático Ligero",
  "tier": 1,
  "tipo": "arma_proyectiles",
  "slot": "ofensivo",
  "pg_requerido": 8,
  "cpu_requerido": 15,
  "capacitor_por_disparo": 20,
  "dps": 25,
  "alcance": 15000,
  "tracking": 0.5,
  "skill_requerida": {
    "armas_proyectiles": 1
  }
}
```

**Ejemplo - Generador de Escudos Mediano T2:**

```json
{
  "nombre": "Generador de Escudos Mediano II",
  "tier": 2,
  "tipo": "escudo",
  "slot": "defensivo",
  "pg_requerido": 12,
  "cpu_requerido": 25,
  "hp_escudos": 800,
  "regeneracion_pasiva": 10,
  "capacitor_regen_activo": 50,
  "skill_requerida": {
    "escudos": 3
  }
}
```

**Ejemplo - Scanner Planetario T1:**

```json
{
  "nombre": "Scanner Planetario Básico",
  "tier": 1,
  "tipo": "utilidad_escaneo",
  "slot": "utilidad",
  "pg_requerido": 3,
  "cpu_requerido": 40,
  "capacitor_por_escaneo": 100,
  "calidad_escaneo": 5,
  "skill_requerida": {
    "escaneo_planetario": 1
  }
}
```

#### 7.3.3 Reglas de Fitting

**Restricciones:**
- No puedes equipar módulos si excedes PG o CPU de la nave
- Puedes equipar módulos que sumen más capacitor del que tienes, pero no podrás usarlos todos simultáneamente
- Los módulos Tier 2 requieren skills más altos que Tier 1
- Los módulos Tier 3 requieren skills nivel 4-5

**Stacking Penalties:**
- Equipar múltiples módulos del mismo tipo reduce su efectividad
- **Fórmula:**

```
efectividad_modulo_N = efectividad_base × (0.87 ^ (N - 1))
```

- Ejemplo: 3x Amplificador de Daño (+10% cada uno)
  - Módulo 1: +10.0%
  - Módulo 2: +8.7% (10 × 0.87)
  - Módulo 3: +7.6% (10 × 0.87²)
  - **Total:** +26.3% en lugar de +30%

**Implica que:**
- Diversificar módulos suele ser mejor que "stackear" el mismo
- Existen límites prácticos al min-maxing

#### 7.3.4 Fitting Planner (Planificador de Equipamiento)

**Descripción:**
Herramienta in-game donde los jugadores pueden diseñar configuraciones de naves antes de comprar/fabricar módulos.

**Funcionalidades:**
1. **Vista de Nave:** Muestra la nave seleccionada con sus slots y recursos (PG, CPU, Capacitor)
2. **Biblioteca de Módulos:** Lista filtrable de módulos disponibles (por tier, tipo, skill)
3. **Drag & Drop:** Arrastrar módulos a slots de la nave
4. **Indicadores en Tiempo Real:**
   - Barras de PG usado / total (verde si OK, rojo si excede)
   - Barras de CPU usado / total
   - Capacitor total y tiempo hasta agotamiento si todos los módulos activos están ON
5. **Estadísticas Calculadas:**
   - DPS total
   - HP total (escudos + armadura + estructura)
   - Velocidad efectiva
   - Alcance de armas
   - Capacidad de carga
6. **Simulación de Combate (básica):**
   - "¿Cuántos ticks sobrevivo contra fragata T1 NPC?"
   - "¿Puedo sostener todas mis armas + reparador simultáneamente?"
7. **Guardar Fits:**
   - Los jugadores pueden guardar configuraciones con nombres
   - Compartir fits con corpmates (exportar como texto/JSON)
8. **Validación:**
   - Marca errores: "No tienes skill Armas de Energía nivel 3"
   - Sugerencias: "Recomendamos un Amplificador de CPU para este fit"

**Acceso:**
- Disponible desde cualquier estación con Hangar
- También disponible como herramienta web externa (si el juego tiene API)

#### 7.3.5 Módulos Pasivos vs Activos

**Módulos Pasivos:**
- Siempre están ON
- Solo consumen PG y CPU (en el fitting)
- No consumen capacitor durante operaciones
- **Ejemplos:** Placas de Armadura, Expansores de Carga, Refuerzos Estructurales

**Módulos Activos:**
- Deben activarse manualmente (o por doctrina de combate)
- Consumen capacitor al usarse
- Tienen cooldown entre activaciones
- **Ejemplos:** Armas, Reparadores, Propulsores, Scanners

**Balance:**
- Módulos pasivos suelen ser menos poderosos pero más confiables
- Módulos activos son más fuertes pero dependen del capacitor

### 7.4 Estados de Nave

- **Atracada:** En hangar de estación
- **Orbitando:** Alrededor de estación/planeta/luna
- **En tránsito:** Viajando entre ubicaciones
- **En combate:** Participando en batalla
- **Minando:** Extrayendo recursos
- **Destruida:** Wreck recuperable

### 7.5 Módulos de Nave por Tier

Todos los módulos existen en 3 tiers con mejoras progresivas.

### 7.5.1 Sistemas Ofensivos

**Armas de Proyectiles:**
- **Tier 1:** Cañón Automático Ligero - 25 DPS, 8 PG, 15 CPU, 20 cap/disparo
- **Tier 2:** Cañón de Riel - 40 DPS, 15 PG, 25 CPU, 35 cap/disparo (requiere Armas Proyectiles 3)
- **Tier 3:** Artillería de Neutrones - 70 DPS, 30 PG, 45 CPU, 60 cap/disparo (requiere Armas Proyectiles 4)
- **Daño:** Fuerte contra armadura (+50%)

**Armas de Energía:**
- **Tier 1:** Láser de Pulso - 22 DPS, 10 PG, 20 CPU, 25 cap/disparo
- **Tier 2:** Láser de Haz - 38 DPS, 18 PG, 35 CPU, 45 cap/disparo (requiere Armas Energía 3)
- **Tier 3:** Láser de Fase Cuántico - 65 DPS, 35 PG, 50 CPU, 70 cap/disparo (requiere Armas Energía 4)
- **Daño:** Fuerte contra escudos (+50%)

**Armas Híbridas:**
- **Tier 1:** Blaster Básico - 20 DPS, 9 PG, 18 CPU, 22 cap/disparo
- **Tier 2:** Cañón de Iones - 35 DPS, 16 PG, 30 CPU, 40 cap/disparo (requiere Armas Híbridas 3)
- **Tier 3:** Disruptor de Antimateria - 60 DPS, 32 PG, 48 CPU, 65 cap/disparo (requiere Armas Híbridas 4)
- **Daño:** Balanceado (escudos y armadura)

**Misiles:**
- **Tier 1:** Lanzamisiles Ligero - 30 DPS, 5 PG, 25 CPU, 15 cap/lanzamiento + munición
- **Tier 2:** Lanzamisiles Pesado - 55 DPS, 12 PG, 40 CPU, 30 cap/lanzamiento + munición (requiere Misiles 3)
- **Tier 3:** Torpedos de Crucero - 95 DPS, 25 PG, 60 CPU, 50 cap/lanzamiento + munición (requiere Misiles 4)
- **Daño:** Variable según munición (explosivo, cinético, EM, térmico)

### 7.5.2 Sistemas Defensivos

**Generadores de Escudos:**
- **Tier 1 Pequeño:** +400 HP escudos, 8 PG, 15 CPU, pasivo
- **Tier 1 Mediano:** +800 HP escudos, 15 PG, 25 CPU, pasivo
- **Tier 1 Grande:** +1500 HP escudos, 30 PG, 40 CPU, pasivo (requiere Escudos 2)
- **Tier 2 Pequeño:** +600 HP escudos, 10 PG, 18 CPU, pasivo (requiere Escudos 3)
- **Tier 2 Mediano:** +1200 HP escudos, 20 PG, 30 CPU, pasivo (requiere Escudos 3)
- **Tier 3 Grande:** +2500 HP escudos, 45 PG, 55 CPU, +10% resist todas (requiere Escudos 4)

**Recargadores de Escudos:**
- **Tier 1:** Regen +15 HP/tick, 12 PG, 20 CPU, 40 cap/activación, activo
- **Tier 2:** Regen +30 HP/tick, 20 PG, 35 CPU, 70 cap/activación, activo (requiere Escudos 3)
- **Tier 3:** Regen +60 HP/tick, 35 PG, 50 CPU, 120 cap/activación, activo (requiere Escudos 4)

**Placas de Armadura:**
- **Tier 1 Pequeña:** +300 HP armadura, 5 PG, 10 CPU, pasivo
- **Tier 1 Mediana:** +700 HP armadura, 10 PG, 18 CPU, pasivo
- **Tier 1 Grande:** +1300 HP armadura, 20 PG, 30 CPU, pasivo (requiere Blindaje 2)
- **Tier 2 Grande:** +2000 HP armadura, 30 PG, 40 CPU, +5% resist explosivo (requiere Blindaje 3)
- **Tier 3 Grande:** +3500 HP armadura, 50 PG, 60 CPU, +10% resist todos (requiere Blindaje 4)

**Reparadores de Armadura:**
- **Tier 1:** Repara 20 HP/tick, 15 PG, 25 CPU, 50 cap/activación, activo
- **Tier 2:** Repara 40 HP/tick, 25 PG, 40 CPU, 90 cap/activación, activo (requiere Blindaje 3)
- **Tier 3:** Repara 80 HP/tick, 40 PG, 60 CPU, 150 cap/activación, activo (requiere Blindaje 4)

**Refuerzos Estructurales:**
- **Tier 1:** +200 HP estructura, 3 PG, 8 CPU, pasivo
- **Tier 2:** +400 HP estructura, 6 PG, 15 CPU, pasivo
- **Tier 3:** +800 HP estructura, 12 PG, 25 CPU, pasivo

### 7.5.3 Sistemas de Utilidad

**Minería:**
- **Tier 1:** Láser de Minería Básico - Reduce 1 tick minería, 10 PG, 20 CPU, 30 cap/ciclo
- **Tier 2:** Láser de Minería Avanzado - Reduce 2 ticks, +15% yield, 18 PG, 35 CPU, 50 cap/ciclo (requiere Minería 3)
- **Tier 3:** Dron Minero Automático - Reduce 3 ticks, +30% yield, puede minar múltiples asteroides, 30 PG, 50 CPU, 80 cap/ciclo (requiere Minería 4, Drones 2)

**Extracción Especializada:**
- **Extractor Criogénico T1:** Para hielo Tier 1-2, 12 PG, 25 CPU, 40 cap/ciclo (requiere Extracción Criogénica 1)
- **Extractor Criogénico T2:** Para hielo Tier 2-3, reduce 1 tick, 20 PG, 40 CPU, 70 cap/ciclo (requiere Extracción Criogénica 3)
- **Extractor Criogénico T3:** Para hielo Tier 3-4, reduce 2 ticks, +20% yield, 35 PG, 60 CPU, 110 cap/ciclo (requiere Extracción Criogénica 5)

**Recolectores de Gas:**
- **Recolector de Gas T1:** Para nebulosas Tier 1-2, 8 PG, 30 CPU, 35 cap/ciclo (requiere Recolección Gas 1)
- **Recolector de Gas T2:** Para nebulosas Tier 2-3, +25% yield, 15 PG, 45 CPU, 60 cap/ciclo (requiere Recolección Gas 3)
- **Recolector de Gas T3:** Para nebulosas Tier 3-4, +50% yield, detección previa tormentas, 28 PG, 70 CPU, 100 cap/ciclo (requiere Recolección Gas 5)

**Expansores de Carga:**
- **Tier 1:** +500 m³, 3 PG, 10 CPU, pasivo
- **Tier 2:** +1000 m³, 5 PG, 18 CPU, pasivo
- **Tier 3:** +2000 m³, 10 PG, 30 CPU, pasivo

**Propulsores:**
- **Tier 1 Básico:** +15% velocidad, 8 PG, 15 CPU, 25 cap/activación (10 ticks), activo
- **Tier 2 Mejorado:** +30% velocidad, 15 PG, 25 CPU, 45 cap/activación (10 ticks), activo (requiere Navegación 2)
- **Tier 3 Avanzado:** +50% velocidad, reduce tiempo warp 20%, 25 PG, 40 CPU, 75 cap/activación (10 ticks), activo (requiere Navegación 4)
- **Motor de Salto:** Necesario para usar Stargates, 20 PG, 50 CPU, pasivo (requiere Navegación 3)

**Scanners:**
- **Scanner de Carga T1:** Detecta carga de otras naves, 2 PG, 25 CPU, 50 cap/escaneo
- **Scanner de Combate T1:** Detecta naves hostiles, 3 PG, 30 CPU, 60 cap/escaneo (requiere Rastreo 1)
- **Scanner de Anomalías T1:** Detecta sitios temporales, 5 PG, 40 CPU, 80 cap/escaneo (requiere Exploración 1)
- **Scanner Planetario T1:** Escanea planetas, calidad 5, 3 PG, 40 CPU, 100 cap/escaneo (requiere Escaneo Planetario 1)
- **Scanner Planetario T2:** Escanea planetas, calidad 10, 6 PG, 60 CPU, 150 cap/escaneo (requiere Escaneo Planetario 3)
- **Scanner Planetario T3:** Escanea planetas, calidad 15, +20% velocidad escaneo, 12 PG, 90 CPU, 220 cap/escaneo (requiere Escaneo Planetario 5)

**Módulos de Sigilo:**
- **Camuflaje Básico T1:** +15% Sigilo, 10 PG, 20 CPU, 40 cap/activación (dura 5 ticks), activo (requiere Sigilo 1)
- **Camuflaje Avanzado T2:** +30% Sigilo, 18 PG, 35 CPU, 70 cap/activación (dura 8 ticks), activo (requiere Sigilo 3)
- **Cloak de Invisibilidad T3:** +60% Sigilo, invisibilidad casi total si no te mueves, 30 PG, 55 CPU, 120 cap/activación (dura 10 ticks), activo (requiere Sigilo 5, solo naves T3)

**Otros:**
- **Estabilizador de Salto T1:** Reduce fatiga de salto 15%, 5 PG, 15 CPU, pasivo
- **Reparador Remoto T1:** Repara nave aliada a distancia, 20 PG, 30 CPU, 80 cap/activación, activo (requiere Logística 2)
- **Transmisor de Energía T1:** Transfiere capacitor a nave aliada, 15 PG, 25 CPU, 60 cap/activación, activo (requiere Logística 2)
- **Amplificador de CPU T1:** +10% CPU total nave, 5 PG, 0 CPU (no consume CPU), pasivo (requiere Ingeniería 2)
- **Relé de Powergrid T1:** +10% PG total nave, 0 PG, 15 CPU, pasivo (requiere Ingeniería 2)

---

## 8. Sistema de Combate

### 8.1 Mecánica de Combate

El combate es por turnos automáticos basado en ticks.

**Inicio de Combate:**
- Un piloto "ataca" a otro
- Se crea una instancia de combate
- Otros pilotos pueden unirse (si están en la ubicación)
- Los combates son visibles en la ubicación

**Turno de Combate (cada tick):**
1. Calcular orden de ataque (basado en velocidad)
2. Para cada nave:
   - Seleccionar objetivo (según Doctrina)
   - Calcular impacto (precisión vs evasión)
   - Calcular daño (arma vs defensas)
   - Aplicar daño (escudos → armadura → estructura)
3. Verificar condiciones de fin
4. Repetir

### 8.2 Tipos de Daño

**Daño Anti-Escudo:**
- **Armas:** Láser, Armas de Energía
- **Multiplicador vs Escudos:** 1.5x
- **Multiplicador vs Armadura:** 0.7x
- **Multiplicador vs Estructura:** 0.8x

**Daño Anti-Armadura:**
- **Armas:** Proyectiles, Artillería
- **Multiplicador vs Escudos:** 0.7x
- **Multiplicador vs Armadura:** 1.5x
- **Multiplicador vs Estructura:** 1.0x

**Daño Híbrido:**
- **Armas:** Blasters, Iones
- **Multiplicador vs Escudos:** 1.0x
- **Multiplicador vs Armadura:** 1.0x
- **Multiplicador vs Estructura:** 1.2x

### 8.3 Doctrina de Combate

Configuración pre-establecida por el jugador que determina el comportamiento automático en combate.

**Parámetros Configurables:**

**Selección de Objetivo:**
- Más cercano
- Más débil (menor estructura)
- Más fuerte (mayor estructura)
- Más peligroso (mayor DPS)
- Aleatorio

**Uso de Módulos:**
- Reparar escudos cuando < X%
- Reparar armadura cuando < X%
- Usar propulsores (huir) cuando estructura < X%

**Condiciones de Huida:**
- Nunca huir
- Huir si estructura < 30%
- Huir si estructura < 50%
- Huir si superado en número

**Agresividad:**
- Defensiva (prioriza supervivencia)
- Balanceada
- Agresiva (prioriza daño)

### 8.4 Recompensas de Combate

- **Experiencia:** Basada en dificultad del enemigo
- **Loot:** Items del wreck de la nave destruida
- **Reputación:** +/- según facción del enemigo
- **Recompensas (Bounties):** Si el objetivo tenía precio

### 8.5 Muerte y Clonación

Cuando la estructura de una nave llega a 0:

**Nave:**
- Destruida → se convierte en Wreck
- Wreck contiene % de los items/módulos
- Wreck puede ser saqueado

**Piloto:**
- Muere si no tiene cápsula de escape
- Con cápsula: puede huir
- Si muere: respawnea en último clon

**Sistema de Clones:**
- Se crean en Laboratorios (ver [PRD-Universe.md](./PRD-Universe.md#6.2.3-laboratorio))
- Guardan punto de reaparición
- Al morir: pierdes skills no guardados en clon
- Clon puede estar en cualquier estación
- Cooldown de actualización de clon: 144 ticks (~24h)

---

## 9. Modificaciones Ilegales de Naves

Modificaciones prohibidas disponibles solo en Mercados Negros Flotantes (ver [PRD-Universe.md](./PRD-Universe.md)).

### 9.1 Concepto

Las modificaciones ilegales son alteraciones permanentes o semi-permanentes de naves que ofrecen ventajas significativas pero violan las regulaciones de la Confederación Vaxav. Estas modificaciones flaggean la nave como "ilegal" y tienen consecuencias severas si son detectadas por la flota Albatross en sistemas de alta seguridad.

### 9.2 Tipos de Modificaciones

#### 9.2.1 Eliminar Transponder

**Descripción:** Remoción completa del transponder de identificación de la nave.

**Beneficios:**
- Stealth permanente: La nave NO aparece en radares de otros jugadores
- Inmunidad a escaneos de detección normales
- Perfecta para operaciones encubiertas, emboscadas, evasión

**Consecuencias:**
- Nave flagged como criminal en sistemas sec 0.5+
- Albatross ataca a la vista en sec 0.5+ (sin advertencia)
- NO REVERSIBLE (no puede deshacerse)
- Standing permanente -50 con Confederación si detectada

**Costo:** 200,000₡

**Implementación Técnica:**
- Modificación permanente en tabla `illegal_ship_modifications`
- Nave invisible en sistema de detección de naves
- Albatross tiene script especial: si `ship.has_no_transponder AND system.security >= 0.5 THEN attack_immediately()`

#### 9.2.2 Amplificador Ilegal de PG/CPU

**Descripción:** Bypass de los limitadores de fábrica en powergrid y CPU.

**Beneficios:**
- +25% Powergrid total
- +25% CPU total
- Permite fitting de módulos más poderosos

**Consecuencias:**
- Nave ilegal, Albatross ataca en sec 0.5+
- Advertencia de 30 segundos antes del ataque (tiempo para huir)
- Detectable por escaneos profundos (20% chance por escaneo)
- Standing -10 con Confederación si detectada

**Costo:** 350,000₡

**Reversibilidad:** SÍ (costo 100,000₡ en cualquier estación con Sala de Ingeniería)

**Implementación Técnica:**
- Modificador en stats de nave: `ship.powergrid *= 1.25; ship.cpu *= 1.25`
- Flag `is_illegal = true`
- Albatross tiene advertencia de 30 segundos (5 ticks) antes de atacar

#### 9.2.3 Reactor Black Hole

**Descripción:** Reactor experimental de materia oscura con capacitor infinito pero inestable.

**Beneficios:**
- Capacitor infinito (nunca se agota)
- Todos los módulos activos pueden funcionar permanentemente
- No hay gestión de energía necesaria

**Consecuencias:**
- 5% chance de explosión catastrófica cada tick mientras está en combate
- Explosión = destrucción inmediata de nave (sin wreck, sin salvamento)
- Standing -25 con Sindicato Técnico (consideran la tecnología peligrosa)

**Costo:** 1,000,000₡

**Reversibilidad:** SÍ (costo 250,000₡, requiere Sala de Ingeniería Nivel 3+)

**Implementación Técnica:**
- `ship.capacitor_infinite = true`
- Cada tick en combate: `if random(0,100) <= 5 THEN explode_ship(ship_id)`
- Explosión ignora cápsula de escape (muerte garantizada del piloto)

#### 9.2.4 Sistema de Puntería Ilegal

**Descripción:** IA de targeting militar prohibida con algoritmos de puntería mejorados.

**Beneficios:**
- +40% tracking speed
- +25% optimal range
- +15% falloff range
- Mejora significativa en precisión de armas

**Consecuencias:**
- Nave ilegal permanentemente
- Albatross ataca en sec 0.5+ (advertencia 10 segundos)
- Detectable por escaneos (30% chance)
- Standing -15 con Confederación

**Costo:** 450,000₡

**Reversibilidad:** NO (sistema integrado en computadora de la nave)

**Implementación Técnica:**
- Modificadores en módulos de arma:
  ```
  weapon.tracking *= 1.40
  weapon.optimal_range *= 1.25
  weapon.falloff_range *= 1.15
  ```

### 9.3 Mecánica de Detección de Albatross

**Sistemas Sec 0.5-1.0:**

1. **Entrada al Sistema:**
   - Albatross escanea todas las naves que entran
   - Detección automática de naves sin transponder (100% detección)
   - Detección probabilística de otras modificaciones:
     - Amplificador PG/CPU: 20% por escaneo
     - Reactor Black Hole: 10% por escaneo (difícil de detectar externamente)
     - Sistema Puntería: 30% por escaneo

2. **Consecuencias de Detección:**
   - **Sin Transponder:** Ataque inmediato sin advertencia
   - **Otras Modificaciones:**
     - Primera detección: Advertencia de "30 segundos para salir del sistema"
     - Si permaneces: Flota Albatross spawneada (4-6 naves T3-T4)
     - Muerte casi segura salvo naves muy poderosas o huida inmediata
     - Standing negativo aplicado

3. **Escaneo Continuo:**
   - Re-escaneo cada 10-30 ticks mientras estés en el sistema
   - Cada escaneo tiene probabilidad acumulativa de detectar modificaciones

**Sistemas Sec 0.1-0.4:**
- Albatross solo en stargates
- Escaneo solo al usar stargate (1 vez)
- 50% menos probabilidad de detección

**Sistemas Sec 0.0:**
- Sin Albatross
- Modificaciones ilegales sin riesgo

### 9.4 Economía de Modificaciones Ilegales

**ROI (Return on Investment):**

| Modificación | Costo | Beneficio | ROI Estimado | Riesgo |
|--------------|-------|-----------|--------------|--------|
| Eliminar Transponder | 200K₡ | Stealth total | Alto (PvP, piratería) | Extremo |
| Amplificador PG/CPU | 350K₡ | +25% fitting | Medio (fittings T3) | Alto |
| Reactor Black Hole | 1M₡ | Cap infinito | Bajo (riesgo explosión) | Muy Alto |
| Sistema Puntería | 450K₡ | +40% tracking | Alto (PvP) | Alto |

**Casos de Uso Comunes:**

1. **Piratería en Null-Sec:**
   - Eliminar Transponder + Sistema Puntería
   - Costo: 650K₡
   - Beneficio: Emboscadas perfectas, alto damage
   - Riesgo: Solo si entra a sec 0.5+

2. **Minería en Low-Sec:**
   - Amplificador PG/CPU
   - Costo: 350K₡
   - Beneficio: Fitting con más láseres de minería + escudos potentes
   - Riesgo: Evitar sec 0.5+, minería en 0.1-0.4

3. **PvP Extremo (Locura):**
   - Reactor Black Hole + Sistema Puntería + Amplificador PG/CPU
   - Costo: 1.8M₡
   - Beneficio: Nave imparable (capacitor infinito, damage máximo)
   - Riesgo: 5% muerte cada tick en combate + detección Albatross

### 9.5 Consideraciones de Balance

**Pros de Modificaciones Ilegales:**
- Poder significativo en naves
- Ventaja estratégica en null-sec
- Fittings imposibles sin ellas
- Economía de riesgo/recompensa interesante

**Contras:**
- Costo alto
- Riesgo de detección y destrucción
- Standing negativo permanente con facciones
- Restricción geográfica (solo viable en low/null-sec)
- Algunas no reversibles

**Diseño Intencional:**
El sistema está diseñado para crear una división clara entre:
- **Pilotos Lawful:** Operan en sec 0.5+ sin preocupaciones, sacrifican poder
- **Pilotos Outlaw:** Operan en null-sec con naves modificadas poderosas, evitan sistemas seguros

---

## 12. Estados del Piloto

El piloto puede estar en múltiples estados simultáneos.

**Estados Primarios:**
- **En Estación:** Dentro de una estación
- **En Órbita:** Orbitando luna/planeta/estación
- **En Tránsito:** Viajando entre ubicaciones
- **Sin Nave:** En estación sin nave activa

**Estados de Acción:**
- **Minando:** Extrayendo recursos
- **En Combate:** Participando en batalla
- **Fabricando:** Usando Sala de Ingeniería
- **Reparando:** En hangar
- **Descansando:** En habitáculos

---

## Navegación

- [← Anterior: PRD-Universe.md](./PRD-Universe.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-Economy.md](./PRD-Economy.md)
