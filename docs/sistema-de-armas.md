# Sistema de armas y heridas

## Introducción

El sistema de armas y heridas maneja las armas de fuego disponibles, su identificación mediante seriales y las consecuencias físicas de recibir disparos, apuñaladas o golpes. Cada arma tiene un calibre, peso, capacidad de cargador y daño distinto; cada herida queda registrada en el cuerpo y puede provocar sangrado, desmayo o muerte.

<img width="396" height="465" alt="image" src="https://github.com/user-attachments/assets/03246ace-0513-420d-b4aa-97686519bd6f" />

### Comandos

- `/heridas [id]` — muestra el listado de daños que ha sufrido un personaje cercano.
- `/asesino` — muestra el nombre de la última persona que te dejó herido.
- `/aceptarmuerte` — cuando estás herido, acepta tu muerte definitiva en vez de esperar.

## Seriales del arma

Cada arma fabricada o comprada lleva un **número de serial único** que la identifica. Sirve para rastrear armas robadas o usadas en crímenes. Los seriales emitidos por el armamento federal usan el formato **CÓDIGO-NÚMERO** (por facción); las armas comunes tienen un serial numérico de 8 cifras.

<img width="212" height="18" alt="image" src="https://github.com/user-attachments/assets/8bc00f91-f086-4495-8241-b1b1c40d1f06" />

Un delincuente experimentado puede **borrar el serial** de su arma con un destornillador, pero este delito aumenta considerablemente la condena si lo descubren.

<img width="212" height="18" alt="image" src=../assets/sistema-de-armas/serial-borrado1.png>

<img width="212" height="18" alt="image" src=../assets/sistema-de-armas/serial-borrado2.png>

### Comandos

- `/serial` — muestra el serial del arma que tienes en la mano derecha.
- `/borrarserial [confirmar]` — borra el serial del arma en la mano derecha (requiere destornillador en la mano izquierda y al menos 80 de habilidad de delincuente.).

## Sistema de heridas

Cuando recibes daño por arma de fuego, arma blanca o golpes, la herida queda **registrada en tu cuerpo** indicando el arma utilizada, la parte del cuerpo afectada, el daño causado y hace cuánto ocurrió. Esta información puede consultarla cualquier personaje cercano con `/heridas`.

<img width="394" height="429" alt="image" src="https://github.com/user-attachments/assets/dd443fac-d3b0-4ec7-9f06-adbad93c19d2" />

- Al caer tu vida a niveles mínimos pasas al estado **herido**: necesitas un médico o alguien que te ayude, o morirás tras unos minutos.
- Puedes morir de forma inmediata si sufres demasiadas heridas críticas: **5 disparos**, **5 apuñaladas**, **10 golpes fuertes** o un **tiro en la cabeza**.
- El chaleco antibalas absorbe parte del daño de disparos antes de afectar tu vida.
- La vida máxima del personaje depende de tu nivel de musculatura en el gimnasio (de 100 HP base hasta 175 HP con musculatura máxima).

<img width="397" height="267" alt="image" src="https://github.com/user-attachments/assets/bbd275a9-8843-4b78-888f-b4ae5bc658a6" />

### Comandos

- `/heridas [id]` — revisa las heridas de un personaje cercano.
- `/asesino` o `/qfa` — consulta quién te dejó herido por última vez.
- `/aceptarmuerte` — aceptas la muerte definitiva cuando estás herido.

## Estado del arma

Cada arma tiene una **calidad** (0 a 100) que se va deteriorando con el uso y con el paso de los días. A menor calidad, mayor probabilidad de que falle al recargar o que se atasque.

Estados según la calidad:

- **En buen estado** — calidad sobre 50. Funciona sin problemas.
- **Desgastada** — calidad entre 25 y 50. Probabilidad baja de fallar al cargar el cargador.
- **Dañada** — calidad entre 1 y 25. Probabilidad alta de fallar al cargar el cargador.
- **Rota** — calidad 1 o menor. El cargador queda atascado y no se puede recargar hasta repararla.

<img width="400" height="45" alt="image" src=../assets/sistema-de-armas/limpiararma.png>>

### Reparar el arma

Para reparar un arma necesitas un **kit de limpieza**. Sostén el arma en la **mano derecha** y el kit de limpieza en la **mano izquierda**, y usa `/limpiararma`.

- El proceso tarda entre **15 segundos** (arma casi nueva) y **60 segundos** (arma rota).
- Cada reparación restaura entre **10% y 33%** de calidad, según el estado actual.
- Cada reparación consume **5 unidades** del kit de limpieza.
- No puedes repararla dentro de un vehículo ni guardarla durante el proceso, o se cancela.

### Comandos

- `/limpiararma` — repara el arma de tu mano derecha usando el kit de limpieza de tu mano izquierda. Alias: `/reparararma`.

## Municiones y cargas

Cada arma usa un **calibre específico** (9x19, .45, 12GA, 7.62x39, etc.) y solo puede cargar munición compatible con ese calibre. Para disparar necesitas tener **balas en el cargador** del arma.

El sistema funciona en tres partes:

- **Arma**: tiene una capacidad máxima de balas en su recámara.
- **Cargador**: se llena con balas de una **caja de munición** del mismo calibre.
- **Caja de munición**: funciona como reserva grande; se usa para rellenar cargadores, no directamente el arma.

### Recargar el arma

Con el arma en la **mano derecha** y el cargador compatible en la **mano izquierda** (o en tu inventario, equipo o cerca si es de gran capacidad), usa `/cargar` o `/recargar` para pasar balas del cargador al arma.

- Puedes especificar cuántas balas quieres cargar, o dejarlo vacío para llenar al máximo.
- Si el arma está **rota** el cargador se atasca y no podrás recargar.
- Si el arma está **dañada o desgastada** existe la probabilidad de que falle al cargar y tengas que reintentar.

<img width="216" height="79" alt="image" src="https://github.com/user-attachments/assets/57e3c92d-71bb-4f49-b586-ecddf3309c20" />

### Rellenar el cargador

Para rellenar un cargador vacío o parcial, sostén el cargador en la **mano derecha** y acércate a una **caja de munición** del mismo calibre. Usa `/municion` para pasar balas de la caja al cargador.

<img src="../assets/sistema-de-armas/municion1.png">

### Comandos

- `/cargar [cantidad]` — carga balas desde tu cargador hacia el arma en la mano derecha. Alias: `/recargar`.
- `/municion` — rellena el cargador que llevas en la mano derecha desde una caja de munición cercana.

## Lista de armas y parámetros

Cada arma tiene: **calibre**, **capacidad del cargador**, **peso (kg)**, **daño por impacto** y **precio**. Las armas **de bolsillo** se pueden ocultar bajo la ropa; las **pesadas** deben portarse visibles en la espalda o en las manos.

### Pistolas (de bolsillo)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| Taurus 605 | .357 | 14 | 0.6 kg | 25 | $1.214 |
| Taurus G2C | .40 | 24 | 0.8 kg | 16 | $810 |
| CZ75B | 9x19 | 17 | 1.0 kg | 17 | $810 |
| Beretta 92FS | 9x19 | 34 | 1.2 kg | 16 | $890 |
| S&W Shield | 9x19 | 14 | 0.8 kg | 22 | $972 |
| Springfield XD40 | .40 | 14 | 1.0 kg | 23 | $1.052 |
| Sig Sauer SP2022 | 9x19 | 34 | 0.8 kg | 18 | $1.132 |
| Glock 39 | .45 | 14 | 1.0 kg | 24 | $1.214 |
| Glock 31 | .357 | 21 | 1.1 kg | 25 | $1.294 |
| Glock 17 | 9x19 | 28 | 1.2 kg | 26 | $1.375 |
| Sig Sauer P226 | 9x19 | 28 | 1.0 kg | 26 | $1.456 |
| S&W M&P9 | 9x19 | 28 | 1.3 kg | 26 | $1.538 |
| HK USP | .45 | 28 | 1.4 kg | 27 | $1.618 |
| Hi-Point C9 | 9x19 | 21 | 0.6 kg | 20 | $890 |
| Bersa Firestorm | .380 | 17 | 0.6 kg | 17 | $810 |
| Desert Eagle | .44 | 7 | 1.6 kg | 40 | $3.235 |
| CZ75 Auto | 9x19 | 17 | 1.2 kg | 16 | $972 |
| AA Arms AP9 | 9x19 | 20 | 1.1 kg | 15 | $1.132 |
| Beretta 92F Auto | 9x19 | 20 | 1.3 kg | 16 | $1.294 |
| Glock 18 Auto | 9x19 | 25 | 1.0 kg | 17 | $1.456 |
| FN 509 MRD-LE | 9x19 | 35 | 1.2 kg | 27 | $1.132 |
| MAC-10 | 9x19 | 25 | 1.0 kg | 16 | $920 |
| AA Custom FMG9 | 9x19 | 40 | 1.0 kg | 17 | $19.406 |

### Pistolas con silenciador (de bolsillo)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| Suppressed Ruger MkIv | .22 LR | 10 | 1.0 kg | 20 | $810 |
| Suppressed HK45 | .45 | 8 | 1.3 kg | 24 | $1.294 |
| AF-1 Strike One | 9x19 | 34 | 0.75 kg | 27 | $3.295 |

### Escopetas compactas (de bolsillo)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| Serbu Super Shorty | 12GA | 3 | 1.8 kg | 34 | $1.618 |
| Mossberg 500 Compact Cruiser | 12GA | 4 | 2.2 kg | 26 | $1.941 |

### Escopetas (pesadas)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| Citadel CDP12 | 12GA | 5 | 3.0 kg | 25 | $810 |
| Mossberg 590A1 | 12GA | 6 | 2.4 kg | 28 | $972 |
| Mossberg Mav88 | 12GA | 7 | 3.0 kg | 28 | $1.132 |
| Remington 870 | 12GA | 8 | 3.6 kg | 30 | $1.456 |
| Benelli M4 | 12GA | 6 | 4.0 kg | 33 | $1.779 |

### Subfusiles (pesadas)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| UZI | 9x19 | 30 | 3.5 kg | 15 | $2.588 |
| Colt Commando | 9x19 | 45 | 2.6 kg | 16 | $2.912 |
| HK MP7 | 9x19 | 30 | 1.9 kg | 17 | $3.073 |
| HK MP5 | 9x19 | 30 | 2.5 kg | 18 | $3.397 |

### Fusiles de asalto (pesadas)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| AKMSU | 7.62x39 | 60 | 2.8 kg | 18 | $2.013 |
| Zastava M70 | 7.62x39 | 60 | 3.7 kg | 21 | $2.750 |
| Colt AR15 | 5.56x45 | 30 | 3.2 kg | 9 | $2.875 |
| Colt M4 | 5.56x45 | 30 | 3.5 kg | 14 | $3.105 |
| HK416 | 5.56x45 | 30 | 3.8 kg | 16 | $3.397 |
| WASR-10 | 7.62x39 | 60 | 2.8 kg | 16 | $2.588 |
| SLR-107 | 7.62x39 | 60 | 2.8 kg | 14 | $1.725 |
| M16A1 | 5.56x45 | 30 | 3.2 kg | 10 | $2.645 |
| M240 | 7.62x51 | 250 | 3.5 kg | 33 | $6.389 |

### Rifles y francotiradores (pesadas)

| Arma | Calibre | Cargador | Peso | Daño | Precio |
|---|---|---|---|---|---|
| Savage Axis XP | .308 Winchester | 4 | 3.3 kg | 40 | $972 |
| Remington 788 | .308 Winchester | 3 | 3.3 kg | 45 | $1.941 |
| VSS Vintorez | 9x39 | 10 | 2.5 kg | 15 | $1.941 |
| Ruger American | .308 Winchester | 4 | 3.0 kg | 25 | $5.750 |
| M40A6 | 7.62x51 | 5 | 4.0 kg | 100 | $22.641 |
| SR-25 | 7.62x51 | 5 | 3.3 kg | 40 | $3.478 |
| Winchester Modelo 70 | .30-06 Springfield | 4 | 3.3 kg | 55 | $972 |
| Remington 700P | .30-06 Springfield | 4 | 3.4 kg | 40 | $8.625 |
| Tikka T3x | 6.5 Creedmoor | 3 | 3.0 kg | 50 | $11.500 |
| Sako 85 | .300 Winchester Magnum | 3 | 3.7 kg | 70 | $14.375 |

### Explosivos (de bolsillo)

| Arma | Capacidad | Peso | Tipo |
|---|---|---|---|
| Cóctel molotov | 1 | 1.0 kg | Arrojadizo incendiario |
