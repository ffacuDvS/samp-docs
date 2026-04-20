# Sistema de propiedades

## Introducción

El sistema de propiedades agrupa todos los inmuebles del servidor: **casas**, **almacenes**, **negocios**, **complejos hoteleros** e **industrias**. Los jugadores pueden comprar, vender, alquilar, amueblar y administrar propiedades, además de prestar llaves y contratar empleados para convertirlas en verdaderos negocios.

<img width="376" height="52" alt="image" src="https://github.com/user-attachments/assets/81baa9c4-2129-48af-a974-8dfe59c7b4c7" />

Todas las propiedades pagan **servicios de electricidad y agua**. El coste se calcula **por hora y por cada jugador** que permanece dentro, y se descuenta directamente al dueño en su **payday**. Cuantos más ocupantes y más tiempo pasen dentro, mayor será la factura.

### Comandos

- /entrar — entra a la propiedad en cuyo marcador de entrada te encuentras.
- /salir — sale de la propiedad por el marcador de salida.
- /puerta — abre o cierra la puerta (dentro de la propiedad, cerca de una puerta).
- /info — muestra información general de la propiedad en la que estás.
- /timbre — toca el timbre para avisar a los ocupantes.
- /visitar — solicita visitar una propiedad cerrada.
- /metermoto — introduce una motocicleta a la propiedad (si la entrada lo permite).
- /phora [0-23] — establece una hora personalizada en el interior (dueño).
- /pclima [0-20] — establece un clima personalizado en el interior (dueño).

## Muebles

Los muebles son objetos que puedes comprar y colocar libremente dentro de tu propiedad para decorarla o darle funcionalidad (camas, sofás, luces, puertas adicionales, etc.). Puedes moverlos, rotarlos, clonarlos, aplicarles texturas y hasta convertir algunos en puertas funcionales.

El flujo típico: compras un mueble con `/comprarmueble`, lo seleccionas con `/seleccionar`, entras en modo edición con `/editarmueble`, lo mueves o rotas con los comandos de ejes, y lo dejas fijo al deseleccionarlo.

<img width="663" height="636" alt="image" src="https://github.com/user-attachments/assets/f6367168-f714-453b-be9f-e7e3af42bbfe" />

### Comandos

- /comprarmueble [modelo] — compra un mueble (sin parámetros muestra categorías). Alias: `/cobject`, `/comprarmuebles`.
- /muebles — lista los muebles de la propiedad actual.
- /buscarmueble [nombre] — busca muebles disponibles por nombre.
- /seleccionar — selecciona el mueble más cercano para editar.
- /cseleccionar — selecciona un mueble personalizado.
- /deseleccionar — deselecciona el mueble actual.
- /editarmueble — activa el modo edición del mueble seleccionado.
- /clonarmueble — duplica el mueble seleccionado.
- /moverx / /movery / /moverz [valor] — mueve el mueble en cada eje.
- /rotarx / /rotary / /rotarz [valor] — rota el mueble en cada eje.
- /prioridad [valor] — ajusta la prioridad de renderizado.
- /resetmueble — devuelve el mueble a su posición original.
- /quitarmueble — elimina el mueble seleccionado.
- /infomueble — muestra detalles del mueble seleccionado.
- /textura [índice] — aplica una textura al mueble.
- /quitartextura — quita la textura del mueble.
- /buscartextura [nombre] — busca texturas disponibles.
- /convertirpuerta — convierte el mueble en puerta funcional.
- /configurarpuerta — ajusta los parámetros de esa puerta.
- /empaquetarmueble — empaqueta el mueble para llevarlo a otra propiedad.
- /desempaquetarmueble — desempaqueta el mueble en la nueva ubicación.

## Llaves prestadas y permisos de muebles

Puedes **compartir tu propiedad** prestando llaves a otros personajes para que puedan entrar sin ti. Los límites son: **2 llaves** en casas y almacenes, **1 llave** en negocios.

Solo el propietario, su cónyuge, miembros de la facción dueña (si aplica) y quienes tengan llave compartida con permisos pueden mover o editar muebles. Las personas con llaves pueden entrar y salir pero no siempre pueden editar muebles ni tocar la configuración del inmueble.

<img width="321" height="21" alt="image" src="https://github.com/user-attachments/assets/ef84cc53-7912-48f0-bce7-a60e1a00fd3b" />

### Comandos

- /prestarllave [id] — entrega una copia de la llave a un jugador.
- /quitarllave [nombre_apellido] — revoca el acceso de una llave prestada.
- /tirarllave — deja caer la llave al suelo para que otro la recoja.

## Compra y venta de inmuebles

Las propiedades se compran entrando en el punto de venta y usando `/comprar`. Puedes venderlas al **Estado** saliendo por la puerta (recibes un porcentaje) o **a otro jugador** dentro de la propiedad con `/venderprop`.

### Cálculo real del valor de la propiedad

El precio total de una propiedad no es solo el valor base: el sistema suma varios componentes:

**Precio = (Valor base × multiplicador) + (Valor de flota × 0.6) + (Valor de muebles × 0.5) + Valor del stock**

- **Valor base**: precio original del inmueble.
- **Valor de flota**: suma del valor de todos los vehículos del negocio (60% del total).
- **Valor de muebles**: suma del valor de los muebles colocados (50% del total).
- **Valor del stock**: suma del inventario actual del negocio.

Al **vender a otro jugador**, puedes pactar el precio entre el **50% (x0.5)** y el **500% (x5.0)** del precio total calculado. Fuera de ese rango, la transacción debe hacerse por transferencia aparte.

Al **vender al Estado**, la oferta es un **30% del valor base**, con bonificación según tu nivel premium:

- Sin premium: 30%.
- Premium 1: 35%.
- Premium 2: 40%.
- Premium 3: 45%.
- Premium 4: 50%.

No puedes vender una propiedad con **caja negativa**, **pedidos en ruta**, **paquetes u objetos ilegales adentro**, ni con un **laboratorio de drogas** activo.

### Comandos

- /comprar — compra la propiedad en la que estás (si está en venta).
- /venderprop [id] [$precio] — vende tu propiedad a otro jugador cercano.
- /aceptar — acepta una oferta de compra/venta.
- /rechazar — rechaza una oferta de compra/venta.

## Entradas y salidas

Una propiedad puede tener **hasta 6 entradas distintas** con su propia posición, puerta e interior. Cada entrada puede permitir o no el ingreso de vehículos. Al acercarte a una entrada aparece un marcador: úsalo con `/entrar`. Desde dentro, `/salir` te devuelve al exterior.

Las puertas pueden estar **abiertas**, **cerradas** o **rotas**. Si está cerrada, solo el dueño o quienes tengan llave pueden pasar. El comando `/puerta` se usa cerca de una puerta interior para abrirla o cerrarla.

### Comandos

- /entrar — entra por el marcador de entrada más cercano.
- /salir — sale por el marcador de salida.
- /puerta — abre o cierra una puerta interior cercana.
- /metermoto — mete una motocicleta dentro de la propiedad.

## Casas

Las casas son propiedades **residenciales personales**. Sirven para vivir, guardar dinero/objetos en la caja, almacenar ropa y personalizar el interior con muebles. Permiten compartir hasta **2 llaves** con otros personajes.

### Comandos

- /ropa — abre el ropero de la casa para cambiar tu vestuario.
- /prestarllave [id] — comparte el acceso con otro personaje.
- /quitarllave [nombre_apellido] — revoca el acceso.

## Almacenes

Los almacenes son propiedades pensadas para **guardar grandes cantidades de objetos**. Tienen un área de almacenamiento ampliada (closet) donde puedes depositar items del inventario. También admiten hasta **2 llaves compartidas**.

A diferencia de los negocios, los almacenes no tienen empleados, ni stock de venta, ni clientes.

### Comandos

- /almacen — abre el inventario del almacén (dentro del área designada).
- /prestarllave [id] — comparte el acceso.
- /quitarllave [nombre_apellido] — revoca el acceso.

## Empresas y negocios

Los negocios son propiedades comerciales que se pueden operar con **empleados**, **stock** y **caja**. Existen varias subcategorías, cada una con mecánicas propias:

- **Tienda** — vende productos físicos, requiere stock y reposición.
- **Club / Bar / Discoteca** — cobra entrada, vende bebidas, mecánicas de ocio.
- **Concesionario** — venta de vehículos.
- **Casa de apuestas** — apuestas en carreras.
- **Casino** — juegos de azar.
- **Depósito de autos** — compraventa de vehículos incautados.
- **Empresa de transporte, taxi, pesca, limpieza, mecánica, seguridad** — basadas en el trabajo de sus empleados.
- **Despacho legal, banco, hospital, periódico** — negocios institucionales con funciones específicas.

**Diferencias clave**: los negocios con producto (tienda, club, concesionario, etc.) gestionan **stock y pedidos**; los negocios de servicios (taxi, mecánica, banco, legal...) se basan en el trabajo activo del empleado. Algunos tipos (**banco, depósito, periodismo, seguridad, casino**) no permiten unirse automáticamente con `/negunirse` y requieren contratación manual.

### Empleados

Los empleados trabajan bajo **cargos** creados por el dueño (con nombre, salario por hora y permisos). Cada cargo define qué puede hacer el empleado: acceder a caja, gestionar stock, hacer pedidos, contratar, despedir, usar los vehículos, etc.

Al entrar en servicio, los empleados reciben un sueldo cada minuto mientras se mantengan dentro del negocio o usando un vehículo de la empresa. Si se alejan demasiado tiempo, el sistema descuenta dinero y los saca de servicio automáticamente.

### Trabajar en un negocio

- Debes **aceptar un contrato** (ya sea por `/negunirse` o por contratación del dueño).
- Entras y sales de servicio con `/negservicio` (alias `/trabajar`).
- Cada minuto en servicio genera un salario (base + salario del cargo).
- Puedes tener **varios contratos** al mismo tiempo y cambiar entre ellos sin renunciar.
- Renunciar requiere confirmación (`/renunciar confirmar`).

<img width="476" height="24" alt="image" src="https://github.com/user-attachments/assets/3b74c4f9-acf5-458c-98a4-fce93212d7ba" />

### Unirse automáticamente con /negunirse

El comando `/negunirse` permite unirte como empleado sin que el dueño tenga que contratarte manualmente, siempre que:

- Estés dentro del negocio.
- El dueño tenga habilitada esta opción (`/tognegunirse`, requiere premium).
- El negocio tenga cargos configurados.
- El tipo de negocio lo permita (no funciona en banco, depósito, periodismo, seguridad ni casino).

Al usarlo recibes el cargo más básico. Después, el dueño o un gerente puede ascenderte con `/darcargo`.

<img width="587" height="61" alt="image" src="https://github.com/user-attachments/assets/78dc4cb0-d9d1-412e-86a7-1173c8d90077" />

### Comandos

- /negunirse — te unes automáticamente como empleado del negocio.
- /negservicio — activa o desactiva el modo trabajo. Alias: `/trabajar`.
- /miscontratos — muestra tus contratos activos y te permite cambiar entre ellos. Alias: `/contratos`, `/misempleos`, `/cambiarempleo`.
- /mostrarcontrato [id] — enseña tu contrato actual a otro jugador.
- /renunciar confirmar — renuncia al contrato actual.
- /contratar [id] — ofrece contrato a un jugador cercano (dueño o gerente).
- /despedir [nombre_apellido] — despide a un empleado.
- /empleados — lista a los empleados del negocio.
- /cargos — crea o edita los cargos, salarios y permisos.
- /darcargo [id] [cargo] — asigna un cargo a un empleado.
- /negnombre [nombre] — cambia el nombre del negocio (dueño, tiene coste).
- /negmotd [texto] — mensaje del día para los empleados.
- /tognegunirse — habilita o deshabilita `/negunirse` en tu negocio.
- /mostrador — fija la posición del mostrador de ventas.
- /entrada [$precio] — establece el precio de entrada (clubes).
- /derechodeadmision [id] — expulsa a un cliente del local.
- /caja — consulta, deposita o retira dinero de la caja del negocio.

## Stock y pedidos

Los negocios con productos (tiendas, clubes, etc.) manejan **stock**: cada artículo tiene un precio de venta, un coste y una cantidad disponible. Los clientes compran en el mostrador; cuando el stock se vacía, el negocio debe **hacer pedidos** a los proveedores.

Cada pedido tiene un **cooldown de 3 horas** por producto y cuesta el **90% del valor del producto**. El pago sale directamente de la caja del negocio, por lo que debe tener saldo suficiente. Los pedidos pasan por estados: _disponible → solicitado → en ruta → entregado_.

Opcionalmente puedes activar la **reposición automática** para que el sistema haga pedidos solos cuando el stock baje.

También puedes **añadir stock manualmente** al negocio: sostén el producto en la mano y usa `/meterstock` dentro del negocio para incorporarlo al inventario disponible a la venta.

### Comandos

- /stock — muestra el inventario del negocio y permite ajustar precios.
- /pedido [producto] [cantidad] — solicita reposición de un producto.
- /pedido — sin parámetros, muestra los pedidos disponibles y su estado.
- /autopedidos — activa o desactiva la reposición automática.
- /meterstock — añade al inventario del negocio el producto que tengas en la mano.
- /caja — controla el dinero disponible para pagar pedidos.

## Ganancias pasivas (NPC)

Aunque el dueño no esté conectado, los negocios con producto **generan ventas automáticas** a clientes NPC una vez por hora. Estas ventas **no usan el precio que pongas en el mostrador**: cada producto vendido paga un valor fijo equivalente a **su coste base × 1.25** (125%), y solo cuentan los productos cuyo coste base sea de **$250 o menos**.

Factores que **maximizan tus ganancias pasivas**:

- **Mantén el local limpio**: la basura acumulada reduce drásticamente cuántos productos se venden por ciclo (ver sección de basura).
- **Vende productos baratos**: los artículos con coste base > $250 no entran en las ventas pasivas. Conviene tener stock barato y variado para que el sistema lo venda.
- **Ten stock disponible**: sin stock no hay venta. Activa `/autopedidos` para que el sistema reponga solo cuando el inventario baje.
- **Mantén saldo en la caja**: los pedidos automáticos y los impuestos diarios se pagan desde la caja; si está vacía, el negocio deja de reponerse.
- **El precio del mostrador afecta solo a las ventas reales**: súbelo para maximizar lo que pagan los jugadores, pero recuerda que las ventas pasivas NPC pagan su propio precio fijo.

## Basura y limpieza

Cada venta (tanto a clientes reales como NPC) genera **1 kg de basura**. La basura se acumula en el local y afecta directamente la experiencia del cliente y tus ventas pasivas.

El efecto en las **ventas automáticas por hora** es proporcional:

| Basura acumulada | Productos vendidos por ciclo |
| ---------------- | ---------------------------- |
| 0–9 kg           | 35                           |
| 10–20 kg         | 30                           |
| 21–30 kg         | 25                           |
| 31–40 kg         | 20                           |
| 41–50 kg         | 15                           |
| 51–60 kg         | 10                           |
| 61–70 kg         | 5                            |
| +71 kg           | **0 (sin ventas)**           |

Cuando la basura supera ciertos umbrales aparecen **mensajes visuales** al entrar al negocio ("el local está desordenado", "zona crítica, cero higiene", etc.) que desincentivan a los clientes reales.

### Comandos

- /mirarbasura — muestra los kilos de basura acumulada en el negocio.
- /limpiarnegocio — limpia una parte de la basura acumulada (empleados o recolectores de basura).

## Incendios y extintores

Los negocios pueden **sufrir incendios** de forma aleatoria cuando hay bomberos en servicio. Si el local **no tiene extintores** en ese momento, se genera un incendio que daña fuertemente el inventario, apaga la emisora, activa la alarma y avisa a bomberos y policías. Tras un incendio, el negocio queda con un **cooldown** antes de poder incendiarse otra vez.

Cada negocio puede almacenar hasta **10 extintores llenos**. Los extintores se consumen cuando el sistema los usa para prevenir un incendio, por eso conviene mantenerlos siempre cargados.

### Comandos

- /extintores sacar — retira un extintor del almacén del negocio (debe estar lleno).
- /extintores rellenar — guarda un extintor lleno de vuelta al almacén del negocio.

## Inactividad y liberación automática

Si un propietario deja de entrar a su propiedad, el sistema la **libera automáticamente** y queda disponible para que otro jugador la compre. Los plazos dependen del tipo:

- **Casas compradas**: 60 días sin actividad.
- **Casas alquiladas**: 14 días sin actividad.
- **Negocios**: 14 días sin actividad.
- **Almacenes**: 90 días sin actividad.
- **Negocios sucios**: 7 días sin actividad **si además** tienen 85+ kg de basura acumulada.

Cuando una propiedad se libera, el dueño recibe una notificación con el motivo. Dentro del negocio se **despide a los empleados**, se **vacía la caja**, se **expulsa a los jugadores**, se **resetean las llaves** y se limpian los inventarios. Por eso conviene entrar cada cierto tiempo a tus propiedades aunque sea brevemente, y mantener limpio cualquier negocio activo.
