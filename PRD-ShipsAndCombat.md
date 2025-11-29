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

Las más grandes y poderosas (end-game). Tienen capacidades únicas incluyendo saltos interestelares sin uso de Stargates.

**Tipos:**
- **Portanaves:** Naves de soporte que transportan cazas y fragatas
- **Dreadnoughts:** Naves de asalto pesado con artillería masiva
- **Titans:** Naves gigantescas, las más poderosas del juego

**Capacidad de Salto Interestelar:**

Las naves capitales pueden realizar saltos FTL directos entre sistemas sin usar Stargates, consumiendo combustible especial.

**Requisitos:**
- Módulo: Motor de Salto FTL (integrado en todas las naves capitales)
- Combustible: Reactores de Antimateria (Tier 4)
- Skill: Navegación Capital Nivel 3+

**Mecánica de Salto:**
1. Seleccionar sistema destino (debe estar dentro del rango máximo)
2. Cargar Reactores de Antimateria en bahía de combustible (1 reactor por salto)
3. Iniciar secuencia de salto (preparación: 15 ticks, cancelable)
4. Durante preparación: Nave vulnerable, no puede moverse ni atacar
5. Al completar: Salto instantáneo al sistema destino
6. Cooldown: 60 minutos antes del próximo salto
7. Costo: 1 Reactor de Antimateria (50,000₡) por salto

**Rango de Salto por Tipo:**
- **Portanaves:** 3 sistemas de distancia
- **Dreadnought:** 4 sistemas de distancia
- **Titan:** 5 sistemas de distancia
- Distancia = número de saltos por Stargate necesarios

**Ejemplo:**
- Sistema A conectado a B, B a C, C a D (A→B→C→D)
- Dreadnought en A puede saltar directo a D (3 saltos de distancia) o cualquier sistema intermedio
- No puede saltar a sistema E que está conectado a D (4 saltos desde A)

**Restricciones:**
- No puede saltar a sistemas IIC 1 (núcleo corporativo, demasiado defendidos)
- No puede saltar si tiene marca criminal activa
- No puede saltar dentro del rango de jammers de salto enemigos (módulo de estación)
- Si es atacado durante preparación, el salto se cancela
- Consumo de combustible no reembolsable si se cancela

**Ventajas Estratégicas:**
- Sorprender enemigos en sistemas remotos
- Evadir bloqueos de Stargates
- Desplegar rápidamente en territorios disputados
- Evacuación de emergencia de zonas peligrosas

**Desventajas:**
- Costo elevado (50K₡ por salto)
- Cooldown largo (1 hora)
- Vulnerabilidad durante preparación
- No funciona en IIC 1 (núcleos corporativos)

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

**1. Reactor de Energía (RE) - Red de Energía:**
- **Descripción:** Energía total que la nave puede suministrar a los módulos
- **Unidad:** Megawatts (MW)
- **Uso:** Módulos activos (armas, escudos, propulsores) consumen RE
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

**Diferencia RE vs Capacitor:**
- **RE:** Límite estático de fitting (no puedes equipar más módulos si excedes RE)
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
- No puedes equipar módulos si excedes RE o CPU de la nave
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
1. **Vista de Nave:** Muestra la nave seleccionada con sus slots y recursos (RE, CPU, Capacitor)
2. **Biblioteca de Módulos:** Lista filtrable de módulos disponibles (por tier, tipo, skill)
3. **Drag & Drop:** Arrastrar módulos a slots de la nave
4. **Indicadores en Tiempo Real:**
   - Barras de RE usado / total (verde si OK, rojo si excede)
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
- Solo consumen RE y CPU (en el fitting)
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
- **Tier 1:** Cañón Automático Ligero - 25 DPS, 8 RE, 15 CPU, 20 cap/disparo
- **Tier 2:** Cañón de Riel - 40 DPS, 15 RE, 25 CPU, 35 cap/disparo (requiere Armas Proyectiles 3)
- **Tier 3:** Artillería de Neutrones - 70 DPS, 30 RE, 45 CPU, 60 cap/disparo (requiere Armas Proyectiles 4)
- **Daño:** Fuerte contra armadura (+50%)

**Armas de Energía:**
- **Tier 1:** Láser de Pulso - 22 DPS, 10 RE, 20 CPU, 25 cap/disparo
- **Tier 2:** Láser de Haz - 38 DPS, 18 RE, 35 CPU, 45 cap/disparo (requiere Armas Energía 3)
- **Tier 3:** Láser de Fase Cuántico - 65 DPS, 35 RE, 50 CPU, 70 cap/disparo (requiere Armas Energía 4)
- **Daño:** Fuerte contra escudos (+50%)

**Armas Híbridas:**
- **Tier 1:** Blaster Básico - 20 DPS, 9 RE, 18 CPU, 22 cap/disparo
- **Tier 2:** Cañón de Iones - 35 DPS, 16 RE, 30 CPU, 40 cap/disparo (requiere Armas Híbridas 3)
- **Tier 3:** Disruptor de Antimateria - 60 DPS, 32 RE, 48 CPU, 65 cap/disparo (requiere Armas Híbridas 4)
- **Daño:** Balanceado (escudos y armadura)

**Misiles:**
- **Tier 1:** Lanzamisiles Ligero - 30 DPS, 5 RE, 25 CPU, 15 cap/lanzamiento + munición
- **Tier 2:** Lanzamisiles Pesado - 55 DPS, 12 RE, 40 CPU, 30 cap/lanzamiento + munición (requiere Misiles 3)
- **Tier 3:** Torpedos de Crucero - 95 DPS, 25 RE, 60 CPU, 50 cap/lanzamiento + munición (requiere Misiles 4)
- **Daño:** Variable según munición (explosivo, cinético, EM, térmico)

### 7.5.2 Sistemas Defensivos

**Generadores de Escudos:**
- **Tier 1 Pequeño:** +400 HP escudos, 8 RE, 15 CPU, pasivo
- **Tier 1 Mediano:** +800 HP escudos, 15 RE, 25 CPU, pasivo
- **Tier 1 Grande:** +1500 HP escudos, 30 RE, 40 CPU, pasivo (requiere Escudos 2)
- **Tier 2 Pequeño:** +600 HP escudos, 10 RE, 18 CPU, pasivo (requiere Escudos 3)
- **Tier 2 Mediano:** +1200 HP escudos, 20 RE, 30 CPU, pasivo (requiere Escudos 3)
- **Tier 3 Grande:** +2500 HP escudos, 45 RE, 55 CPU, +10% resist todas (requiere Escudos 4)

**Recargadores de Escudos:**
- **Tier 1:** Regen +15 HP/tick, 12 RE, 20 CPU, 40 cap/activación, activo
- **Tier 2:** Regen +30 HP/tick, 20 RE, 35 CPU, 70 cap/activación, activo (requiere Escudos 3)
- **Tier 3:** Regen +60 HP/tick, 35 RE, 50 CPU, 120 cap/activación, activo (requiere Escudos 4)

**Placas de Armadura:**
- **Tier 1 Pequeña:** +300 HP armadura, 5 RE, 10 CPU, pasivo
- **Tier 1 Mediana:** +700 HP armadura, 10 RE, 18 CPU, pasivo
- **Tier 1 Grande:** +1300 HP armadura, 20 RE, 30 CPU, pasivo (requiere Blindaje 2)
- **Tier 2 Grande:** +2000 HP armadura, 30 RE, 40 CPU, +5% resist explosivo (requiere Blindaje 3)
- **Tier 3 Grande:** +3500 HP armadura, 50 RE, 60 CPU, +10% resist todos (requiere Blindaje 4)

**Reparadores de Armadura:**
- **Tier 1:** Repara 20 HP/tick, 15 RE, 25 CPU, 50 cap/activación, activo
- **Tier 2:** Repara 40 HP/tick, 25 RE, 40 CPU, 90 cap/activación, activo (requiere Blindaje 3)
- **Tier 3:** Repara 80 HP/tick, 40 RE, 60 CPU, 150 cap/activación, activo (requiere Blindaje 4)

**Refuerzos Estructurales:**
- **Tier 1:** +200 HP estructura, 3 RE, 8 CPU, pasivo
- **Tier 2:** +400 HP estructura, 6 RE, 15 CPU, pasivo
- **Tier 3:** +800 HP estructura, 12 RE, 25 CPU, pasivo

### 7.5.3 Sistemas de Utilidad

**Minería:**
- **Tier 1:** Láser de Minería Básico - Reduce 1 tick minería, 10 RE, 20 CPU, 30 cap/ciclo
- **Tier 2:** Láser de Minería Avanzado - Reduce 2 ticks, +15% yield, 18 RE, 35 CPU, 50 cap/ciclo (requiere Minería 3)
- **Tier 3:** Dron Minero Automático - Reduce 3 ticks, +30% yield, puede minar múltiples asteroides, 30 RE, 50 CPU, 80 cap/ciclo (requiere Minería 4, Drones 2)

**Extracción Especializada:**
- **Extractor Criogénico T1:** Para hielo Tier 1-2, 12 RE, 25 CPU, 40 cap/ciclo (requiere Extracción Criogénica 1)
- **Extractor Criogénico T2:** Para hielo Tier 2-3, reduce 1 tick, 20 RE, 40 CPU, 70 cap/ciclo (requiere Extracción Criogénica 3)
- **Extractor Criogénico T3:** Para hielo Tier 3-4, reduce 2 ticks, +20% yield, 35 RE, 60 CPU, 110 cap/ciclo (requiere Extracción Criogénica 5)

**Recolectores de Gas:**
- **Recolector de Gas T1:** Para nebulosas Tier 1-2, 8 RE, 30 CPU, 35 cap/ciclo (requiere Recolección Gas 1)
- **Recolector de Gas T2:** Para nebulosas Tier 2-3, +25% yield, 15 RE, 45 CPU, 60 cap/ciclo (requiere Recolección Gas 3)
- **Recolector de Gas T3:** Para nebulosas Tier 3-4, +50% yield, detección previa tormentas, 28 RE, 70 CPU, 100 cap/ciclo (requiere Recolección Gas 5)

**Expansores de Carga:**
- **Tier 1:** +500 m³, 3 RE, 10 CPU, pasivo
- **Tier 2:** +1000 m³, 5 RE, 18 CPU, pasivo
- **Tier 3:** +2000 m³, 10 RE, 30 CPU, pasivo

**Propulsores:**
- **Tier 1 Básico:** +15% velocidad, 8 RE, 15 CPU, 25 cap/activación (10 ticks), activo
- **Tier 2 Mejorado:** +30% velocidad, 15 RE, 25 CPU, 45 cap/activación (10 ticks), activo (requiere Navegación 2)
- **Tier 3 Avanzado:** +50% velocidad, reduce tiempo warp 20%, 25 RE, 40 CPU, 75 cap/activación (10 ticks), activo (requiere Navegación 4)
- **Motor de Salto:** Necesario para usar Stargates, 20 RE, 50 CPU, pasivo (requiere Navegación 3)

**Scanners:**
- **Scanner de Carga T1:** Detecta presencia de ítems ilegales, 40% precisión, 1 escaneo por objetivo, 10 ticks duración, 10 RE, 35 CPU, 80 cap/escaneo (requiere Escaneo de Carga 1)
- **Scanner de Carga T2:** Detecta ítems ilegales, 65% precisión, 2 escaneos por objetivo, 8 ticks duración, 18 RE, 55 CPU, 140 cap/escaneo (requiere Escaneo de Carga 3)
- **Scanner de Carga T3:** Detecta ítems ilegales + cantidad exacta, 90% precisión, 3 escaneos por objetivo, 6 ticks duración, escaneo penetrante, 30 RE, 80 CPU, 220 cap/escaneo (requiere Escaneo de Carga 5)
- **Scanner de Combate T1:** Detecta naves hostiles, 3 RE, 30 CPU, 60 cap/escaneo (requiere Rastreo 1)
- **Scanner de Anomalías T1:** Detecta sitios temporales, 5 RE, 40 CPU, 80 cap/escaneo (requiere Exploración 1)
- **Scanner Planetario T1:** Escanea planetas, calidad 5, 3 RE, 40 CPU, 100 cap/escaneo (requiere Escaneo Planetario 1)
- **Scanner Planetario T2:** Escanea planetas, calidad 10, 6 RE, 60 CPU, 150 cap/escaneo (requiere Escaneo Planetario 3)
- **Scanner Planetario T3:** Escanea planetas, calidad 15, +20% velocidad escaneo, 12 RE, 90 CPU, 220 cap/escaneo (requiere Escaneo Planetario 5)

**Mecánica de Escaneo de Carga (Jugador vs Jugador):**
- El escáner debe estar dentro del mismo sistema que el objetivo
- Proceso: Seleccionar nave objetivo → Activar Scanner de Carga → Esperar duración (6-10 ticks)
- Fórmula de detección:

```
chance_detectar = precisión_scanner - (evasión_compartimento + evasión_bloqueador + evasión_revestimiento)
chance_final = max(5%, min(95%, chance_detectar))
```

- Si detecta: Muestra lista de ítems ilegales + cantidad aproximada (T3 muestra cantidad exacta)
- Si falla: Muestra "Escaneo incompleto - no se detectaron anomalías"
- El objetivo recibe notificación "Tu nave está siendo escaneada por [piloto]"
- El objetivo puede huir durante el escaneo (cancela el proceso)

**Módulos de Sigilo:**
- **Camuflaje Básico T1:** +15% Sigilo, 10 RE, 20 CPU, 40 cap/activación (dura 5 ticks), activo (requiere Sigilo 1)
- **Camuflaje Avanzado T2:** +30% Sigilo, 18 RE, 35 CPU, 70 cap/activación (dura 8 ticks), activo (requiere Sigilo 3)
- **Cloak de Invisibilidad T3:** +60% Sigilo, invisibilidad casi total si no te mueves, 30 RE, 55 CPU, 120 cap/activación (dura 10 ticks), activo (requiere Sigilo 5, solo naves T3)

**Otros:**
- **Estabilizador de Salto T1:** Reduce fatiga de salto 15%, 5 RE, 15 CPU, pasivo
- **Reparador Remoto T1:** Repara nave aliada a distancia, 20 RE, 30 CPU, 80 cap/activación, activo (requiere Logística 2)
- **Transmisor de Energía T1:** Transfiere capacitor a nave aliada, 15 RE, 25 CPU, 60 cap/activación, activo (requiere Logística 2)
- **Amplificador de CPU T1:** +10% CPU total nave, 5 RE, 0 CPU (no consume CPU), pasivo (requiere Ingeniería 2)
- **Relé de Reactor de Energía T1:** +10% RE total nave, 0 RE, 15 CPU, pasivo (requiere Ingeniería 2)

### 7.5.4 Recetas de Fabricación de Módulos T1

Todos los módulos se fabrican en Sala de Ingeniería (ver PRD-Universe.md). Ningún módulo se fabrica con recursos crudos - todos requieren componentes intermedios.

**Regla Crítica:** La cadena de fabricación es: Recursos Crudos → Refinamiento → Componentes Intermedios → Módulos → Naves

#### Tabla de Recetas - 25 Módulos T1 Esenciales

| Módulo T1 | Componentes Requeridos | Tiempo | Skill Fabricación | Precio NPC | Volumen | Desbloqueo |
|-----------|------------------------|--------|-------------------|------------|---------|------------|
| Cañón Automático Ligero | 15 Placas de Blindaje T1 + 10 Servomotores T1 + 8 Circuitos Básicos | 8 ticks | Construcción de Naves Nivel 1 | 25,000₡ | 2 m³ | Gratis |
| Láser de Pulso | 12 Lentes Básicas + 15 Celdas de Energía T1 + 10 Circuitos Básicos | 8 ticks | Construcción de Naves Nivel 1 | 28,000₡ | 1.5 m³ | Gratis |
| Blaster Básico | 10 Superconductores T1 + 12 Circuitos Básicos + 8 Placas de Blindaje T1 | 8 ticks | Construcción de Naves Nivel 1 | 22,000₡ | 1.8 m³ | Gratis |
| Lanzamisiles Ligero | 20 Barras de Acero + 10 Servomotores T1 + 8 Procesadores T1 | 10 ticks | Construcción de Naves Nivel 1 | 30,000₡ | 3 m³ | Gratis |
| Generador de Escudos Pequeño | 15 Superconductores T1 + 20 Celdas de Energía T1 + 10 Circuitos Básicos | 6 ticks | Construcción de Naves Nivel 1 | 18,000₡ | 1 m³ | Gratis |
| Generador de Escudos Mediano | 25 Superconductores T1 + 30 Celdas de Energía T1 + 15 Condensadores | 8 ticks | Construcción de Naves Nivel 1 | 32,000₡ | 1.5 m³ | Gratis |
| Generador de Escudos Grande | 40 Superconductores T1 + 50 Celdas de Energía T1 + 25 Condensadores | 12 ticks | Construcción de Naves Nivel 1 | 65,000₡ | 2.5 m³ | 10,000₡ |
| Recargador de Escudos T1 | 20 Celdas de Energía T1 + 15 Superconductores T1 + 12 Procesadores T1 | 7 ticks | Construcción de Naves Nivel 1 | 35,000₡ | 1.2 m³ | Gratis |
| Placa de Armadura Pequeña | 30 Placas de Blindaje T1 + 10 Barras de Acero | 5 ticks | Construcción de Naves Nivel 1 | 15,000₡ | 2 m³ | Gratis |
| Placa de Armadura Mediana | 50 Placas de Blindaje T1 + 20 Barras de Acero + 10 Vigas Reforzadas | 7 ticks | Construcción de Naves Nivel 1 | 28,000₡ | 3 m³ | Gratis |
| Placa de Armadura Grande | 80 Placas de Blindaje T1 + 40 Vigas Reforzadas + 15 Barras de Acero | 10 ticks | Construcción de Naves Nivel 1 | 55,000₡ | 5 m³ | 10,000₡ |
| Reparador de Armadura T1 | 25 Placas de Blindaje T1 + 15 Servomotores T1 + 20 Celdas de Energía T1 | 8 ticks | Construcción de Naves Nivel 1 | 40,000₡ | 2 m³ | Gratis |
| Refuerzo Estructural T1 | 40 Barras de Acero + 20 Placas de Blindaje T1 | 4 ticks | Construcción de Naves Nivel 1 | 12,000₡ | 3 m³ | Gratis |
| Láser de Minería Básico | 10 Lentes Básicas + 12 Celdas de Energía T1 + 8 Servomotores T1 | 6 ticks | Construcción de Naves Nivel 1 | 25,000₡ | 1.5 m³ | Gratis |
| Extractor Criogénico T1 | 15 Actuadores Hidráulicos + 20 Celdas de Energía T1 + 10 Circuitos Básicos | 7 ticks | Construcción de Naves Nivel 1 | 30,000₡ | 2.5 m³ | Gratis |
| Recolector de Gas T1 | 12 Baterías Iónicas + 10 Actuadores Hidráulicos + 8 Circuitos Básicos | 6 ticks | Construcción de Naves Nivel 1 | 24,000₡ | 2 m³ | Gratis |
| Expansor de Carga T1 | 25 Barras de Acero + 15 Vigas Reforzadas | 5 ticks | Construcción de Naves Nivel 1 | 15,000₡ | 4 m³ | Gratis |
| Propulsor Básico T1 | 18 Sistemas de Propulsión T1 + 25 Celdas de Energía T1 + 10 Servomotores T1 | 8 ticks | Construcción de Naves Nivel 1 | 35,000₡ | 1.8 m³ | Gratis |
| Motor de Salto | 30 Sistemas de Propulsión T1 + 40 Celdas de Energía T1 + 20 Procesadores T1 | 12 ticks | Construcción de Naves Nivel 1 | 75,000₡ | 3 m³ | 15,000₡ |
| Scanner de Carga T1 | 15 Lentes Básicas + 20 Procesadores T1 + 12 Circuitos Básicos | 7 ticks | Construcción de Naves Nivel 1 | 40,000₡ | 1 m³ | Gratis |
| Scanner de Combate T1 | 10 Lentes Básicas + 15 Procesadores T1 + 8 Circuitos Básicos | 5 ticks | Construcción de Naves Nivel 1 | 28,000₡ | 0.8 m³ | Gratis |
| Scanner de Anomalías T1 | 12 Sistemas Ópticos T1 + 18 Procesadores T1 + 10 Circuitos Básicos | 6 ticks | Construcción de Naves Nivel 1 | 32,000₡ | 1 m³ | Gratis |
| Scanner Planetario T1 | 15 Sistemas Ópticos T1 + 20 Procesadores T1 + 12 Condensadores | 8 ticks | Construcción de Naves Nivel 1 | 45,000₡ | 1.2 m³ | Gratis |
| Camuflaje Básico T1 | 12 Procesadores T1 + 15 Superconductores T1 + 20 Celdas de Energía T1 | 9 ticks | Construcción de Naves Nivel 1 | 50,000₡ | 1.5 m³ | 10,000₡ |
| Amplificador de CPU T1 | 25 Procesadores T1 + 20 Microconductores + 15 Circuitos Básicos | 7 ticks | Construcción de Naves Nivel 1 | 38,000₡ | 0.5 m³ | 10,000₡ |

**Notas Importantes:**
- **Módulo Requerido:** Sala de Ingeniería Nivel 1+ (ver PRD-Universe.md sección 6.2.7)
- **Skill "Construcción de Naves":** Skill nueva que se agrega a PRD-GameDesign.md
  - Nivel 1: Permite fabricar módulos y naves T1
  - Nivel 2: Reduce tiempo fabricación 5%
  - Nivel 3: Permite fabricar naves T2
  - Nivel 4: Reduce tiempo fabricación 10% adicional
  - Nivel 5: Permite fabricar módulos y naves T3
- **Tiempo de Fabricación:** Por unidad individual, producción en masa disponible con Sala de Ingeniería Nivel 3+
- **Desbloqueo de Recetas:**
  - Módulos básicos (marcados "Gratis"): Desbloqueados por defecto
  - Módulos avanzados: Requieren pago de créditos (10K-15K₡)
  - Módulos T2-T3: Requieren Chips de Diseño o descifrado en Laboratorio
- **Volumen:** Importante para planificar transporte desde estación de fabricación
- **Precios NPC:** Valor base de venta a NPCs, el mercado de jugadores fluctúa ±200%
- **Árbol de Dependencias:** Cada módulo muestra sus componentes, que a su vez requieren recursos procesados
  - Ejemplo: Cañón Automático → Placas de Blindaje T1 → (Ferrita + Titanita) Refinadas → Ferrita + Titanita Crudas

**Ejemplo de Cadena Completa:**

```
LÁSER DE PULSO (Módulo Final)
├─> 12× Lentes Básicas (Componente)
│   ├─> 25 Silicatos Refinados (Recurso Procesado)
│   │   └─> 33 Silicatos Crudos (Recurso Crudo, ratio 0.75)
│   └─> 10 Agua Destilada (Recurso Procesado)
│       └─> 13 Agua Sucia (Recurso Crudo, ratio 0.75)
├─> 15× Celdas de Energía T1 (Componente)
│   ├─> 30 Hidrógeno Comprimido (Recurso Procesado)
│   │   └─> 40 Hidrógeno Crudo (Recurso Crudo, ratio 0.75)
│   └─> 15 Helio Líquido (Recurso Procesado)
│       └─> 20 Helio Crudo (Recurso Crudo, ratio 0.75)
└─> 10× Circuitos Básicos (Componente)
    ├─> 20 Cobre Estelar (Recurso Procesado)
    │   └─> 27 Cobre Crudo (Recurso Crudo, ratio 0.75)
    └─> 10 Silicatos Refinados (Recurso Procesado)
        └─> 13 Silicatos Crudos (Recurso Crudo, ratio 0.75)
```

Este árbol de dependencias es visible en la GUI de inspección de ítems (ver PRD-Interface.md).

### 7.6 Recetas de Fabricación de Naves Fragata T1

Todas las naves se fabrican en Astillero de estaciones (ver PRD-Universe.md sección 6.2.6). Como con los módulos, ninguna nave se fabrica directamente con recursos crudos.

**Regla Crítica:** Recursos Crudos → Refinamiento → Componentes Intermedios → Módulos/Submódulos → Naves

#### 7.6.1 Las 5 Fragatas T1 Especializadas

Las fragatas T1 son las naves de entrada al juego. Cada una está especializada en un rol específico.

| Nave Fragata T1 | Especialización | Componentes Requeridos | Tiempo | Skill Fabricación | Precio NPC | Volumen | Desbloqueo |
|-----------------|-----------------|------------------------|--------|-------------------|------------|---------|------------|
| Excavador MK-I | Minería Industrial | 200 Placas de Blindaje T1 + 150 Barras de Acero + 100 Sistemas de Propulsión T1 + 80 Celdas de Energía T1 + 60 Procesadores T1 + 40 Actuadores Hidráulicos | 48 ticks | Construcción de Naves Nivel 1 | 800,000₡ | 25,000 m³ | Gratis |
| Depredador | Combate PvP/PvE | 250 Placas de Blindaje T1 + 120 Barras de Acero + 150 Superconductores T1 + 100 Celdas de Energía T1 + 80 Servomotores T1 + 60 Procesadores T1 | 52 ticks | Construcción de Naves Nivel 1 | 900,000₡ | 22,000 m³ | Gratis |
| Explorador Vaxav | Exploración y Escaneo | 180 Placas de Blindaje T1 + 100 Barras de Acero + 120 Sistemas de Propulsión T1 + 150 Sistemas Ópticos T1 + 100 Procesadores T1 + 80 Lentes Básicas | 50 ticks | Construcción de Naves Nivel 1 | 850,000₡ | 20,000 m³ | Gratis |
| Mercante Rápido | Transporte y Comercio | 220 Barras de Acero + 180 Vigas Reforzadas + 100 Sistemas de Propulsión T1 + 80 Celdas de Energía T1 + 60 Procesadores T1 + 40 Superconductores T1 | 46 ticks | Construcción de Naves Nivel 1 | 750,000₡ | 35,000 m³ | Gratis |
| Vanguardia | Multi-rol Equilibrada | 200 Placas de Blindaje T1 + 130 Barras de Acero + 120 Sistemas de Propulsión T1 + 100 Celdas de Energía T1 + 80 Superconductores T1 + 70 Procesadores T1 | 50 ticks | Construcción de Naves Nivel 1 | 820,000₡ | 23,000 m³ | Gratis |

#### 7.6.2 Especificaciones Completas de las Fragatas T1

**1. Excavador MK-I (Minera)**

```json
{
  "nombre": "Excavador MK-I",
  "clase": "Fragata",
  "tipo": "Minera",
  "tier": 1,
  "escudos": 500,
  "armadura": 800,
  "estructura": 600,
  "carga": 5000,
  "velocidad": 15,
  "reactor_energia": 50,
  "cpu": 200,
  "capacitor": 500,
  "capacitor_regen": 25,
  "slots_ofensivos": 1,
  "slots_defensivos": 2,
  "slots_utilidad": 3,
  "bonos": {
    "mineria_tick_reduction": 0.15,
    "carga_minerales": 1.25
  },
  "requerimientos": {
    "pilotaje_fragatas": 1,
    "mineria": 1
  }
}
```

**2. Depredador (Combate)**

```json
{
  "nombre": "Depredador",
  "clase": "Fragata",
  "tipo": "Combate",
  "tier": 1,
  "escudos": 800,
  "armadura": 600,
  "estructura": 500,
  "carga": 200,
  "velocidad": 20,
  "reactor_energia": 60,
  "cpu": 220,
  "capacitor": 600,
  "capacitor_regen": 30,
  "slots_ofensivos": 3,
  "slots_defensivos": 2,
  "slots_utilidad": 2,
  "bonos": {
    "danio_proyectiles": 1.10,
    "rastreo": 1.15
  },
  "requerimientos": {
    "pilotaje_fragatas": 2,
    "armas_proyectiles": 1
  }
}
```

**3. Explorador Vaxav (Exploración)**

```json
{
  "nombre": "Explorador Vaxav",
  "clase": "Fragata",
  "tipo": "Exploración",
  "tier": 1,
  "escudos": 600,
  "armadura": 500,
  "estructura": 550,
  "carga": 800,
  "velocidad": 22,
  "reactor_energia": 55,
  "cpu": 250,
  "capacitor": 550,
  "capacitor_regen": 28,
  "slots_ofensivos": 1,
  "slots_defensivos": 2,
  "slots_utilidad": 4,
  "bonos": {
    "escaneo_precision": 1.25,
    "velocidad_warp": 1.15
  },
  "requerimientos": {
    "pilotaje_fragatas": 2,
    "exploracion": 1
  }
}
```

**4. Mercante Rápido (Transporte)**

```json
{
  "nombre": "Mercante Rápido",
  "clase": "Fragata",
  "tipo": "Transporte",
  "tier": 1,
  "escudos": 400,
  "armadura": 700,
  "estructura": 650,
  "carga": 10000,
  "velocidad": 18,
  "reactor_energia": 45,
  "cpu": 180,
  "capacitor": 480,
  "capacitor_regen": 22,
  "slots_ofensivos": 0,
  "slots_defensivos": 3,
  "slots_utilidad": 3,
  "bonos": {
    "carga_bonus": 1.50,
    "velocidad_alineamiento": 1.20
  },
  "requerimientos": {
    "pilotaje_fragatas": 1
  }
}
```

**5. Vanguardia (Multi-rol)**

```json
{
  "nombre": "Vanguardia",
  "clase": "Fragata",
  "tipo": "Multi-rol",
  "tier": 1,
  "escudos": 700,
  "armadura": 650,
  "estructura": 570,
  "carga": 1500,
  "velocidad": 18,
  "reactor_energia": 55,
  "cpu": 210,
  "capacitor": 550,
  "capacitor_regen": 26,
  "slots_ofensivos": 2,
  "slots_defensivos": 3,
  "slots_utilidad": 2,
  "bonos": {
    "versatilidad": 1.05
  },
  "requerimientos": {
    "pilotaje_fragatas": 1
  }
}
```

**Notas Importantes:**
- **Módulo Requerido:** Astillero Nivel 1+ (ver PRD-Universe.md sección 6.2.6)
- **Skill "Construcción de Naves":** Requerida para fabricar (ver PRD-GameDesign.md)
  - Nivel 1: Permite fabricar naves T1
  - Nivel 3: Permite fabricar naves T2
  - Nivel 5: Permite fabricar naves T3
- **Tiempo de Fabricación:**
  - Base: 46-52 ticks por fragata T1
  - Reducible con skill "Producción en Masa" (-5% a -25%)
  - Reducible con Astillero de nivel superior (+15% a +75% velocidad)
- **Desbloqueo de Recetas:**
  - Todas las fragatas T1: Desbloqueadas por defecto
  - Fragatas T2: Requieren pago de créditos (500K₡) o Chip de Diseño
  - Fragatas T3: Requieren Chips de Diseño exclusivamente (no se pueden comprar)
- **Volumen:** El volumen ensamblado, importante para determinar qué nave puede transportar la base de estación
- **Precios NPC:** Valor de venta a NPCs, mercado de jugadores puede variar significativamente
- **Bonos de Nave:**
  - Excavador: +15% velocidad minería, +25% capacidad de carga de minerales
  - Depredador: +10% daño proyectiles, +15% tracking
  - Explorador: +25% precisión escaneo, +15% velocidad warp
  - Mercante: +50% carga total, +20% velocidad alineamiento
  - Vanguardia: +5% todas las stats (versátil pero sin especialización)

**Ejemplo de Árbol de Dependencias - Excavador MK-I:**

```
EXCAVADOR MK-I (Nave Final)
├─> 200× Placas de Blindaje T1 (Componente)
│   ├─> 60 Ferrita Refinada × 200 = 12,000 unidades
│   │   └─> 16,000 Ferrita Cruda (ratio 0.75)
│   └─> 20 Titanita Refinada × 200 = 4,000 unidades
│       └─> 5,714 Titanita Cruda (ratio 0.70)
├─> 150× Barras de Acero (Componente)
│   ├─> 50 Ferrita Refinada × 150 = 7,500 unidades
│   └─> 10 Silicatos Refinados × 150 = 1,500 unidades
├─> 100× Sistemas de Propulsión T1 (Componente)
│   ├─> 40 Titanita Refinada × 100 = 4,000 unidades
│   └─> 25 Servomotores T1 × 100 = 2,500 unidades (que a su vez requieren Ferrita + Cobre)
├─> 80× Celdas de Energía T1 (Componente)
│   ├─> 30 Hidrógeno Comprimido × 80 = 2,400 unidades
│   └─> 15 Helio Líquido × 80 = 1,200 unidades
├─> 60× Procesadores T1 (Componente)
│   └─> (Cobre Estelar + Silicatos Refinados)
└─> 40× Actuadores Hidráulicos (Componente)
    └─> (Ferrita Refinada + Agua Destilada)
```

**Total aproximado de recursos crudos para 1 Excavador MK-I:**
- ~40,000 unidades de recursos metálicos crudos
- ~8,000 unidades de recursos gaseosos/volátiles crudos
- ~3,000 unidades de recursos orgánicos crudos
- 48 ticks de fabricación + tiempo de componentes (~200 ticks totales incluyendo refinamiento y fabricación de componentes)

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
- Con cápsula: puede huir en pod (nave ligera indefensa)
- Si el pod también es destruido: el piloto muere y respawnea en último clon

**Sistema de Clones (Estilo EVE):**

El sistema de clones en VAXAV funciona similar a EVE Online, permitiendo múltiples clones con implantes independientes.

**Mecánica:**
- Los clones se crean en Laboratorios de estaciones (ver [PRD-Universe.md](./PRD-Universe.md#6.2.3-laboratorio))
- Puedes tener múltiples clones activos en diferentes estaciones (límite según nivel de Laboratorio + skill)
- Cada clon mantiene sus propios implantes (máximo 5 implantes por clon)
- Puedes "saltar" entre clones usando la acción "Clone Jump"
- Al morir: **NO pierdes skills ni experiencia**, respawneas en el clon activo más reciente
- El clon destruido y sus implantes se pierden (a menos que tengas seguro)

**Crear un Clon:**
1. Visitar un Laboratorio (Nivel 1+)
2. Seleccionar "Crear Nuevo Clon"
3. Costo: 50,000₡
4. Tiempo: 12 ticks
5. El clon queda almacenado en esa estación

**Saltar entre Clones (Clone Jump):**
- Requiere estar atracado en un Laboratorio (Nivel 2+)
- Tu consciencia se transfiere instantáneamente al clon destino
- El clon anterior queda en su estación con todos sus implantes
- **Cooldown:** 144 ticks (24 horas), reducido a 72 ticks (12 horas) con Laboratorio Nivel 5
- **Skill:** Requiere "Gestión de Clones Avanzada" para aumentar límite de clones

**Límites de Clones:**
- Laboratorio Nivel 1: 1 clon activo
- Laboratorio Nivel 2: 3 clones activos
- Laboratorio Nivel 3: 5 clones activos
- Laboratorio Nivel 4: 10 clones activos
- Laboratorio Nivel 5: Clones ilimitados
- **Skill "Gestión de Clones Avanzada":** +2 clones máximos por nivel

**Ejemplo de Uso:**
- Piloto tiene clones en: Estación A (minero, implantes de minería), Estación B (comercial), Estación C (PvP, implantes de combate)
- Clon activo: Estación A
- Piloto termina minería → Salta a Clon C (cooldown 144 ticks)
- Clon A queda en Estación A con sus implantes de minería intactos
- Piloto ahora está en Clon C con implantes de combate
- Piloto muere en PvP → Respawnea en Clon A (clon C y sus implantes destruidos)

**Pérdidas al Morir:**
- Nave destruida (se convierte en Wreck saqueab le)
- Módulos equipados (% quedan en Wreck)
- Carga de la nave (% queda en Wreck)
- Clon activo destruido con todos sus implantes (a menos que tengas seguro de implantes)
- **NO SE PIERDEN:** Skills, experiencia, items en estaciones, créditos, otros clones en otras estaciones

**Ventaja sobre EVE:**
- Morir es menos punitivo (no pierdes progreso de skills)
- Permite juego más agresivo y experimental
- Clones especializados como herramienta estratégica (clones con diferentes implantes para diferentes actividades)

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
- Nave flagged como criminal en sistemas IIC 1-2
- Albatross ataca a la vista en IIC 1-2 (sin advertencia)
- NO REVERSIBLE (no puede deshacerse)
- Standing permanente -50 con Confederación si detectada

**Costo:** 200,000₡

**Implementación Técnica:**
- Modificación permanente en tabla `illegal_ship_modifications`
- Nave invisible en sistema de detección de naves
- Albatross tiene script especial: si `ship.has_no_transponder AND system.iic <= 2 THEN attack_immediately()`

#### 9.2.2 Amplificador Ilegal de RE/CPU

**Descripción:** Bypass de los limitadores de fábrica en reactor de energía y CPU.

**Beneficios:**
- +25% Reactor de Energía total
- +25% CPU total
- Permite fitting de módulos más poderosos

**Consecuencias:**
- Nave ilegal, Albatross ataca en IIC 1-2
- Advertencia de 30 segundos antes del ataque (tiempo para huir)
- Detectable por escaneos profundos (20% chance por escaneo)
- Standing -10 con Confederación si detectada

**Costo:** 350,000₡

**Reversibilidad:** SÍ (costo 100,000₡ en cualquier estación con Sala de Ingeniería)

**Implementación Técnica:**
- Modificador en stats de nave: `ship.reactor_energia *= 1.25; ship.cpu *= 1.25`
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
- Albatross ataca en IIC 1-2 (advertencia 10 segundos)
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

**Sistemas IIC 1-2 (Alta Seguridad):**

1. **Entrada al Sistema:**
   - Albatross escanea todas las naves que entran
   - Detección automática de naves sin transponder (100% detección)
   - Detección probabilística de otras modificaciones:
     - Amplificador RE/CPU: 20% por escaneo
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

**Sistemas IIC 3 (Frontera Disputada):**
- Albatross solo en stargates
- Escaneo solo al usar stargate (1 vez)
- 50% menos probabilidad de detección

**Sistemas IIC 4-5 (Tierra de Nadie / Espacio Profundo):**
- Sin Albatross
- Modificaciones ilegales sin riesgo

### 9.4 Economía de Modificaciones Ilegales

**ROI (Return on Investment):**

| Modificación | Costo | Beneficio | ROI Estimado | Riesgo |
|--------------|-------|-----------|--------------|--------|
| Eliminar Transponder | 200K₡ | Stealth total | Alto (PvP, piratería) | Extremo |
| Amplificador RE/CPU | 350K₡ | +25% fitting | Medio (fittings T3) | Alto |
| Reactor Black Hole | 1M₡ | Cap infinito | Bajo (riesgo explosión) | Muy Alto |
| Sistema Puntería | 450K₡ | +40% tracking | Alto (PvP) | Alto |

**Casos de Uso Comunes:**

1. **Piratería en Espacio Profundo:**
   - Eliminar Transponder + Sistema Puntería
   - Costo: 650K₡
   - Beneficio: Emboscadas perfectas, alto damage
   - Riesgo: Solo si entra a Territorio Estable+

2. **Minería en Frontera Disputada:**
   - Amplificador RE/CPU
   - Costo: 350K₡
   - Beneficio: Fitting con más láseres de minería + escudos potentes
   - Riesgo: Evitar Territorio Estable+, minería en Frontera/Tierra de Nadie

3. **PvP Extremo (Locura):**
   - Reactor Black Hole + Sistema Puntería + Amplificador RE/CPU
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
- **Pilotos Lawful:** Operan en IIC 1-2 sin preocupaciones, sacrifican poder
- **Pilotos Outlaw:** Operan en IIC 4-5 con naves modificadas poderosas, evitan sistemas seguros

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
