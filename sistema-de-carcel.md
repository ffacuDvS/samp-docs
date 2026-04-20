# Sistema de cárcel

## Introducción

En el servidor, la cárcel representa fielmente una **cárcel del condado**, sin confundirla con prisiones federales o estatales. Para efectos prácticos en SARP, **prisión y cárcel son lo mismo**: ambos términos se refieren a la Twin Towers Correctional Facility.

Dentro de Twin Towers conviven dos tipos de reclusos:

- **Condenados** — personajes ya sentenciados cumpliendo su condena.
- **Internos a la espera de juicio** — personajes en prisión preventiva mientras se resuelve su caso.

La cárcel está administrada por el **Los Santos County Sheriff's Department (LSSD)** o, según la disponibilidad, por el **San Andreas Department of Corrections and Rehabilitation (SADCR)**.

La cárcel del condado contempla secciones únicamente para hombres. Las mujeres cumplen condena en la cárcel de la estación del sheriff.

Los arrestos que hagan Los Santos Police Department, Los Santos County Sheriff's Department o agencias del Department of Justice trasladan a los reclusos automáticamente a la **Twin Towers Correctional Facility**.

### Comandos

- /tiempocarcel — muestra cuántas horas te quedan de condena.
- /salircarcel — sales de la cárcel cuando se ha cumplido tu condena. Alias: `/salirprision`.
- /uniformecarcel — cambia tu uniforme de interno (solo hombres).

## Twin Towers Correctional Facility

La **Twin Towers Correctional Facility** (o _Twin Towers Jail_) es el complejo carcelario del condado de Los Santos, ubicado en **934 Artesina Avenue**. Consta de dos torres, un edificio de servicios médicos y la cárcel del Los Santos County Medical Center.

Inaugurado en **1997**, el complejo de 140.000 m² tardó en abrir por falta de fondos operativos. Su diseño de seguridad es **panóptico**: los agentes en una sala de control central pueden observar todas las áreas del recinto a través de material óptico seguro.

En mayo de 2013, junto con la Men's Central Jail adyacente, fue clasificada como **una de las diez peores cárceles de condado de Estados Unidos** (informe de Mother Jones / ACLU), con quejas por hacinamiento, ataques de agentes a reclusos y abuso de drogas psiquiátricas para controlar presos.

### Secciones

El edificio alberga dos secciones de reclusos:

- **187-A-POD** (lado izquierdo).
- **187-B-POD** (lado derecho).

Cada sección tiene exactamente **12 celdas**, numeradas del 1 al 12 por sección. Las celdas se abren automáticamente en cada reinicio del servidor, y **solo los ayudantes del sheriff** pueden cerrarlas desde el panel de control.

### Celdas

Cada celda está equipada con un camarote de dos camas, un estante para objetos personales, un retrete y un escritorio empotrado. En futuras actualizaciones se implementará un **inventario personal** dentro de la celda asignada.

## Pasillo de servicios

El pasillo del sector 1 da acceso a los servicios básicos de la cárcel: **cafetería, gimnasio, librería, iglesia y lavandería**. Este pasillo se abre y cierra automáticamente **cada hora** de servidor.

### Cafetería

Los internos pueden entregar **bandejas de comida** a otros reclusos desde la cafetería. El interno receptor debe aceptar la bandeja. No puedes comer si ya lo has hecho recientemente, ni recibir comida con las manos ocupadas.

En próximas actualizaciones la cafetería funcionará también como espacio de trabajo en la cocina.

### Gimnasio, librería, iglesia y lavandería

Espacios del recinto destinados a roleplay. Están preparados para futuras funcionalidades: entrenamiento en el gimnasio, lectura de libros y desarrollo de habilidades en la librería, lavado de uniformes y generación de ingresos en la lavandería.

### Comandos

- /cafeteria [id] — entrega una bandeja de comida a otro interno (dentro del puesto de cafetería).

## Avisar a los deputies

Cuando pasa algo dentro de la cárcel y no hay deputies presentes, los internos pueden avisar al **LSSD** de dos formas:

- **Evento de cárcel**: envías una descripción detallada del entorno y los personajes involucrados (celda, módulo, vestimenta, etnia…) a todos los deputies, incluso desconectados. Máximo **128 caracteres**. Cooldown de **30 minutos**. No abuses o puedes ser sancionado.
- **Solicitud de deputies**: avisas por radio a los deputies de que hay un incidente en Twin Towers, indicando el motivo. Cooldown de **10 minutos**.

Solo disponibles para **internos hombres** (las mujeres no están asignadas en Twin Towers).

### Comandos

- /eventocarcel — envía una alerta de evento carcelario a los deputies de LSSD (cooldown 30 min).
- /solicitardeputies [razón] — solicita la presencia de deputies en la cárcel (cooldown 10 min).

## Quiosco de la cárcel

Dentro del recinto hay un **quiosco (commissary)** donde los internos pueden comprar artículos básicos: papel higiénico, rollo de gasa, jabón, crema, etc. Los precios están fijados por el sistema.

### Comandos

- /quioscocarcel — abre el menú del quiosco. Alias: `/quiosco`, `/quioscoc`.

## Confinamiento y aislamiento

En la sección de **confinamiento** se encuentran los reclusos aislados por mal comportamiento o agresividad. Solo los agentes del **Los Santos County Sheriff's Department** pueden trasladar internos a esta sección.

Los reclusos que **abatan a otro interno** reciben automáticamente **+60 minutos** de condena, ya que la cárcel es un nicho de roleplay, no una zona off-rol.

## Patio

Aunque la Twin Towers no tiene patio en la vida real, en el servidor se implementó para romper la monotonía y generar roles interesantes. A diferencia del pasillo de servicios, el patio **no se abre automáticamente**: depende de la actividad del Los Santos County Sheriff's Department.

El patio está equipado con una **cancha de baloncesto**, un **quiosco**, estructuras para **gimnasia** y **tres secciones de mesas**.

## Centro médico

La cárcel cuenta con una sección médica equipada con **seis camas de cuidados intensivos** y un **módulo de enfermería**.

## Control de acceso

El panel de control de accesos está en la sala de control dentro de las secciones. Desde ahí los ayudantes del sheriff controlan todas las secciones de la cárcel y cada celda individualmente, usando como referencia la **sección** (A o B) y el **número de celda** (1-12).

## Condenas

Las condenas de tiempo y multa están expuestas en el **código penal** disponible en el PCU. Puntos clave:

- El **límite máximo** de cárcel es de **360 minutos (6 horas)**, considerando que la mayoría del tiempo la cárcel no tiene rol activo. Este límite puede modificarse según la actividad.
- El tiempo de cárcel **no pasa el doble de rápido**.
- El tiempo de cárcel **no pasa desconectado**: debes estar en el juego para cumplir condena.

## Libertad condicional

Al salir de la cárcel, el juez puede asignarte **libertad condicional** (parole). Durante ese periodo debes cumplir una serie de reglas estrictas (informar domicilio y trabajo, no poseer armas, no salir del condado sin permiso, obedecer toda instrucción verbal o escrita, etc.). Romper cualquiera de esas reglas puede devolverte a la cárcel sin necesidad de un nuevo caso penal.

Los parolees pueden solicitar un oficial de libertad condicional cada **15 minutos** para cuestiones relacionadas con su situación.

Cuando vence el plazo, debes terminar voluntariamente la condicional para quitarte la tobillera.

### Comandos

- /reglasparole — muestra las 15 reglas oficiales de la libertad condicional. Alias: `/reglasp`.
- /tiempoparole — muestra cuánto tiempo te queda de condicional. Alias: `/tiempop`.
- /solicitaroficialparole — solicita la presencia de un oficial de libertad condicional (cooldown 15 min).
- /terminarparole — da por finalizada tu condicional al expirar el plazo. Alias: `/terminarp`.

## Personajes en perpetua

Los personajes que deseen ingresar **permanentemente** a la cárcel (para roles de Mafia Mexicana, PEN1 u otras facciones carcelarias) pueden hacerlo entrando por el acceso principal y usando `/encarcelarme`.

La perpetua implica una condena de **3 meses (2190 horas)** y **no es reversible** por la administración. Las únicas formas de salir son:

- Cumplir los 3 meses completos.
- Solicitar un **Character Kill** del personaje.

Al elegir perpetua no habrá arrepentimientos ni devoluciones por el tiempo cumplido.

### Comandos

- /encarcelarme — entra voluntariamente a la cárcel con condena de 3 meses (junto a la entrada principal).
