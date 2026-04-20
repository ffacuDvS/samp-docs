# Sistema de zonas de pandilla

## Introducción

Las **zonas de pandilla** delimitan los territorios controlados por las facciones criminales. Aparecen en el minimapa con el color distintivo de la facción que las controla y pueden ocultarse desde `/panel`.

El sistema persigue tres objetivos:

- Reducir los conflictos innecesarios dando a cada grupo un espacio claro.
- Premiar la **presencia activa** dentro del propio territorio con bonificaciones mecánicas.
- Fomentar la competencia por la captura de zonas a través del sistema de **influencias**.

### Comandos

- /influencias — muestra las influencias acumuladas por cada facción en la zona de pandilla donde estás.
- /panel — abre el panel de preferencias desde donde puedes ocultar las zonas de pandilla del minimapa. Alias: `/preferencias`.

## Beneficios por presencia en zona propia

Cuando un miembro de una pandilla realiza ciertas actividades **dentro de una zona controlada por su propia facción**, tiene una probabilidad de ganar puntos de habilidad (delincuente o ladrón de autos).

**Requisitos** para que los beneficios se activen:

- La facción del jugador debe ser de **tipo pandilla**.
- El jugador debe tener al menos **10 puntos de habilidad de drogas**.
- La zona donde se encuentra debe estar **controlada por su facción**.
- Haber pasado el **cooldown global** de 30 minutos desde la última recompensa.

### Tabla de recompensas

| Actividad | Probabilidad | Puntos | Categoría |
|---|---|---|---|
| Fumar tabaco | 5 % | +1 | Delincuente |
| Beber alcohol | 10 % | +1 | Delincuente |
| Drogarse | 50 % | +1 a +2 | Delincuente |
| Cartear | 50 % | +2 a +3 | Delincuente |
| Robar un vehículo | 40 % | +2 a +3 | Ladrón de autos |
| Grafitear | 40 % | +2 a +3 | Delincuente |

Cada recompensa activa un **cooldown único de 30 minutos** sobre el jugador — durante ese tiempo ninguna otra actividad de la lista otorgará puntos, aunque sí se ejecute.

### Recompensas pasivas

Cada **30 minutos** se ejecuta un barrido automático por cada miembro de una pandilla presente en su propia zona:

- **30 %** de probabilidad de ganar entre **$100 y $499** en mano.
- **50 %** de probabilidad de recibir una **misión SMS** de un NPC pidiendo drogas, con una propiedad aleatoria de la zona como punto de entrega (solo si el jugador no tiene otra misión activa).

Los jugadores pausados no participan en estos sorteos.

## Influencias de pandilla

La **influencia** es el contador que determina qué facción controla cada zona. Todas las pandillas, mafias y facciones oficiales pueden acumular influencia en cualquier zona simplemente **estando presentes en ella**.

### Cómo se gana influencia

El sistema procesa influencia **una vez por minuto** por cada jugador elegible. No se genera influencia si:

- El jugador no pertenece a una pandilla o mafia.
- Está pausado (AFK).
- Está dentro de un vehículo.

Por cada jugador elegible dentro de una zona se añade una cantidad de influencia a su facción basada en esta fórmula:

| Fuente | Influencia |
|---|---|
| Presencia base | +1 |
| Por cada otra zona ya controlada por la facción | +1 |
| Facción con estatus **destacada** | +1 |
| Facción de tipo **pandilla** | +2 |
| Facción con estatus **oficial** | +3 |

Los modificadores son **acumulables**. Además, cada vez que un miembro suma influencia en una zona, **todas las demás facciones con influencia en esa zona pierden 1 punto** (hasta un mínimo de 0).

La influencia por facción está capada a **10.000 puntos** en cada zona.

### Cómo se captura una zona

Cada vez que se actualiza la influencia, **15 segundos después** se evalúa quién tiene el mayor valor en la zona. La facción con **más influencia** pasa a controlarla, siempre y cuando supere el umbral de **100 puntos**.

> **Nota:** el umbral de captura es de **100 puntos**, no 5.000. Una zona puede cambiar de manos con relativa rapidez si no hay oposición.

### Mantenimiento

Cada **1 hora** se ejecuta un evento global que **reduce aleatoriamente** la influencia de todas las facciones en todas las zonas en un valor entre **0 y 10 puntos**. Esto evita que una facción mantenga una zona indefinidamente sin actividad.

## Beneficios por controlar territorios

Los miembros de facciones que controlan zonas reciben dos beneficios principales:

### Atraso en alertas policiales

Los incidentes (balaceras, heridos de bala, reportes al 911) generados **dentro de una zona capturada por una facción** se retrasan entre **30 y 60 segundos adicionales** (aleatorio) antes de ser anunciados a la policía, sumándose al retardo normal de la alerta.

### Bonificación en el paycheck

En cada paycheck, los miembros de facciones tipo pandilla o mafia reciben una bonificación por cada zona controlada:

- **Entre $0 y $4** por zona controlada, sumados al paycheck (aleatorio por zona).

Los miembros de facciones que pierden su estatus de pandilla/mafia, o cuya facción es disuelta, pierden automáticamente el control de todas sus zonas y sus influencias asociadas.

## Ejemplos prácticos

### Ejemplo 1 — Facción oficial con 1 zona ya controlada

Un miembro de una **facción oficial tipo pandilla** que ya controla 1 zona, acumulando influencia en una segunda zona:

- +1 por presencia.
- +1 porque su facción ya controla otra zona.
- +2 por tipo pandilla.
- +3 por estatus oficial.
- **Total: 7 puntos por minuto.**

Con 10 miembros presentes, la facción genera **70 puntos por minuto**. Como el umbral de captura es de **100 puntos**, podrían capturar la nueva zona en poco más de **1 minuto** (asumiendo que no haya oposición que reste).

### Ejemplo 2 — Facción no oficial sin zonas previas

Un miembro de una **pandilla no oficial y no destacada** en su primer territorio:

- +1 por presencia.
- +2 por tipo pandilla.
- **Total: 3 puntos por minuto.**

Con 10 miembros presentes, la facción genera **30 puntos por minuto**, capturando la zona en unos **3-4 minutos**.

La presencia simultánea de enemigos cuesta **−1 punto por minuto por cada enemigo**, por lo que una zona muy disputada puede tardar significativamente más en caer.
