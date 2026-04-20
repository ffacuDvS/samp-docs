# Sistema de skimming

## Introducción

Los **skimmers** son dispositivos electrónicos maliciosos que los delincuentes utilizan para robar información de las tarjetas bancarias en los cajeros automáticos. El funcionamiento del sistema es simple: en vista de que no existe un sistema de tarjetas de crédito, el robo opera sobre las **transacciones que se hagan en los cajeros automáticos** y sumará dinero a la cuenta del delincuente una vez que retire el skimmer del cajero.

Se requiere un mínimo de **50 de habilidad de delincuente** para instalar skimmers y un mínimo de **50 de habilidad de electrónica** para fabricarlos.

## ¿Cómo consigo un dispositivo skimmer?

Los miembros de **facciones ilegales oficiales** pueden fabricar skimmers en el juego siempre que cumplan los requisitos técnicos. El comando `/skimmer` crea un skimmer y lo coloca en la mano derecha del personaje.

Requisitos para fabricar un skimmer:

- Ser miembro de una **facción ilegal oficial**.
- Tener al menos **50 de habilidad de electrónica**.
- Tener una **laptop en la mano izquierda**.
- Tener la **mano derecha libre**.
- Disponer de **$5.000** en efectivo (coste de fabricación).

Los miembros de facciones destacadas también pueden solicitar este dispositivo al **Faction Team**, siempre que presenten una justificación adecuada que respalde el perfil de su personaje como ciberdelincuente.

### Comandos

- /skimmer — fabrica un skimmer (requiere laptop en mano izquierda, mano derecha libre y $5.000).

## Instalación

Para instalar un skimmer, sostén el dispositivo electrónico en la **mano derecha** y acércate a un cajero automático que no haya sido manipulado previamente.

El proceso se compone de dos pasos obligatorios:

1. **Revisar el cajero** con `/revisarcajero` para confirmar que no tiene otro skimmer ya instalado.
2. **Instalar el skimmer** con `/instalarskimmer` en el mismo cajero revisado.

La instalación dura **90 segundos** durante los cuales el personaje debe permanecer junto al cajero y con vida. Si te alejas, pierdes el skimmer de la mano o mueres, la instalación se cancela.

Al instalar, el sistema genera la **calidad del skimmer** (valor entre 0 y 100). La calidad se calcula como `habilidad de electrónica + random(0-29)`, con tope de 100. Al finalizar, el personaje recibe entre **0 y 2 puntos** de habilidad de electrónica.

Restricciones de instalación:

- Requiere **50 de habilidad de delincuente**.
- El cajero **no debe tener otro skimmer** ya instalado.
- Debes haber ejecutado `/revisarcajero` previamente sobre ese mismo cajero.

### Comandos

- /revisarcajero — inspecciona el cajero automático (5 segundos, requiere 5 de habilidad de electrónica).
- /instalarskimmer — instala el skimmer que llevas en la mano derecha (90 segundos).

## Detección

La detección de skimmers **no es tan fácil ni evidente** como en la vida real: el sistema busca equilibrar el juego para que la mayoría de los usuarios no detecten la instalación de estos dispositivos. Los usuarios deben mejorar su **habilidad de electrónica** antes de intentar detectar un skimmer.

El comando `/revisarcajero` ejecuta una animación de 5 segundos y calcula un chequeo aleatorio:

- Se genera un número aleatorio entre **0 y 100**.
- El umbral de éxito es `(habilidad de electrónica + calidad del skimmer) / 2`.
- Si el número aleatorio es **menor o igual** al umbral, detectas el skimmer.

Esto significa que skimmers de **mayor calidad** son más difíciles de detectar para jugadores con poca habilidad de electrónica, y más fáciles para quienes tengan mucha habilidad.

Detectan el skimmer **automáticamente** (sin chequeo aleatorio):

- El propio dueño del skimmer.
- Los **técnicos de seguridad** en servicio.
- Los **administradores** en modo servicio.

### Técnicos de seguridad

Los técnicos de seguridad en servicio pueden localizar cajeros marcados por la inspección municipal mediante `/marcarcajero` (radio de 50 m). Este comando sólo detecta cajeros con **skimmer instalado**, y queda registrado en un checkpoint en pantalla.

Al retirar un skimmer como técnico de seguridad en servicio, la ciudad paga **$5.000** al técnico y descuenta **$50.000** del banco del Gobierno (los $5.000 del sueldo más $45.000 de multa).

### Comandos

- /marcarcajero — localiza el cajero con skimmer más cercano (sólo técnicos de seguridad en servicio).
- /revisarcajero — revisa un cajero para detectar si tiene un skimmer instalado.

## Ganancias

En cada transacción realizada en el cajero automático (retiros y depósitos), el skimmer descuenta una pequeña porción al cliente. El dinero descontado se **acumula en el skimmer** y se transfiere a la cuenta bancaria del delincuente al retirar el dispositivo.

El porcentaje robado por transacción depende de la **calidad del skimmer** y escala de forma lineal:

| Calidad | Porcentaje de la transacción |
|---------|------------------------------|
| 0 | 3% |
| 50 | 7,5% |
| 100 | 12% |

Fórmula: `0,03 + (calidad × 0,0009)`.

El dinero se descuenta directamente de la **cuenta bancaria** del cliente que realiza la transacción, no de sus manos.

El dinero acumulado en el skimmer únicamente se otorgará al **dueño del dispositivo** (el personaje que lo instaló). **No es posible robar las ganancias del skimmer a otro ciberdelincuente**: si otro delincuente, un policía o un técnico de seguridad retira el skimmer, no recibe el dinero acumulado.

## Retirada del skimmer

Para recoger las ganancias, el dueño debe volver al cajero y usar `/retirarskimmer`. El proceso dura **60 segundos** y requiere permanecer junto al cajero y con vida.

Al finalizar, el dinero acumulado se **transfiere a la cuenta bancaria** del dueño del skimmer y el dispositivo es destruido. El personaje recibe entre **0 y 4 puntos** de habilidad de electrónica.

Restricciones para retirar:

- Sólo el **dueño del skimmer**, **policías**, **técnicos de seguridad** o **administradores en servicio** pueden retirar.
- Requiere **50 de habilidad de delincuente** (salvo policías y técnicos de seguridad).
- Debes haber usado `/revisarcajero` sobre ese cajero previamente.

### Comandos

- /retirarskimmer — retira el skimmer del cajero (60 segundos).
