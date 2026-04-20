# Sistema de camionero

## Introducción

El sistema de tráileres es una rama de las **empresas de repartos** y trata del transporte de cargas pesadas mediante cisternas o carros de arrastre. Los camioneros avanzados pueden convertirse en traileros según su habilidad en el rubro y también tienen la posibilidad de **independizarse** de las empresas de reparto.

Los camioneros con un mínimo de **75 de habilidad de camionero** (`pTruckerSkill`) son catalogados como **camioneros avanzados** y desbloquean los comandos del sistema de tráilers.

### Comandos

- /trailero — asigna un viaje aleatorio (origen, destino y tipo de carga).
- /recogertrailer — spawnea y acopla el tráiler en el punto de recogida.
- /entregartrailer — entrega el tráiler en el destino y cobra el pago.
- /cancelartrailer — cancela la misión antes de recoger el tráiler (−2 de habilidad de camionero).
- /rastreotrailer — reubica el checkpoint sobre tu tráiler actual.

## Camiones

Los camiones pueden ser propiedad de las **empresas de reparto** o del propio camionero. Si el camionero realiza una misión de trailero **sin estar de servicio** en una empresa de reparto, el sistema entiende que está haciendo viajes por su cuenta y no paga a la empresa. Para trabajar como camionero de una empresa, debes utilizar un **camión de la empresa** y estar de servicio.

Los camiones habilitados son:

| Modelo | ID |
|--------|----|
| Linerunner | 403 |
| Tanker | 514 |
| Roadtrain | 515 |

Cualquier intento de usar `/trailero`, `/recogertrailer` o `/entregartrailer` desde otro vehículo será rechazado.

## Misión

Para comenzar a trabajar basta con utilizar `/trailero`. El comando asigna un viaje aleatorio de los **+45 viajes predefinidos**, otorgando un origen, destino y tipo de carga que deberás transportar. Si no tienes **licencia de cargas pesadas** (`pTruckingLicense`), el sistema te lo advierte: podrías ser multado si un policía te detiene.

### Recogida

Cuando llegues al punto de recogida, utiliza `/recogertrailer` para spawnear el tráiler correspondiente. Requisitos:

- Estar dentro de un camión habilitado (403, 514 o 515).
- Estar dentro de un radio de **10 metros** del punto de recogida.
- No tener ya un tráiler acoplado.

**TIP**: llega siempre de frente al punto de carga para evitar que el tráiler se buguee.

El tráiler se crea 5 unidades por delante y a la derecha del punto y se acopla automáticamente al camión **1 segundo después** mediante `AttachTrailerToVehicle`. Una vez acoplado, el checkpoint se actualiza al destino final.

### Entrega

Cuando llegues al destino, utiliza `/entregartrailer` con la misma mecánica. Requisitos:

- Estar en un camión habilitado con el tráiler correcto acoplado.
- Estar dentro de un radio de **10 metros** del punto de entrega.
- El tráiler acoplado debe ser el que recogiste originalmente.

## Pagos

El pago base se calcula como `distancia_3D × 2` (redondeado hacia arriba), depositado en el **banco** del camionero y sumado al próximo paycheck.

| Situación | Pago al camionero | Pago a la empresa |
|-----------|-------------------|-------------------|
| **Empleado de empresa** (el camión pertenece a tu `pEmployment`) | 100% del pago base | 100% del pago base a la caja de la empresa |
| **Independiente** (sin empleo o camión ajeno) | **1/3** del pago base | — |

El camionero independiente recibe una notificación roja indicándole que solo cobró la tercera parte por no trabajar para una empresa.

## Habilidad de camionero

Cada entrega otorga un **50% de probabilidad** de subir habilidad:

- Jugador estándar: **+1** de `pTruckerSkill`.
- Jugador con **premium**: **+2** de `pTruckerSkill`.

El progreso se muestra con el sprite "Camionero". Cancelar una misión resta **−2**, y que te roben el tráiler resta **−5**.

Entregar con éxito como empleado otorga además el logro `ACHIEVEMENT_TRAILER`.

## Tipos de tráileres

Hay **13 tipos de tráiler** implementados, con modelos base 584 (cisterna), 591 (contenedor), 450 (chatarra) y 435 (articulado). Varios incluyen un objeto custom 3D acoplado para mejorar la inmersión.

| # | Nombre | Vehículo base | Precio robado |
|---|--------|---------------|---------------|
| 0 | Cisterna de petróleo | 584 | $10.000 |
| 1 | Cisterna de químicos | 584 + custom | $8.000 |
| 2 | Tráiler con artículos | 591 | $7.000 |
| 3 | Tráiler con artículos | 435 | $7.000 |
| 4 | Tráiler con artículos | 591 + custom | $7.000 |
| 5 | Tráiler con artículos | 591 + custom | $7.000 |
| 6 | Tráiler con chatarra | 450 + custom | $2.500 |
| 7 | Tráiler con gravilla | 450 | $2.500 |
| 8 | Tráiler con arena | 450 + custom | $2.500 |
| 9 | Tráiler con materiales | 584 + custom | $8.000 |
| 10 | Frigorífico | 591 + custom | $9.000 |
| 11 | Tráiler con madera | 584 + custom | $5.000 |
| 12 | Tráiler con contenedor | 591 + custom | $2.500 |

## Robo de tráiler

Los miembros de **facciones ilegales oficiales** pueden interceptar y vender tráileres no registrados (sin dueño, facción ni empresa). Requisitos:

- Ser miembro **oficial** de una facción ilegal (`IsIlegalFactionMember` + `IsOfficialIlegalMember`).
- Tener al menos **50 de habilidad de delincuente** (`pCriminalSkill`).
- No estar en cooldown de criminal (`pCriminalCooldown`).
- Estar dentro de un camión habilitado con el tráiler enganchado.
- Llevar el tráiler al **punto de venta** en `(226.49, 85.66, 4.23)`.

El pago es el **precio completo del tráiler** (ver tabla) en efectivo. Tras vender:

- Se aplica **cooldown de 12 horas** al delincuente.
- El camionero víctima pierde el rastro del tráiler y recibe **−5** de habilidad de camionero.
- El tráiler se destruye.

### Comandos

- /robartrailer — vende el tráiler enganchado al punto de fence (solo facciones ilegales oficiales).
