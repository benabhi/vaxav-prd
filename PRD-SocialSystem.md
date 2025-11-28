# Sistema Social y Estado del Piloto

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 13. Sistema Social y Estado del Piloto

### 13.1 Atributos del Piloto

El piloto tiene atributos que afectan su rendimiento en las acciones y deben ser gestionados activamente.

### 13.1.1 Energía (0-100)

Combina fatiga física y mental del piloto.

**Efectos en el juego:**

```
100-80:  Rendimiento óptimo (+5% a todas las acciones)
79-60:   Rendimiento normal (sin modificadores)
59-40:   Cansancio (-10% eficiencia, -5% exp ganada)
39-20:   Agotamiento (-25% eficiencia, -15% exp ganada)
19-0:    Exhausto (-50% eficiencia, -30% exp ganada, riesgo de errores)
```

**Cómo se consume:**
- Cada acción de tick consume energía (1-5 puntos según intensidad)
- Minería: -2 energía por tick
- Combate: -4 energía por tick
- Pilotaje: -1 energía por tick
- Fabricación: -2 energía por tick
- Navegación simple: -1 energía cada 10 ticks

**Cómo se recupera:**
- **Descansar en Habitáculos:** +20 energía por tick (requiere estar en estación)
- **Dormir (offline 48 ticks / ~8 horas):** Recuperación completa a 100
- **Consumir estimulantes:** +30 energía instantánea (tiene cooldown y efectos secundarios)
- **Pasivo (offline):** +1 energía cada 2 ticks (equivalente a +3 energía/hora con tick de 10 min)

**Mecánica anti-grinding:**
- Si la energía llega a 0, el piloto queda "inconsciente" y se teletransporta a la última estación
- Cooldown de 6 ticks (~1 hora con tick de 10 min) antes de poder volver a jugar
- Penalización: -10% energía máxima por 144 ticks (~24h) (recuperable descansando)

### 13.1.2 Nutrición (0-100)

Representa alimentación e hidratación.

**Efectos en el juego:**

```
100-70:  Bien nutrido (+3% regeneración de energía)
69-40:   Nutrición normal (sin modificadores)
39-20:   Hambriento (-5% energía máxima)
19-0:    Desnutrido (-15% energía máxima, -10% eficiencia)
```

**Cómo se consume:**
- Disminuye 1 punto cada 6 ticks (~1 hora con tick de 10 min)
- Acciones intensas (combate) consumen +1 adicional cada 6 ticks de combate

**Cómo se recupera:**
- **Comer en Habitáculos:** +30 nutrición (consume "Raciones Alimenticias" del inventario)
- **Restaurantes de estación:** +50 nutrición (cuesta créditos, disponible en estaciones grandes)
- **Raciones de emergencia:** +15 nutrición (item consumible, se puede llevar en la nave)

**Items de comida:**
- Raciones Básicas (100₡): +30 nutrición
- Comida de Lujo (500₡): +50 nutrición + buff temporal (+5% exp por 12 ticks / ~2 horas)
- Raciones de Emergencia (50₡): +15 nutrición (stackeable, para viajes largos)

### 13.1.3 Moral (0-100)

Estado anímico y psicológico del piloto.

**Efectos en el juego:**

```
100-80:  Excelente moral (+10% exp ganada, +5% eficiencia social)
79-60:   Moral normal (sin modificadores)
59-40:   Moral baja (-5% exp ganada)
39-20:   Deprimido (-15% exp ganada, -10% relaciones sociales)
19-0:    Desesperado (-25% exp ganada, riesgo de abandonar corporación)
```

**Cómo se consume:**
- Morir en combate: -20 moral
- Perder nave cara: -15 moral
- Perder dinero en mercado: -5 moral
- Estar solo (sin interacciones sociales) por 432+ ticks (~3 días): -2 moral cada 144 ticks (cada día)
- Trabajar demasiado (energía <30 por mucho tiempo): -1 moral cada 6 ticks (~1 hora)

**Cómo se recupera:**
- **Socializar con otros pilotos:** +5 moral (máx 1 vez cada 144 ticks / ~1 día por piloto)
- **Completar misiones exitosamente:** +3 moral
- **Ganar combates PvP:** +10 moral
- **Ganar dinero en mercado:** +2 moral por transacción exitosa
- **Actividades recreativas en Habitáculos:** +5 moral (1 vez cada 144 ticks / ~1 día)
- **Estar en corporación activa:** +2 moral cada 144 ticks (~1 día) pasivo
- **Tener amigos (relaciones >50):** +1 moral cada 144 ticks (~1 día) por amigo (máx 5 amigos)

### 13.1.4 Estrés Espacial (0-100)

Presión psicológica de estar en el espacio. **Menor es mejor**.

**Efectos en el juego:**

```
0-20:    Tranquilo (sin efectos)
21-40:   Tenso (-3% precisión en combate)
41-60:   Estresado (-7% precisión, -5% eficiencia minería)
61-80:   Muy estresado (-15% precisión, -10% eficiencia, -5% moral cada 144 ticks)
81-100:  Crisis nerviosa (-30% a todo, riesgo de error crítico)
```

**Cómo se acumula:**
- Estar en espacio (no en estación): +1 estrés cada 6 ticks (~1 hora)
- Combate: +5 estrés por combate
- Viajar solo en sistemas peligrosos: +3 estrés cada 6 ticks (~1 hora)
- Estar en nave dañada (<30% estructura): +2 estrés cada 6 ticks (~1 hora)
- Eventos traumáticos (casi morir): +20 estrés

**Cómo se reduce:**
- **Estar atracado en estación:** -5 estrés cada 6 ticks (~1 hora) pasivo
- **Descansar en Habitáculos:** -10 estrés por tick de descanso
- **Terapia psicológica (NPC médico):** -30 estrés (cuesta 5,000₡)
- **Viajar en flota con amigos:** -2 estrés cada 6 ticks (~1 hora) (en lugar de +1 solo)
- **Tiempo offline:** -3 estrés cada 6 ticks (~1 hora) desconectado

### 13.2 Sistema de Relaciones Sociales

Inspirado en Popmundo, los pilotos pueden formar relaciones con otros jugadores y NPCs.

### 13.2.1 Niveles de Relación (0-100)

**Escala:**

```
0-10:    Desconocido
11-25:   Conocido
26-50:   Camarada
51-75:   Amigo
76-90:   Amigo cercano
91-100:  Mejor amigo / Hermano de batalla
```

**Beneficios por nivel:**

```
Conocido (11+):
  - Puede enviar mensajes privados
  - Aparece en lista de contactos

Camarada (26+):
  - +2% eficiencia cuando trabajan juntos
  - Pueden compartir ubicación en tiempo real
  - Descuento 5% en trades entre ustedes

Amigo (51+):
  - +5% eficiencia cuando trabajan juntos
  - Pueden compartir hangares corporativos
  - +5 moral cuando están online simultáneamente
  - Descuento 10% en trades

Amigo cercano (76+):
  - +10% eficiencia trabajando juntos
  - Pueden prestarse naves
  - Notificación cuando el amigo está en peligro
  - +10 moral cuando están online
  - Descuento 15% en trades

Mejor amigo (91+):
  - +15% eficiencia trabajando juntos
  - Compartir skills (buff temporal del skill del amigo)
  - Respawn prioritario cerca del amigo si muere
  - +15 moral cuando están online
  - Descuento 20% en trades
```

### 13.2.2 Acciones Sociales

**Formas de aumentar relación:**

1. **Pasar tiempo juntos:**
    - Minar juntos en la misma ubicación: +2 relación cada 6 ticks (~1 hora)
    - Combatir en la misma flota: +5 relación/combate
    - Misiones cooperativas: +10 relación al completar
    - Simplemente estar en la misma estación: +1 relación cada 6 ticks (~1 hora)
2. **Socializar:**
    - Chatear (sistema de chat): +1 relación/cada 10 mensajes
    - Invitar a bebidas en Habitáculos: +5 relación (cuesta créditos)
    - Compartir comida: +3 relación
    - Regalar items: +1 relación por cada 1000₡ de valor
3. **Ayudarse mutuamente:**
    - Rescatar al otro en combate: +15 relación
    - Prestarle créditos: +10 relación
    - Compartir información valiosa (ubicación de recursos): +8 relación
    - Reparar su nave: +5 relación
4. **Eventos especiales:**
    - Sobrevivir juntos a combate difícil: +20 relación
    - Completar misión épica juntos: +25 relación
    - Defender la estación corporativa juntos: +30 relación

**Formas de disminuir relación:**
- Atacar al otro: -50 relación
- Robar del hangar compartido: -30 relación
- Traicionar en combate: -40 relación
- No devolver préstamo: -20 relación
- Insultar en chat: -5 relación
- Dejar morir en combate pudiendo ayudar: -15 relación

### 13.2.3 Sistema de Reputación Personal

Además de relaciones individuales, cada piloto tiene una reputación general.

**Atributos de Reputación:**

1. **Honorabilidad (0-100):**
    - Sube: Cumplir contratos, devolver préstamos, ayudar a otros
    - Baja: Romper contratos, traicionar, robar
    - **Efecto:** Afecta costo de seguros, intereses de préstamos, acceso a misiones
2. **Fiabilidad en Combate (0-100):**
    - Sube: Ganar combates, rescatar aliados, defender estaciones
    - Baja: Huir de combates, abandonar flota
    - **Efecto:** Afecta invitaciones a flotas PvP, acceso a misiones de combate
3. **Reputación Comercial (0-100):**
    - Sube: Completar contratos de transporte, comercio exitoso
    - Baja: Cancelar contratos, fraude
    - **Efecto:** Afecta comisiones de mercado, acceso a contratos premium

### 13.3 Actividades Recreativas

Para recuperar moral, energía y reducir estrés.

**En Habitáculos de estaciones:**

1. **Descansar (pasivo):**
    - +20 energía/tick
    - -10 estrés/tick
    - Gratis
2. **Dormir (programado):**
    - Requiere: Piloto debe estar offline mínimo 36 ticks (~6h con tick de 10 min)
    - Al volver: Energía al 100%, estrés reducido a la mitad
    - +5 moral
3. **Socializar en Sala Común:**
    - Requiere: Estar en la misma estación que otros pilotos
    - +5 moral
    - +2 relación con pilotos presentes
    - Costo: 500₡ (consumiciones)
    - Cooldown: 1 vez cada 144 ticks (~1 día)
4. **Entretenimiento:**
    - Ver holofilms: +3 moral, -5 estrés (500₡)
    - Jugar juegos VR: +5 moral, -3 estrés (1000₡)
    - Leer noticias galácticas: +2 moral, +información del universo (gratis)
5. **Ejercicio físico:**
    - Gimnasio: +5 energía máxima por 144 ticks (~24h) (1000₡)
    - Requiere: 6 ticks (~1 hora) de cooldown
6. **Meditación:**
    - -20 estrés
    - +10 moral
    - Gratis
    - Cooldown: 72 ticks (~12 horas)

### 13.4 Visualización en la Interfaz

**Panel de Estado del Piloto (siempre visible):**

```
╔═══════════════════════════════════════════════════════════╗
║ JOHN DOE                                    ₡ 250,450     ║
╠═══════════════════════════════════════════════════════════╣
║ ⚡ Energía:    ████████░░  85/100                         ║
║ 🍖 Nutrición:  ██████░░░░  60/100  [!] Comer pronto      ║
║ 😊 Moral:      ████████░░  82/100                         ║
║ 💭 Estrés:     ██░░░░░░░░  15/100  Tranquilo             ║
╚═══════════════════════════════════════════════════════════╝
```

**Vista Detallada (`/pilot/status`):**

```
╔═══════════════════════════════════════════════════════════╗
║ ESTADO DEL PILOTO                                         ║
╠═══════════════════════════════════════════════════════════╣

ATRIBUTOS FÍSICOS Y MENTALES
┌───────────────────────────────────────────────────────────┐
│ ⚡ ENERGÍA:        85/100  ████████░░                     │
│    Estado: Descansado                                     │
│    Modificador: +5% eficiencia                            │
│    Próxima comida recomendada: En 4 horas                │
│                                                           │
│ 🍖 NUTRICIÓN:      60/100  ██████░░░░                     │
│    Estado: Nutrición normal                               │
│    Última comida: Hace 3 horas                            │
│    [Comer Ahora]                                          │
│                                                           │
│ 😊 MORAL:          82/100  ████████░░                     │
│    Estado: Excelente moral                                │
│    Modificador: +10% exp ganada                           │
│    Factores positivos:                                    │
│      + Corporación activa (+2/día)                        │
│      + 3 amigos online (+3 moral)                         │
│      + Victoria reciente (+10)                            │
│                                                           │
│ 💭 ESTRÉS:         15/100  ██░░░░░░░░                     │
│    Estado: Tranquilo                                      │
│    Tiempo en estación: 2 horas (-10 estrés)              │
│    [Meditar] [Terapia]                                    │
└───────────────────────────────────────────────────────────┘

REPUTACIÓN PERSONAL
┌───────────────────────────────────────────────────────────┐
│ 🏅 Honorabilidad:       ████████░░  78/100  (Honorable)  │
│ ⚔️  Fiabilidad Combate:  ██████░░░░  65/100  (Confiable) │
│ 💼 Reputación Comercial: ███████░░░  72/100  (Buen trader)│
└───────────────────────────────────────────────────────────┘

AMISTADES (Top 5)
┌────────────────────┬──────────────┬────────────┬─────────┐
│ Piloto             │ Relación     │ Estado     │ Acciones│
├────────────────────┼──────────────┼────────────┼─────────┤
│ Marcus Steel       │ ████████░░ 88│ ⚫ Online   │ [Chat]  │
│                    │ Amigo cercano│            │ [Flota] │
│ Jane Smith         │ ███████░░░ 76│ ⚫ Online   │ [Chat]  │
│                    │ Amigo cercano│            │ [Flota] │
│ Bob Johnson        │ █████░░░░░ 52│ ⚪ Offline  │ [Msg]   │
│                    │ Amigo        │            │         │
└────────────────────┴──────────────┴────────────┴─────────┘

ACTIVIDADES DISPONIBLES
  [Descansar] [Comer] [Socializar] [Entretenimiento]
  [Meditación] [Ejercicio] [Ver Amigos]

╚═══════════════════════════════════════════════════════════╝
```

### 13.5 Efectos en Gameplay

**Ejemplo de cálculo de acción con todos los modificadores:**

```
Acción: Minar Tritanio

Base ticks requeridos: 10
Skill bonus (Minería Lvl 3): ×0.85 = 8.5 ticks
Ship bonus (Excavador MK-I): ×0.85 = 7.2 ticks
Module bonus (Láser Avanzado): ×0.90 = 6.5 ticks

Modificadores de estado:
  Energía (85): +5% eficiencia = 6.2 ticks
  Moral (82): +10% exp ganada (no afecta ticks)
  Estrés (15): Sin penalización

Trabajando con amigo cercano:
  Bonus de relación: +10% eficiencia = 5.6 ticks

RESULTADO FINAL: 6 ticks
Energía consumida: 2 × 6 = 12 energía
Exp ganada: 100 base × 1.10 (moral) = 110 exp
```

---

## Navegación

- [← Anterior: PRD-Economy.md](./PRD-Economy.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-FutureConsiderations.md](./PRD-FutureConsiderations.md)
