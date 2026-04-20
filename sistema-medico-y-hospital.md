# Sistema de enfermedades, cirugías y hospital

## Introducción

El sistema médico integra tres piezas del servidor: la **facción del hospital**, los **eventos médicos (enfermedades)** y las **cirugías**. Todo gira en torno al **All Saints General Hospital**, ubicado en Market, Los Santos.

La facción del hospital provee **atención primaria de urgencias**, **consultas médicas**, **cirugías estéticas u operaciones** y respuesta privada a accidentes. El sistema genera ganancias para la facción y para el gobierno según quién atiende y quién paga.

## All Saints General Hospital

El hospital es el centro sanitario principal del servidor. Funciona con dos figuras jerárquicas:

- **Paramédicos** — atienden en exteriores (reanimaciones, vendajes, traslados).
- **Médicos residentes** — personal interno del hospital con acceso a consultas médicas y cirugías.

La presencia de residentes conectados **dentro del perímetro del hospital** (radio de 100 metros respecto al mostrador de urgencias) cambia el comportamiento del sistema:

| Residentes en servicio dentro del hospital | Comportamiento de `/curarme`                                                          |
| ------------------------------------------ | ------------------------------------------------------------------------------------- |
| **0 – 1**                                  | Teletransporta al paciente a una cama de urgencias y lo cura automáticamente.         |
| **≥ 2**                                    | En lugar de curar, envía una alerta de socorro a los médicos para un atendimiento IC. |

Cuando hay ≥ 2 residentes, cada uso de `/curarme` tiene un **cooldown de 60 segundos** por paciente.

### Costes de urgencias

El importe del `/curarme` varía según el residente presente y la residencia del paciente:

| Situación                                                | Precio           | Quién paga                                                  |
| -------------------------------------------------------- | ---------------- | ----------------------------------------------------------- |
| Paciente con casa en Los Santos, 0–1 residente activo    | **$2.500**       | El paciente                                                 |
| Paciente con casa en Los Santos, ≥ 2 residentes activos  | **$5.000**       | El paciente                                                 |
| Paciente **sin residencia** en Los Santos                | **$5.000**       | Fondos del gobierno                                         |
| Paciente **funcionario público** en servicio             | Precio aplicable | Fondos del gobierno                                         |
| Empleado en servicio en un **negocio con seguro médico** | Cubierto         | La empresa empleadora                                       |

Si hay **al menos 1 residente conectado**, el importe pagado por el paciente ingresa a la caja de la facción del hospital. Si no hay residentes, el dinero no genera ingresos a la facción.

### Comandos

- /curarme — solicita atención de urgencias en el mostrador del hospital.
- /llevarhospital [id] — (solo policías en servicio, si no hay paramédicos conectados) traslada a un personaje muerto al hospital.
- /paramedicos — muestra cuántos paramédicos y residentes hay de servicio. Alias: `/mds`.

## Sistema de eventos médicos

Cada vez que un personaje logueaua en el servidor hay una **probabilidad aleatoria (~4 %)** de que se le ofrezca participar en un evento médico. El jugador puede:

- **Aceptar** el evento y elegir una de las 5 enfermedades sorteadas en la lista.
- **Rechazar** cerrando la ventana.
- **Forzar** una enfermedad en cualquier momento con `/enfermarme`.

La base de datos del servidor incluye más de **60 enfermedades** distintas, cada una con:

- Una **descripción** corta.
- Una lista de **tres síntomas** visibles en `/mirar`.
- Una **duración** expresada en horas reales desde que comenzó.
- Unos **efectos mecánicos** opcionales (mareos, vómitos, tos, estornudos, alucinaciones, puntería reducida, imposibilidad de saltar).

### Efectos sobre el personaje

- **Tos** — genera un `/ame` "tose" con **33 %** de probabilidad; en el 67 % restante se muestra como burbuja de chat. Se acompaña de un efecto de sonido audible en 10 m.
- **Estornudo** — `/ame` "estornuda" con **20 %** de probabilidad; el resto, burbuja. La loratadina anula el síntoma.
- **Síntomas tipo "rotura de brazo"** — bajan la puntería con armas de fuego al mínimo.
- **Síntomas tipo "esguince de tobillo"** — impiden correr y saltar.
- **Otros** — mareos, vómitos y alucinaciones visuales.

### Ejemplos de enfermedades

| Enfermedad         | Descripción                             | Duración |
| ------------------ | --------------------------------------- | -------- |
| Calambre muscular  | Contracción involuntaria de un músculo. | 2 horas  |
| Dolor de estómago  | Malestar abdominal temporal.            | 8 horas  |
| Conjuntivitis      | Inflamación de la membrana ocular.      | 16 horas |
| Golpe en la cabeza | Contusión leve por impacto.             | 12 horas |

Los síntomas activos son visibles para otros personajes mediante el comando `/mirar`.

### Comandos

- /enfermarme — fuerza el diálogo de selección de evento médico.
- /mirar [id] — inspecciona a otro personaje y, si está enfermo, ve sus síntomas.

## Tratamiento y medicamentos

El personal médico del hospital puede tratar una enfermedad con una **consulta médica** (`/consultamedica`). Además, el servidor incluye medicamentos que actúan directamente sobre algunos síntomas:

| Medicamento | Función                               |
| ----------- | ------------------------------------- |
| Paracetamol | Analgésico / antifebril               |
| Ibuprofeno  | Antiinflamatorio                      |
| Amoxicilina | Antibiótico                           |
| Omeprazol   | Antiácido                             |
| Losartán    | Hipertensión                          |
| Metformina  | Diabetes                              |
| Salbutamol  | Trata la tos (elimina síntomas)       |
| Loratadina  | Antialérgico (anula estornudos)       |
| Codeína     | Analgésico opioide (elimina síntomas) |
| Diclofenaco | Analgésico / antiinflamatorio         |

**Salbutamol** y **Codeína** bloquean la eliminación estándar de síntomas en una consulta médica mientras están activos en el cuerpo del paciente.

### Consulta médica

- /consultamedica [id] [precio] — ofrece una consulta médica. Restringido a **paramédicos / residentes en servicio**. Precio entre **$1.000** y **$100.000**. El paciente acepta o rechaza con `/aceptar` o `/rechazar`.

Tras aceptar:

- El paciente paga el precio completo de su cuenta bancaria.
- El médico recibe **50 %** del importe en su cuenta personal.
- La facción del hospital recibe el otro **50 %** en su caja.
- Los síntomas y el estado de enfermedad se eliminan (salvo los bloqueos por salbutamol o codeína).

## Sistema de cirugías

Los paramédicos y residentes pueden realizar **cirugías estéticas, operaciones o cualquier intervención** que deje una marca permanente en el personaje paciente. La descripción se adjunta al `/mirar` del paciente y se muestra con color destacado.

### Requisitos para operar

- Estar en servicio (`/servicio`).
- Llevar un **bisturí** en la mano derecha.
- Estar a **≤ 3 metros** del paciente.

### Proceso

1. El médico ejecuta `/cirugia [id] [precio]` con el paciente a la vista.
2. Se abre un diálogo donde el médico escribe la **descripción de la cirugía** (entre **10 y 128 caracteres**).
3. El paciente recibe la oferta con la descripción y acepta con `/aceptar` o rechaza con `/rechazar`.
4. Al aceptar:
   - El paciente paga el precio completo.
   - El médico recibe el **50 %** en su cuenta personal.
   - La facción del hospital recibe el **50 %** en su caja.
   - La descripción se guarda de forma permanente en el personaje y se muestra destacada en su `/mirar`.

El rango de precios de la cirugía es **$1.000 – $1.000.000**.

### Comandos

- /cirugia [id] [precio] — realiza una cirugía a un paciente. Solo paramédicos / residentes en servicio con bisturí en mano.
