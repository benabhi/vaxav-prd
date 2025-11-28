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

### 7.3 Estados de Nave

- **Atracada:** En hangar de estación
- **Orbitando:** Alrededor de estación/planeta/luna
- **En tránsito:** Viajando entre ubicaciones
- **En combate:** Participando en batalla
- **Minando:** Extrayendo recursos
- **Destruida:** Wreck recuperable

### 7.4 Módulos de Nave

### 7.4.1 Sistemas Ofensivos

**Armas de Proyectiles:**
- Cañón Automático Ligero (T1)
- Cañón de Riel (T2)
- Artillería Pesada (T3)
- **Daño:** Fuerte contra armadura

**Armas de Energía:**
- Láser de Pulso (T1)
- Láser de Haz (T2)
- Láser de Fase (T3)
- **Daño:** Fuerte contra escudos

**Armas Híbridas:**
- Blasters (T1)
- Cañones de Iones (T2)
- **Daño:** Balanceado (escudos y armadura)

**Misiles:**
- Lanzamisiles Ligero (T1)
- Lanzamisiles Pesado (T2)
- Torpedos (T3)
- **Daño:** Variable según munición

### 7.4.2 Sistemas Defensivos

**Escudos:**
- Generador de Escudos Pequeño
- Generador de Escudos Mediano
- Generador de Escudos Grande
- Amplificador de Escudos
- Recargador de Escudos

**Armadura:**
- Placas de Armadura (Pequeña/Mediana/Grande)
- Reparador de Armadura
- Revestimiento Reactivo

**Estructura:**
- Refuerzos Estructurales
- Reparador de Casco

### 7.4.3 Sistemas de Utilidad

**Minería:**
- Láser de Minería Básico
- Láser de Minería Avanzado
- Dron Minero

**Carga:**
- Expansor de Carga I/II/III
- Optimizador de Carga

**Propulsión:**
- Propulsor Básico
- Propulsor Mejorado
- Motor de Salto (para Stargates)

**Escaneo:**
- Scanner de Carga
- Scanner de Combate
- Scanner de Anomalías

**Sigilo:**
- Camuflaje Básico
- Silenciador de Firma

**Otros:**
- Estabilizador de Salto
- Reparador Remoto
- Transmisor de Energía

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
