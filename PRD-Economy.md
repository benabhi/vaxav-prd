# Economía, Misiones y Organizaciones

**Parte del:** PRD - Vaxav
**Versión:** 1.5
**Fecha:** 2025-11-28
**Estado:** Documento Vivo - En Desarrollo

[Volver al PRD Master](./PRD-Master.md)

---

## 9. Economía y Recursos

### 9.1 Moneda

**Créditos:** Moneda única del juego.

**Fuentes de Créditos:**
- Vender recursos/items
- Completar misiones
- Recompensas de combate
- Comercio entre jugadores

**Sumideros de Créditos:**
- Comprar items/naves
- Reparaciones
- Tarifas de estación
- Impuestos de mercado
- Construcción

### 9.2 Recursos

### 9.2.1 Minerales en Crudo (Raw Ores)

Extraídos de asteroides.

**Tier 1 (Comunes):**
- **Tritanio:** Básico, muy común
- **Pirita:** Común
- **Mexalón:** Común

**Tier 2 (Poco Comunes):**
- **Isógeno:** Poco común
- **Noxcio:** Poco común

**Tier 3 (Raros):**
- **Megacita:** Raro
- **Zydrina:** Raro

**Tier 4 (Muy Raros):**
- **Morfita:** Muy raro
- **Arkonor:** Muy raro, alto valor

### 9.2.2 Minerales Refinados

Resultado de refinar minerales en crudo.

- Los minerales crudos se refinan en estaciones con Sala de Ingeniería (ver [PRD-Universe.md](./PRD-Universe.md#6.2.7-sala-de-ingeniería))
- Ratio de refinamiento depende de habilidades
- Se obtienen minerales purificados usados en fabricación

**Ejemplo:**

```
100 unidades de Tritanio Crudo
→ Refinamiento (85% eficiencia)
→ 85 unidades de Tritanio Puro
```

### 9.2.3 Componentes

Creados combinando minerales refinados.

**Ejemplos:**
- **Circuitos Electrónicos:** Tritanio + Pirita
- **Superconductores:** Isógeno + Megacita
- **Nano-Ensambladores:** Morfita + Zydrina

### 9.2.4 Otros Recursos

- **Combustible:** Para viajes largos
- **Municiones:** Consumibles de combate
- **Drones:** Consumibles/semi-permanentes
- **Blueprints (BPO/BPC):** Planos de fabricación

### 9.3 Cadena de Producción

**Flujo completo controlado por jugadores:**

```
1. Minería
   └─> Minerales Crudos

2. Refinamiento
   └─> Minerales Refinados

3. Fabricación de Componentes
   └─> Componentes

4. Fabricación de Módulos
   └─> Módulos de Nave

5. Construcción de Naves
   └─> Naves

6. Mercado
   └─> Venta a otros jugadores
```

**Blueprints (BPO/BPC):**
- **BPO (Original):** Infinitos usos, caro
- **BPC (Copia):** Usos limitados, más barato
- Se pueden investigar para mejorar eficiencia

### 9.4 Mercado de Habilidades

El mercado de inyectores de habilidades funciona de manera similar al mercado de EVE Online.

**Fuentes de Inyectores:**

1. **Laboratorios NPC:**
    - Cada laboratorio vende un catálogo limitado según su especialización (ver [PRD-Universe.md](./PRD-Universe.md#6.2.3-laboratorio))
    - Precio base según multiplicador de habilidad
    - Descuentos según nivel del laboratorio (hasta 20% en nivel 5)
    - Stock generalmente infinito
2. **Mercado de Jugadores:**
    - Los jugadores pueden revender inyectores comprados
    - Permite especulación y comercio
    - Precios determinados por oferta y demanda
    - Útil para encontrar inyectores raros o de estaciones lejanas
3. **Recompensas de Misiones:**
    - Misiones de alto nivel pueden recompensar con inyectores raros
    - Algunos inyectores solo se obtienen así (skills únicos o avanzados)

**Sistema de Órdenes (Estilo EVE Online):**

**Órdenes de Compra (Buy Orders):**
- El jugador especifica: "Compro Inyector de Minería por 18,000 créditos"
- Cuando alguien vende a ese precio, la orden se ejecuta
- Permite comprar sin estar presente

**Órdenes de Venta (Sell Orders):**
- El jugador especifica: "Vendo Inyector de Escudos por 32,000 créditos"
- El item se almacena en el mercado hasta que se venda
- Otros pueden comprarlo instantáneamente

**Características del Mercado:**
- **Alcance Regional:** Los mercados de nivel 5 conectan múltiples estaciones
- **Historial de Precios:** Ver tendencias de los últimos 30 días
- **Filtros Avanzados:** Por categoría de skill, multiplicador, precio
- **Mercado de Inyectores Destacado:** Sección especial en la UI del mercado
- **Comparador:** Muestra precios en diferentes estaciones

**Interfaz de Búsqueda de Inyectores:**
Desde la vista de habilidades, el jugador puede:
1. Ver habilidad "No Inyectada"
2. Click en "Buscar en Mercado"
3. Se muestra lista de órdenes de venta disponibles
4. Puede comprar inmediatamente o crear orden de compra

**Ejemplo de Búsqueda:**

```
Inyector: Pilotaje de Cruceros (x3)

Órdenes de Venta:
┌─────────────────────────────────────────────────────────────┐
│ Precio    │ Cantidad │ Estación              │ Distancia   │
├───────────┼──────────┼───────────────────────┼─────────────┤
│ 28,500 ₡  │    5     │ Puerto Génesis        │ Esta        │
│ 29,000 ₡  │    2     │ Estación Marte-2      │ 5 saltos    │
│ 30,000 ₡  │   12     │ Centro Comercial Vax  │ 2 saltos    │
└─────────────────────────────────────────────────────────────┘

Órdenes de Compra:
┌─────────────────────────────────────────────────────────────┐
│ Precio    │ Cantidad │ Estación              │ Rango       │
├───────────┼──────────┼───────────────────────┼─────────────┤
│ 27,500 ₡  │    3     │ Puerto Génesis        │ Esta        │
│ 27,000 ₡  │   10     │ Cualquiera            │ Regional    │
└─────────────────────────────────────────────────────────────┘

[ Comprar Ahora ]  [ Crear Orden de Compra ]
```

**Economía de Inyectores:**
- Los jugadores pueden **arbitraje:** comprar barato en una estación, vender caro en otra
- **Inyectores raros** se vuelven commodities valiosos
- Estaciones alejadas pueden tener precios más altos
- Creación de **rutas comerciales** de inyectores

---

## 10. Misiones y Agentes NPC

### 10.1 Sistema de Agentes

Los agentes NPC ofrecen misiones.

**Ubicación:**
- Estaciones NPC
- Cada estación tiene 1-5 agentes

**Atributos del Agente:**
- **Nombre:** Generado
- **Corporación:** A la que pertenece
- **Facción:** A la que pertenece la corporación (ver [PRD-Universe.md](./PRD-Universe.md#4-sistema-de-facciones))
- **Tipo:** Minería, Combate, Transporte, Investigación
- **Nivel:** 1-5

### 10.2 Nivel de Agente y Acceso

**Nivel 1:**
- Relación requerida: -20 (Neutral bajo)
- Recompensas bajas
- Misiones sencillas

**Nivel 2:**
- Relación requerida: +10
- Recompensas moderadas

**Nivel 3:**
- Relación requerida: +30
- Recompensas buenas

**Nivel 4:**
- Relación requerida: +50
- Recompensas excelentes

**Nivel 5:**
- Relación requerida: +70
- Recompensas excepcionales
- Acceso a items raros

### 10.3 Tipos de Misiones

### 10.3.1 Misiones de Minería

"Extrae X unidades de Y mineral"

**Recompensas:**
- Créditos
- +Relación con corporación/facción
- Experiencia en Minería

### 10.3.2 Misiones de Transporte

"Transporta X m³ de carga desde A hasta B"

**Dificultad:**
- Puede haber piratas en la ruta
- Límite de tiempo (ticks)

**Recompensas:**
- Créditos (proporcional a distancia y riesgo)
- +Relación
- Experiencia en Pilotaje

### 10.3.3 Misiones de Combate

"Elimina X naves enemigas en Y ubicación"

**Variantes:**
- Eliminar piratas
- Escoltar convoy
- Defender estación

**Recompensas:**
- Créditos
- Loot de enemigos
- +Relación (y -Relación con facción enemiga)
- Experiencia en combate

### 10.3.4 Misiones de Investigación

"Escanea X anomalías" o "Recupera datos"

**Recompensas:**
- Blueprints
- Datos de investigación
- +Relación
- Experiencia en Exploración

---

## 11. Corporaciones y Organizaciones

### 11.1 Corporaciones de Jugadores

**Creación:**
- Requiere: 1,000,000 Créditos
- Nombre único
- Mínimo 5 miembros fundadores

**Características:**
- Hangar corporativo
- Almacén compartido
- Chat corporativo
- Roles y permisos
- Impuestos corporativos (% de ingresos de miembros)

**Roles:**
- **CEO:** Control total
- **Director:** Gestión de miembros, diplomacia
- **Gerente:** Gestión de recursos
- **Reclutador:** Invitar miembros
- **Miembro:** Acceso básico

### 11.2 Alianzas

Agrupación de múltiples corporaciones.

**Requisitos:**
- Mínimo 3 corporaciones
- Votación de corporaciones fundadoras

**Beneficios:**
- Compartir estaciones
- Sistema de defensa mutua
- Declaraciones de guerra conjuntas

### 11.3 Diplomacia

**Estados Diplomáticos:**
- Guerra
- Neutral
- Pacto de No Agresión
- Alianza

**Sistema de Guerra:**
- Declaración de guerra: 144 ticks (~24h) de cooldown
- Duración mínima: 1008 ticks (~7 días)
- Costo: Escala según tamaño

---

## Navegación

- [← Anterior: PRD-ShipsAndCombat.md](./PRD-ShipsAndCombat.md)
- [↑ Volver al Índice](./PRD-Master.md)
- [→ Siguiente: PRD-SocialSystem.md](./PRD-SocialSystem.md)
