# Sistema forense

## Introducción

El sistema forense es esencial en la investigación de crímenes ya que proporciona pruebas tangibles y científicas que pueden ayudar a identificar a los sospechosos, establecer las causas de muertes y apoyar la acusación en un juicio.

En el roleplay policial y criminal, la inclusión de estas herramientas y técnicas forenses agrega un nivel adicional de realismo y autenticidad a la historia. Al incorporar la recopilación y análisis de evidencia en la narrativa, los jugadores pueden sumergirse en las persecuciones policiales y explorar la complejidad de la investigación criminal.

---

## 1. Casquillos de bala

Los casquillos se crean cada vez que alguien dispara un arma. Existen **tres modelos 0.3 DL** distintos que aparecen en el piso:

- Casquillos de **pistola**.
- Casquillos de **rifle**.
- **Cartuchos de escopeta**.

En cada **reinicio diario del servidor**, los casquillos que permanezcan en el suelo son eliminados automáticamente.

### Examen de casquillos

Al examinar un casquillo se revelan dos datos importantes sobre la escena del crimen:

- **Temperatura:** comienza alrededor de los **370 °C** y desciende hasta la temperatura ambiente con una tasa decreciente. Un casquillo tarda aproximadamente **10 minutos** en enfriarse del todo, lo que permite **cronometrar escenas** y estimar cuándo se produjo el disparo.
- **Estado del casquillo:** se aleatoriza en cada disparo y puede ser:
  - **Destruido**
  - **Severamente dañado**
  - **Bueno**
  - **Excelente**

El estado es determinante a la hora de analizarlo en el laboratorio forense.

### Recolección de casquillos

Los casquillos **solo pueden ser recogidos** por:

- Jugadores con al menos **30 de habilidad de delincuente**.
- **Agentes de la ley (policías).**

Esta restricción evita que cualquier criminal sin experiencia pueda limpiar escenas del crimen con total facilidad.

> 💡 **Casquillos calientes:** si un casquillo todavía no se ha enfriado, es obligatorio usar **guantes** para recogerlo. De lo contrario, el sistema no permitirá la acción.

### Comandos

- `/casquillo` — examina el casquillo que tengas en la **mano derecha** (muestra temperatura y estado).
- `/recogercasquillo` — recoge el casquillo **más cercano**.
- `/aborrarcasquillo` _(ADMIN)_ — elimina el casquillo más cercano.

---

## 2. Manchas de sangre

Las manchas de sangre se crean automáticamente cuando:

- Una persona es **herida gravemente** por una puñalada o un disparo.
- Se activa el **sistema de desangrado** sobre un jugador herido.

Utilizan el **modelo 0.3.7 de sangre** y pueden **acumularse** en un mismo lugar si varias heridas se producen en la misma zona.

En cada **reinicio diario del servidor**, las manchas de sangre que queden en el suelo son eliminadas automáticamente.

### Recolección de muestras de sangre

Las muestras de sangre **solo pueden ser recolectadas** por **policías o detectives**.

### Comandos

- `/recogersangre` — recoge la mancha de sangre más cercana en forma de muestra.
- `/aborrarsangre` _(ADMIN)_ — elimina la mancha de sangre más cercana.

---

## 3. Pruebas de ADN

Una muestra de sangre **no identifica automáticamente** a una persona: el sistema necesita una **prueba de ADN previamente registrada** en los archivos para poder cruzar la información.

Las pruebas de ADN se registran en dos situaciones:

- **Automáticamente**, al ingresar al **Twin Towers Correctional Facility**.
- **Manualmente**, cuando un **agente de la ley solicita** realizar una prueba a un sospechoso.

> ⚖️ Los jugadores que **no tengan prueba de ADN registrada** no podrán ser identificados de ninguna manera a partir de su sangre. De esta forma, el **MetaGaming** por parte de los agentes de la ley resulta imposible.

### Comandos

- `/pruebaadn [jugador]` — solicita realizar una prueba de ADN a un sospechoso.

---

## 4. Huellas dactilares

Cada objeto del sistema de inventario **almacena las huellas** de todos los portadores que lo han tenido en sus manos a lo largo de su vida útil. Es posible **evitar ensuciar un objeto** con huellas usando **guantes desechables** al manipularlo.

### Limpieza de huellas

Las huellas de un objeto pueden limpiarse con **alcohol isopropílico**. La acción fuerza una **animación de 30 segundos** y tiene las siguientes probabilidades:

| Resultado                | Probabilidad |
| ------------------------ | ------------ |
| No limpia ninguna huella | **40%**      |
| Limpia una huella        | **30%**      |
| Limpia dos huellas       | **20%**      |
| Limpia tres huellas      | **10%**      |

Cada uso del comando **consume 3 unidades** de alcohol isopropílico.

### Comandos

- `/limpiarhuellas` — limpia las huellas dactilares del objeto que lleves en la **mano derecha**.

---

## 5. Almacén de evidencias

Las **agencias de la ley** disponen de un **almacén de evidencias con capacidad ilimitada** dentro de sus propiedades de facción. En él se **guardan, examinan y registran** las bolsas de evidencias.

Los almacenes son **independientes por facción**: cada agencia gestiona su propio archivo de pruebas.

### Etiquetado obligatorio

Antes de guardar una bolsa en el almacén, **debe etiquetarse** siguiendo los formatos normalizados de cada facción. Esto permite llevar un orden claro en las investigaciones y localizar las evidencias posteriormente.

### Búsqueda de evidencias

Las evidencias dentro del almacén pueden buscarse por:

- **Etiqueta** (texto).
- **Fecha de creación.**
- **Número identificador (#ID).**

### Bitácora de registros

Cada **movimiento** realizado sobre una evidencia (guardar, sacar, examinar, etc.) queda registrado en la **bitácora propia** de esa evidencia, junto con el agente responsable y la fecha.

### Comandos

- `/evidencias buscar [etiqueta, fecha o #id]` — busca una evidencia en el almacén.
- `/evidencias sacar [#id]` — saca una evidencia del almacén.
- `/evidencias guardar` — guarda en el almacén la bolsa de evidencias de la mano derecha.
- `/evidencias bitácora [#id]` — muestra la bitácora de registros de una evidencia.
- `/etiqueta` — añade una etiqueta a la bolsa de evidencias de la mano derecha.

---

## 6. Laboratorio forense

El laboratorio forense permite analizar el contenido de las bolsas de evidencias guardadas en el almacén. Se pueden examinar **muestras de sangre**, **casquillos** y **objetos** empaquetados como evidencia.

### Examen de casquillos

Las bases de datos de balística de Estados Unidos almacenan las **estrías y marcas únicas** de cada casquillo, lo que permite asociar un casquillo disparado a un arma mediante su **registro seriado**.

Los resultados del examen dependen del **estado del casquillo**:

| Estado                 | Resultado en el examen                  |
| ---------------------- | --------------------------------------- |
| **Destruido**          | Se descarta automáticamente.            |
| **Severamente dañado** | **75%** de probabilidad de descartarse. |
| **Bueno**              | Pasa el examen.                         |
| **Excelente**          | Pasa el examen.                         |

> 🔍 Cuantos **más casquillos** se adjunten a una bolsa de evidencias, **mayor probabilidad** hay de conseguir una coincidencia con el arma disparadora.

Si un casquillo fue percutado por un **arma fantasma** (no registrada), la balística solo podrá determinar el **modelo del arma**, nunca su serial.

### Examen de muestras de sangre

Las muestras de sangre se comparan contra las **pruebas de ADN registradas** previamente en el sistema.

Si el sospechoso **no tiene una prueba de ADN registrada**, no será posible identificarlo por este medio.

### Examen de huellas dactilares

El examen forense identifica a **cada uno de los usuarios** que hayan tocado la evidencia. A diferencia del ADN, **no existe forma de evitar ser identificado por huellas** una vez que estas quedan en el objeto (salvo limpiándolas con antelación).

### Reporte forense

Los exámenes forenses solicitados por los agentes **no son inmediatos**: los resultados se entregan **una hora después** de utilizar el comando. Este retraso simula el tiempo real de un análisis y da **margen narrativo** entre la investigación policial y la posible reacción de los criminales.

### Comandos

- `/evidencias examinar [#id]` — envía la evidencia al laboratorio forense para su análisis.
- `/evidencias resultados [#id]` — muestra los resultados del examen forense.
- `/mostrarevidencias [jugador] [#id]` _(FISCALES Y JUECES)_ — muestra los resultados del reporte forense a otro jugador cercano.

---

> 📌 **Recordatorio:** el sistema forense está diseñado para enriquecer el roleplay policial y criminal. Aprovéchalo para construir investigaciones realistas, limpiar escenas con cuidado y sostener acusaciones con pruebas científicas antes de un juicio.
