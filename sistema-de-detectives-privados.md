# Sistema de detectives privados

## Introducción

Los **detectives privados** son investigadores civiles con licencia del **San Andreas Association of Licensed Investigators (SAALI)**, capaces de operar con herramientas de vigilancia y espionaje muy similares a las de la policía: micrófonos espía, GPS espía, drones, escuchas telefónicas (StingRay), autoradares y kits de desactivación de bombas.

A diferencia de los agentes del orden, **no están atados al servicio de facción**: un detective privado puede usar su equipamiento en cualquier momento siempre que lo lleve encima, lo que los convierte en una pieza clave del roleplay de investigación, contraespionaje y trabajo encubierto.

Este documento cubre:

- La **licencia de detective** y su equipamiento.
- El **Private Detective Computer (PDC)**.
- Los sistemas de **espionaje**: micrófonos, GPS y drones.
- Las **escuchas telefónicas** con StingRay y los **autoradares**.
- La **detección de señales** y cómo defenderse frente a estos dispositivos.

> Los detectives también disponen de **kits de desactivación de bombas** como parte de su equipamiento. El funcionamiento de las bombas telefónicas y su desactivación está documentado por separado en el **[Sistema de bombas](sistema-de-bombas.md)**.

## Licencia de detective privado

La licencia es asignada por staff especializado del servidor y cuesta **$50.000** (descontados directamente del banco del jugador y depositados al Estado de San Andreas bajo el concepto `LICENCIAS_PRIVADAS`).

Los detectives privados se identifican con una placa oficial:

```
N.º: [ID del personaje]
Placa: San Andreas Association of Licensed Investigators
Detective privado
```

### Comandos básicos del detective

- `/placadet` — muestra tu placa a ti mismo o la enseña a otro jugador cercano (hasta 5 metros).
- `/equipodet` — abre el catálogo de compra de equipamiento en el **Ammu-Nation de Market**.
- `/pdc` — abre el **Private Detective Computer** (requiere tener una laptop en la mano derecha).
- `/informacionbanco` — accede a información bancaria (uso interno del rol de detective).
- `/recogercasquillo`, `/recogersangre` — recogida de evidencias sobre el terreno.
- `/autoradar`, `/interceptarnumero`, `/rastreargps`, `/drone`, `/destruirdrone` — ver secciones específicas más abajo.

## Equipo de detective (Ammu-Nation de Market)

Con `/equipodet` se abre un catálogo exclusivo dentro del Ammu-Nation de Market. Todos los precios son **el doble del coste base** del objeto, y el cobro es directamente del **banco**. Es necesaria licencia de armas para los artículos clasificados como arma.

Equipamiento disponible:

- **Armamento no letal y protección**: cuchillo de hoja fija, porra, spray de pimienta, táser, esposas, chaleco kevlar, escudo, guantes LawPro kevlar, mascarilla, máscara táctica de gas, gafas de visión nocturna.
- **Armas de fuego**: Glock 17, AF-1 Strike One, cargadores 9x19.
- **Herramientas de trabajo**: cámara, linterna, radio UHF, halligan, ganzúas, Super Scanner, kit de reparación de armas, estuche porta rifles.
- **Acreditación**: ID policial propia del detective.
- **Electrónica de vigilancia**:
  - Micrófono espía y receptor/detector de micrófonos.
  - GPS espía y receptor de GPS.
  - StingRay y detector de StingRay.
  - Inhibidor de señales de radio.
  - Kit de desactivación de bombas (objeto 943).
- **Médico / logístico**: medicamentos de detoxicación, Narcan, caja de cartón, bolsa de evidencias, bolsa de cadáveres.

> Durante los **eventos de La Purga** no se puede usar `/equipodet`.

## Private Detective Computer (PDC)

Con una **laptop** en la mano derecha, el comando `/pdc` abre una interfaz equivalente al ordenador policial, pero de pago. Cada consulta cobra directamente del banco del detective:

| Consulta | Precio |
|---|---|
| Buscar información por **nombre** | **$50.000** |
| Buscar información por **matrícula** | **$25.000** |
| Buscar información por **propiedad** | **$10.000** |
| Buscar información por **teléfono** | **$10.000** |
| Buscar información por **serial de arma** | **$50.000** |
| Buscar **armas por propietario** | **$100.000** |

Esto convierte la investigación en una actividad costosa y premia la información verificada, al tiempo que impide el abuso del sistema.

---

## Micrófonos espía 🎤

Los **micrófonos espía** permiten escuchar conversaciones cercanas. Funcionan con tres objetos que se complementan entre sí:

- **Micrófono espía** — se planta en el mundo y capta el audio a su alrededor.
- **Receptor de micrófonos** — permite escuchar los micrófonos activos en un radio amplio.
- **Detector de micrófonos** — permite localizar micrófonos cerca de ti.

### Rangos

- **Radio de captación del micrófono**: **20 metros** al aire libre. Dentro de una propiedad se reduce a **8 metros**, y en conversaciones susurradas/bajas el radio de captación baja a **5 metros**.
- **Radio de escucha del receptor**: **300 metros**.
- **Radio de trabajo del detector**: **10 metros**.
- **Batería del micrófono**: dura aproximadamente **60 minutos** desde que se enciende (pasado ese tiempo el micrófono se apaga automáticamente).

### Cómo se capturan los mensajes

- Cualquier **mensaje IC hablado** por un jugador (habla normal, susurros, `/me`, `/do`, gritos…) dentro del radio del micrófono se reenvía automáticamente a **todos los receptores** encendidos que estén dentro de los 300 metros del micrófono.
- Si el micrófono está **dentro de una propiedad**, los receptores que estén **en el exterior**, cerca de la entrada de esa propiedad (dentro de los 300 metros de la puerta), también reciben el audio — es decir, **no hace falta entrar en la propiedad para escuchar lo que pasa dentro**, lo que permite vigilancia encubierta desde fuera.
- Cada mensaje interceptado aparece con el formato:
  `[Micrófono a X.Xm] #NÚMERO dice: "mensaje"` — donde el número es un identificador anónimo del hablante.

### Comandos de micrófono espía

- `/encendermicrofono` — enciende el micrófono que lleves en la mano derecha y lo deja activo donde lo coloques. **Requiere**: ser detective **o** tener al menos **5 de habilidad de electrónica**.
- `/apagarmicrofono` — apaga un micrófono. **Requiere**: ser detective **o** tener al menos **20 de habilidad de electrónica**.
- `/escucharmicrofono` — activa/desactiva la escucha a través del receptor. **Requiere**: ser detective **o** tener al menos **5 de habilidad de electrónica**. El detector deja de funcionar si el jugador muere o si se saca el receptor de la mano.
- `/detectarmicrofono` — barre el área en busca de micrófonos. **Requiere**: ser detective **o** tener al menos **15 de habilidad de electrónica**. Si se encuentra uno, muestra la **distancia exacta** al dispositivo. **Consume 1 unidad de batería** del detector por uso.

---

## GPS espía 📡

Los **GPS espía** se colocan discretamente en un objetivo (vehículo, bolsa, persona) y permiten seguir su ubicación en el mapa a distancia.

### Rangos

- **Radio de seguimiento del receptor**: **300 metros**.
- **Límite de GPS rastreados simultáneamente**: hasta **5 objetivos** en el mapa a la vez.

### Cómo funciona el rastreo

- Mientras el detective tenga el receptor en la mano derecha, esté **vivo** y haya activado el rastreo, el sistema refresca las ubicaciones cada **0.5 segundos** y coloca un **icono rojo** en el minimapa/mapa por cada GPS dentro de rango.
- Si el receptor se guarda o el personaje muere, el rastreo se interrumpe automáticamente.

### Comando de GPS espía

- `/rastreargps` — activa o desactiva el rastreo. **Requiere** receptor de GPS en la mano derecha y, si no eres detective, al menos **5 de habilidad de electrónica**.

---

## Drones RC 🚁

El sistema de drones permite desplegar un **vehículo RC aéreo** que se pilota desde el asiento trasero de una **Topfun Van (Berkley's RC Van — modelo 459)**. La policía puede además usar el modelo **Enforcer (482)**.

### Requisitos para usar un drone

- Estar **vivo** y no tener ya otro drone activo.
- Estar en el **asiento trasero** de una Topfun Van (o, para cops, también Enforcer).
- No estar en interior ni virtual world especial.
- Cumplir **al menos una** de estas condiciones:
  - Ser **detective privado**, o
  - Ser **policía**, o
  - Tener **70 o más de habilidad de electrónica**, o
  - Tener **premium oro** (o superior).

### Modelos disponibles

- `/drone raider` — Raider (modelo 465).
- `/drone goblin` — Goblin (modelo 501).
- Variantes adicionales (`bandit`, `baron`, `tiger`, `cam`) están reservadas para staff de rango **Lead Admin** o superior.

### Rangos y señal

- **Alcance máximo desde la van**: **150 metros** para civiles/detectives y **300 metros** para policías.
- Se dibuja un **gangzone** alrededor de la van que indica el área operativa del drone, con código de color:
  - 🟢 **Verde** — señal fuerte (primer tercio del rango).
  - 🟡 **Amarillo** — señal media (segundo tercio del rango).
  - 🔴 **Rojo** — señal débil (último tercio del rango).
- Al superar el rango, el drone **pierde señal** y se apaga; si se recupera la distancia, vuelve a encenderse automáticamente.

### Condiciones que destruyen el drone

- Que la **Topfun Van sea destruida**.
- Que el piloto **muera**, **salga del drone** o **cambie a otro interior/virtual world**.
- Que el drone **reciba suficiente daño** (por debajo de 700 de salud, se destruye).
- Usar `/destruirdrone` manualmente devuelve al jugador al asiento trasero de la van.

### Comandos de drone

- `/drone [raider | goblin]` — despliega el drone.
- `/destruirdrone` — destruye el drone activo y devuelve al piloto a la van.

---

## Escuchas telefónicas (StingRay) 📶

La **StingRay** es un dispositivo que, en la mano derecha de su operador, se configura con un **número de teléfono objetivo** y a partir de ese momento intercepta todas las **comunicaciones IC** asociadas a ese número.

### Quién puede usarla

- **Detectives privados**.
- **Policías supervisores** en servicio.
- **Agentes de la JSA** en servicio con rango de supervisor.

El detective privado **no necesita estar en servicio** para usarla; los cops/JSA sí.

### Rangos

- **Radio de captación (la bola de cobertura de la StingRay sobre el mapa)**: **300 metros** alrededor del dispositivo.
- **Radio de emisión del mensaje interceptado**: **10 metros** alrededor de quien lleva la StingRay (cualquiera a ese alcance ve el mensaje).
- Si el operador está dentro de una propiedad, los mensajes solo se transmiten a quien esté **fuera, cerca de la entrada** (dentro de los mismos 300 metros respecto a la puerta).

### Cómo se capturan los mensajes

- Al interceptar, los **SMS y mensajes de voz/texto IC** enviados hacia o desde ese número, y cuyo emisor esté dentro de los 300 metros de la StingRay, aparecen en el chat del operador (y de quien esté a ≤10 m de él) con el formato:
  `[StingRay] Tlf. NÚMERO_EMISOR: "mensaje"`.
- El número introducido debe estar entre `0` y `999999999`.

### Comando

- `/interceptarnumero [número]` — configura la StingRay para interceptar ese teléfono. Debe llevarse la StingRay en la mano derecha.

---

## Autoradares de vehículo 🚐

Los **autoradares** convierten ciertos vehículos en unidades de **vigilancia de comunicaciones** por radio/celular cercanas. Funcionan como un "escáner" móvil que pasa los mensajes interceptados al interior del vehículo.

### Quién puede instalar un autoradar

- **Detectives privados**.
- **Supervisores de policía** en servicio.
- **Supervisores de JSA** en servicio.

### Vehículos compatibles

- **Boxville** (modelos 498 y 609) — cualquier autorizado.
- **Newsvan** (modelo 582) — cualquier autorizado.
- **Enforcer** (modelo 482) — **solo policías**.

Se requiere una **laptop en la mano derecha** y ser **conductor** del vehículo para instalar o desinstalar el autoradar. El mismo comando instala y desinstala según el estado actual.

### Rango y funcionamiento

- **Radio de intercepción**: **300 metros** alrededor del vehículo.
- Los mensajes cazados se muestran únicamente a los **ocupantes del vehículo** con el formato:
  `[Distancia X.Xm] #NÚMERO dice: "mensaje"`.

### Comandos

- `/autoradar` — instala/desinstala el autoradar en el vehículo que conduces.

---

## Contramedidas: detección de señales

Los civiles y criminales también pueden defenderse. Con un **detector de receptores de señal** en la mano derecha se puede barrer el entorno.

### Requisitos

- Detector de receptores de señal en la mano derecha (tiene batería limitada; se consume 1 unidad por uso y al llegar a 0 se apaga).
- Ser **detective** **o** tener al menos **15 de habilidad de electrónica**.

### Resultado del barrido (`/detectarsenal` o `/detectarseñal`)

La detección informa en mensajes diferenciados por color:

1. Si hay un **autoradar activo** dentro de los 300 metros (prioritario):
   - ✅ *"Has detectado una alteración **fuerte** en las señales de teléfono."*
2. Si hay una **StingRay operativa** dentro de los 300 metros:
   - ✅ *"Has detectado una alteración **mediana** en las señales de teléfono."*
3. Si **no hay ninguna señal activa**, el resultado es ambiguo — se reparte al azar a medias:
   - **50 % de probabilidad** de recibir un falso positivo: *"Has detectado una alteración **débil** en las señales de teléfono."*
   - **50 % de probabilidad** de recibir la lectura limpia: *"No has detectado ningún receptor de señal."*

Este ruido intencionado evita que el detector sea 100 % fiable para confirmar que la zona está limpia.

---

## Resumen de comandos del sistema

| Comando | Rol que lo usa | Qué hace |
|---|---|---|
| `/placadet` | Detective | Mostrar la placa SAALI. |
| `/equipodet` | Detective | Comprar equipamiento en el Ammu-Nation de Market. |
| `/pdc` | Detective | Abrir el Private Detective Computer con laptop. |
| `/encendermicrofono` / `/apagarmicrofono` | Detective o electrónica ≥5 / ≥20 | Activar o apagar un micrófono espía. |
| `/escucharmicrofono` | Detective o electrónica ≥5 | Escuchar todos los micrófonos cercanos por receptor. |
| `/detectarmicrofono` | Detective o electrónica ≥15 | Localizar micrófonos en un radio de 10 m. |
| `/rastreargps` | Detective o electrónica ≥5 | Rastrear hasta 5 GPS espía en un radio de 300 m. |
| `/drone raider` / `/drone goblin` | Detective, cop, electrónica ≥70 o premium oro | Desplegar un drone RC desde una Topfun Van. |
| `/destruirdrone` | Dueño del drone | Recoger el drone y volver a la van. |
| `/interceptarnumero [número]` | Detective, cop supervisor en servicio o JSA supervisor en servicio | Configurar la StingRay para interceptar un teléfono. |
| `/autoradar` | Detective, cop supervisor en servicio o JSA supervisor en servicio | Instalar/desinstalar el autoradar del vehículo. |
| `/detectarsenal` | Detective o electrónica ≥15 | Detectar StingRays y autoradares cercanos. |

> **Aviso de roleplay:** el equipamiento de detective es potente y puede desequilibrar situaciones si se abusa. Úsalo como parte de investigaciones creíbles, respeta el /b y el metagame, y recuerda que **las contramedidas (detectores) existen precisamente para dar contrajuego al bando vigilado**.
