# Sistema de plantaciones de marihuana

## Introducción

El sistema de plantación de marihuana ha sido una de las características más demandadas dentro del sistema de creación de drogas. Cualquier personaje puede cultivar marihuana en casas, negocios, almacenes, bosques o al aire libre, sin necesidad de una habilidad mínima en drogas.

Ten cuidado: cualquier personaje que tenga acceso al lugar donde está la planta podrá **robar los cogollos** o **destruirla**.

El servidor permite un máximo de **1500 plantas activas** simultáneamente.

### Comandos

- /plantacion crear — planta una nueva maceta de marihuana. Alias: `/plantación`.
- /plantacion mejorar — aplica fertilizante a la planta más cercana.
- /plantacion cuidar — riega la planta más cercana.
- /plantacion examinar — muestra las estadísticas de la planta más cercana.
- /plantacion cosechar — recoge los cogollos cuando la planta está madura.
- /plantacion eliminar — descarta la planta más cercana (la convierte en bolsa de basura).

## Plantación

Para crear una nueva planta debes cumplir **tres requisitos simultáneos**:

- Llevar un paquete de **Semillas de Marihuana** en la mano derecha (al menos 1 unidad).
- Tener un **Saco de Abono** en el piso, a **≤ 5 metros** de distancia.
- No estar a menos de **1,5 metros** de otra planta ya existente.

Al ejecutar `/plantacion crear`, el personaje coloca una maceta en su posición y orientación actuales. La planta nace con **5/10 de salud**, **0/5 de agua**, **0/5 de fertilizante** y madurez **Semilla**.

El consumo por plantación es aleatorio:

- **1 a 5 semillas** del paquete.
- **1 a 5 unidades** del saco de abono.

Si cualquiera de los dos items se queda en 0 tras el descuento, se elimina del inventario.

## Mejora (fertilización)

El comando `/plantacion mejorar` aplica fertilizante a la planta más cercana. Requisitos:

- Tener un **bote de Fertilizante para Cannabis** en la mano derecha (al menos 1 unidad).
- Que la planta tenga menos de **5/5** de fertilizante acumulado.

Cada uso aumenta **+1 salud** y **+1 fertilizante** (hasta sus topes de 10 y 5). El bote consume entre **1 y 3 unidades** por aplicación y puede otorgar **+0 a +1 de habilidad de drogas**.

## Cuidado (riego)

Con `/plantacion cuidar` riegas la planta más cercana. Requisitos:

- Tener una **Botella de Agua** en la mano derecha (al menos 1 unidad).
- Que la planta tenga menos de **5/5** de agua.

Cada uso aumenta **+1 salud** y **+1 agua** (topes 10 y 5). La botella consume entre **1 y 3 unidades** por aplicación y puede otorgar **+0 a +1 de habilidad de drogas**.

Es recomendable regar y fertilizar de forma regular: sin agua o sin fertilizante la planta no crecerá y, en cada ciclo, irá perdiendo estadísticas hasta morir.

## Crecimiento

Cada planta tiene **seis etapas de madurez**:

| Etapa | Nombre |
|-------|--------|
| 0 | Semilla |
| 1 | Brote |
| 2 | Plántula |
| 3 | Crecida |
| 4 | Floración |
| 5 | Cosecha |

El estímulo de crecimiento se procesa en **cada reinicio del servidor**: al cargar las plantas de la base de datos, cada planta intenta subir una etapa si cumple los **tres requisitos**:

- Salud ≥ **5/10**
- Agua ≥ **3/5**
- Fertilizante ≥ **1/5**

Tras el intento de crecimiento (cumpla o no los requisitos) **siempre se consumen estadísticas**:

- Salud: **−1 a −2**
- Agua: **−1 a −3**
- Fertilizante: **−1 a −3**

Las plantas con **salud 0** son eliminadas automáticamente de la base de datos al arrancar el servidor.

## Cosecha

Cuando la planta alcanza la etapa **Floración** o **Cosecha**, puede recogerse con `/plantacion cosechar`. Requisitos:

- Tener la **mano derecha vacía**.
- Planta en madurez **≥ 4** (Floración o Cosecha).

Rendimiento por etapa:

- **Floración (4)**: entre **20 y 49 gramos** de cogollos.
- **Cosecha (5)**: entre **30 y 49 gramos** de cogollos.

Los cogollos cosechados llegan a la mano derecha con una **calidad (fuerza) calculada** a partir del estado final de la planta:

- Agua aporta hasta **20 puntos**.
- Fertilizante aporta hasta **50 puntos**.
- Salud aporta hasta **30 puntos**.
- Total posible: **0 a 100**.

Cada cosecha otorga **+0 a +2 de habilidad de drogas**. Tras la cosecha, la planta se reinicia a madurez **Semilla** y vuelve a arrancar desde cero (manteniendo agua, fertilizante y salud residuales).

## Examinar

Con `/plantacion examinar` consultas los datos de la planta más cercana. La visibilidad depende de la **habilidad de drogas** del personaje:

- **Siempre visible**: ID de la planta y etapa de madurez.
- **Habilidad ≥ 5**: agua (`X/5`) y fertilizante (`X/5`).
- **Habilidad ≥ 10**: salud (`X/10`).

## Eliminar

`/plantacion eliminar` destruye la planta más cercana y deja una **bolsa de basura** en su posición. La acción es irreversible y no requiere items.

## Comandos administrativos

- /plantacion forzar — fuerza un ciclo de crecimiento en la planta más cercana (sin esperar a un reinicio). Restringido a **Manager (8)**.

## Growshops

Los negocios con catálogo de tipo **growshop** tienen acceso a la venta de los tres consumibles del sistema:

- **Semillas de Marihuana** (ID de objeto 62).
- **Saco de Abono** (ID de objeto 712).
- **Fertilizante para Cannabis** (ID de objeto 713).

La **Botella de Agua** (ID 152) se obtiene por los canales habituales (tiendas 24/7, máquinas expendedoras, etc.).
