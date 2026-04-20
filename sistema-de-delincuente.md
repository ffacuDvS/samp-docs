# Sistema de delincuente

## Introducción

El sistema de **Delincuente** te permite dedicarte a la vida criminal: robar a jugadores, hurtar en tiendas, atracar negocios, asaltar propiedades y robar o desarmar vehículos. Para compensar la libertad que ofrece, muchos delitos tienen **cooldowns largos** y exigen respetar las normativas de rol.

Para convertirte en delincuente debes ir a uno de los **puntos escondidos en el mapa** y usar `/delincuente`. El único requisito es tener al menos **16 horas jugadas** y no pertenecer a una facción legal.

### Comandos

- /delincuente — conviértete en delincuente si estás en el lugar adecuado.
- /ayudarobos — muestra las normativas más relevantes para robar a jugadores.
- /venderrobo — obtén un checkpoint en una zona de mercado negro para vender tu botín.

## Habilidad

Tu **habilidad como delincuente** determina directamente las probabilidades de éxito, la recompensa y los tiempos de tus delitos. Además de la habilidad global, existen dos habilidades específicas:

- **Robo de vehículos** — afecta al éxito al forzar, cruzar cables y desarmar piezas.
- **Robo de propiedades** — afecta al éxito al forzar entradas y robar muebles.

A mayor habilidad, más rápido eres, más probabilidades tienes de triunfar y más puntos puedes conseguir por cada delito.

## Robo a jugadores

El sistema de robo a jugadores existe para **evitar abusos de ambas partes**: asegura que las víctimas no sufran robos continuos y que los ladrones registren correctamente cada intento. **Toda interacción de robo debe pasar por este sistema**: no se puede forzar a un jugador a ceder dinero o inventario por rol.

- Un delincuente puede robar a otros jugadores **cada 2 horas**.
- Una víctima solo puede ser robada **una vez cada 2 días**.
- Antes de robar debes comprobar con `/victima [id]` si la persona es robable. **Ignorar este aviso es sanción administrativa**.
- Durante el robo necesitas tener un **arma de fuego o cuchillo** en la mano derecha.
- La víctima tiene **60 segundos** para confirmar el rol; si no lo hace, el robo se cancela y se avisa a la administración.
- Si la víctima muere tras haber confirmado el robo, puedes seguir saqueando su inventario. **Nunca puedes robarle a un cadáver** sin confirmación previa.

Cuando la víctima acepta, se te abre un **menú con todo su inventario** (bolsillos, accesorios y dinero). Los objetos robados pasan directos a tus bolsillos; si son demasiado grandes, van a tus manos. El dinero se convierte en **fajos de billetes**.

### Duración del robo según habilidad

| Habilidad de delincuente | Tiempo de robo de inventario |
| ------------------------ | ---------------------------- |
| Menos de 30              | 60 segundos                  |
| 30 – 49                  | 90 segundos                  |
| 50 – 69                  | 120 segundos                 |
| 70 – 100                 | 150 segundos                 |

### Comandos

- /victima [id] — comprueba si un jugador puede ser robado.
- /robar [id] — inicia el robo y registra el intento en el sistema.
- /ayudarobos — resumen de normativas de robo a jugadores.

## Hurtar en negocios

Puedes hurtar productos pequeños dentro de un negocio con `/hurtar`. Aparecerá un temporizador que indica cuánto falta para completarlo. Al terminar con éxito ganas **1 punto de habilidad** y el negocio queda con **cooldown de 3 horas** (hurto/atraco). Tu cooldown personal de hurto es de **15 minutos**.

No tiene restricción de habilidad.

### Duración del hurto según habilidad

| Habilidad | Tiempo para terminar |
| --------- | -------------------- |
| ≤ 15      | 45 segundos          |
| 16 – 49   | 30 segundos          |
| ≥ 50      | 15 segundos          |

### Comandos

- /hurtar — hurta un producto del negocio en el que estás.

## Atracar negocios

Para atracar necesitas un **arma de fuego o un cuchillo** y estar en el mostrador del negocio. La recompensa depende del **dinero en caja** y de tu habilidad. Sin al menos **4 policías de servicio**, la recompensa se reduce a la mitad; en zonas rurales, solo recibes un tercio y el cooldown se triplica.

Un atraco exitoso otorga **3 puntos de habilidad**. Independientemente de si fallas o aciertas, **se avisa a la policía**. El negocio queda con cooldown de atraco durante horas.

### Progresión según habilidad

| Habilidad   | Máximo  | Cooldown | Tiempo del atraco |
| ----------- | ------- | -------- | ----------------- |
| Menos de 30 | $8.000  | 18 h     | 120 s             |
| 30 – 49     | $10.000 | 16 h     | 100 s             |
| 50 – 69     | $12.000 | 14 h     | 80 s              |
| 70 o más    | $15.000 | 12 h     | 60 s              |

Sin restricción de habilidad.

### Comandos

- /atracar — comienza un atraco en el mostrador del negocio.

## Robo de propiedades

Para asaltar una propiedad debes **forzar la entrada** con `/forzarentrada`. El mismo comando sirve para forzar puertas interiores. Según la herramienta que uses, cambiará la probabilidad de éxito: **destornillador**, **ganzúa** o **palanca**.

No hace falta que haya policías conectados, pero debes respetar la normativa de entorno y llamar al 911 si la situación lo amerita.

Actualmente **solo se pueden robar electrodomésticos** (muebles válidos), y **solo dentro de casas**. Una vez dentro, inicia el robo con `/robarprop` y roba muebles con `/robarmueble`. Los muebles robados se venden en el punto de `/venderrobo`.

Forzar la entrada con éxito otorga **2 puntos de habilidad de robo de propiedades** y **2 puntos de habilidad global**. El cooldown de forzar entradas es de **6 horas**.

### Progresión de robo de propiedades

| Habilidad  | Espera | Tiempo total del robo |
| ---------- | ------ | --------------------- |
| Menos de 6 | 40 s   | 120 s                 |
| 6 – 15     | 30 s   | 180 s                 |
| 16 o más   | 20 s   | 240 s                 |

### Probabilidad de forzar la entrada

| Herramienta    | <6  | 6–15 | ≥16  |
| -------------- | --- | ---- | ---- |
| Destornillador | 30% | 40%  | 50%  |
| Ganzúa         | 50% | 60%  | 70%  |
| Palanca        | 80% | 90%  | 100% |

### Cooldown de /robarprop según habilidad global

| Habilidad global | Cooldown |
| ---------------- | -------- |
| Menos de 50      | 24 h     |
| 50 – 79          | 18 h     |
| 80 o más         | 16 h     |

### Comandos

- /forzarentrada — fuerza la entrada o una puerta interior de una propiedad.
- /robarprop — inicia el robo estando dentro de la propiedad.
- /robarmueble — roba el electrodoméstico más cercano.
- /venderrobo — obtén un checkpoint para vender muebles robados.

## Robo y desarme de vehículos

Los vehículos tienen distintos tipos de **alarma** e **ignición**: **básica**, **segura**, **avanzada** y **super**. Cuanto más avanzado el sistema, más difícil será robarlo. Puedes inspeccionar los sistemas de un auto antes de actuar.

Las **piezas del vehículo** pueden robarse y venderse al punto de delincuente por el **35% de su costo base**, o directamente a otros jugadores.

### Comandos de inspección

- /miraralarma — mira el tipo de alarma (con el capó abierto, cualquier jugador).
- /mirargps — mira el tipo de GPS del vehículo.
- /mirarpanel — mira el tipo de ignición (dentro del vehículo como conductor, cualquier jugador). Si la ignición está adulterada, se indica.

### Romper ventanilla

`/romperventanilla` rompe la ventanilla, **activa la alarma** y **desbloquea el vehículo**. No otorga habilidad y tiene **cooldown de 6 horas**. Sin restricción de habilidad.

### Forzar puerta

Si el vehículo está cerrado y tienes una **ganzúa**, usa `/forzarpuerta` para intentar abrirla. Te congelarás durante el intento. Si fallas, puede o no activarse la alarma según tu habilidad. Un forzado exitoso otorga **2 puntos de habilidad global** y aplica **cooldown de 6 horas**.

El tipo de cerradura depende del sistema de ignición (básica, segura, avanzada, super).

| Habilidad de vehículos | Alarma al fallar | Básica     | Segura     | Avanzada/Super |
| ---------------------- | ---------------- | ---------- | ---------- | -------------- |
| Menos de 10            | 60%              | 35 s · 50% | 45 s · 40% | 55 s · 30%     |
| 10 – 19                | 40%              | 25 s · 60% | 35 s · 50% | 45 s · 40%     |
| 20 o más               | 20%              | 15 s · 70% | 25 s · 60% | 35 s · 50%     |

### Cortar y unir cableado

Dentro del vehículo, usa `/cortarcableado` para intentar cruzar los cables. A mayor ignición, más cables habrá en la combinación; fallar demasiadas veces activa la alarma. Tras cortar dos cables, usa `/unircableado` para encender el motor.

Encender el motor con éxito otorga **2 puntos de habilidad de vehículos**. Requiere al menos **20 puntos de habilidad de robo de vehículos** para usarse.

| Habilidad de vehículos | Intentos | Cooldown |
| ---------------------- | -------- | -------- |
| Menos de 10            | 3        | 16 h     |
| 10 – 19                | 4        | 12 h     |
| 20 o más               | 5        | 8 h      |

### Desarme y robo de piezas

Con `/desarme` cerca del vehículo puedes robar piezas. Cada pieza requiere **herramientas concretas** y algunas **solo pueden desmontarse en interiores**. El cooldown de desarme es siempre **24 horas**, sin importar la pieza o habilidad.

**Piezas desmontables en exteriores:**

| Pieza                  | Herramienta              | Tiempo | Habilidad que otorga |
| ---------------------- | ------------------------ | ------ | -------------------- |
| Radio                  | Destornillador           | 60 s   | +2 vehículos         |
| Llantas                | Llave de cruz            | 75 s   | +2 vehículos         |
| Convertidor catalítico | Palanca o destornillador | 90 s   | +2 vehículos         |

**Piezas desmontables solo en interiores:**

| Pieza           | Requisitos                              | Tiempo | Habilidad que otorga                                           |
| --------------- | --------------------------------------- | ------ | -------------------------------------------------------------- |
| Parachoques     | Palanca o destornillador + 15 habilidad | 300 s  | +2 vehículos                                                   |
| Faldones        | Palanca o destornillador + 25 habilidad | 300 s  | +2 vehículos                                                   |
| Alerón          | Palanca o destornillador + 25 habilidad | 300 s  | +2 vehículos                                                   |
| Tomas de aire   | Palanca o destornillador + 25 habilidad | 300 s  | +2 vehículos                                                   |
| Motor           | Palanca o destornillador + 35 habilidad | 600 s  | +7 vehículos                                                   |
| Vehículo entero | 95 habilidad                            | 900 s  | +16 habilidad (todas las piezas al inventario de la propiedad) |

### Cantidad de piezas que puedes robar por sesión

| Habilidad de vehículos | Piezas |
| ---------------------- | ------ |
| Menos de 15            | 1      |
| 15 – 34                | 2      |
| 35 – 64                | 3      |
| 65 – 94                | 4      |
| 95 o más               | Todas  |

### Comandos

- /romperventanilla — rompe la ventanilla y desbloquea el vehículo.
- /forzarpuerta — intenta abrir la puerta con una ganzúa.
- /cortarcableado — corta los cables de la ignición para intentar encender el motor.
- /unircableado — une los cables cortados.
- /desarme — desmonta piezas del vehículo más cercano.
- /venderrobo — vende las piezas robadas en el mercado negro.
