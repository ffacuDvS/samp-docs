# Sistema de drogas

## Introducción

El sistema de drogas permite a los personajes consumir, fabricar y cultivar distintas sustancias. Cada droga tiene efectos propios, una duración, y puede generar adicción. Mezclar varias drogas o abusar de ellas puede causar sobredosis, heridas y deterioro de salud.

<img width="192" height="17" alt="image" src="https://github.com/user-attachments/assets/b6b2dd13-ecad-4b25-a30d-d20e9c515fba" />

### Comandos

- /usardroga [cantidad] — consume la droga que tengas en la mano derecha (0.1 a 1 gramos).
- /mirar [id] — muestra los estados visibles de un personaje.

## Lista de drogas

Cada droga tiene efectos distintos: recupera hasta cierto valor de vida, resistencia a golpes / disparos / arresto (en porcentaje), y bonificaciones delictivas. Los efectos tardan en activarse (**retraso**) y duran un tiempo (**duración**).

- **Marihuana**
  - Retraso: 2 min. Duración: 30 min.
  - Recupera hasta +10 HP.
  - Resistencia: 5% golpes, 5% disparos.
  - 70% de probabilidad de +1 punto de habilidad delictiva.
- **Cocaína**
  - Retraso: 1 min. Duración: 5 min.
  - Recupera hasta +20 HP.
  - Resistencia: 20% golpes, 15% disparos.
  - 75% de probabilidad de +2 puntos de habilidad.
  - 70% de probabilidad de +$30 extra por delitos.
- **Crack**
  - Retraso: 10 s. Duración: 1 min 30 s.
  - Recupera hasta +30 HP.
  - Resistencia: 20% golpes, 25% disparos.
  - 85% de probabilidad de +2 puntos de habilidad.
  - 75% de probabilidad de +$45 extra por delitos.
- **MDMA**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +15 HP.
  - Resistencia: 10% golpes, 10% disparos, 10% arresto.
  - 80% de probabilidad de +2 puntos de habilidad.
- **Fentanilo**
  - Retraso: 1 min. Duración: 1 hora.
  - **Quita hasta 15 HP** en vez de curar.
  - Resistencia: 50% golpes, 25% disparos, 25% arresto.
  - 80% de probabilidad de +3 puntos de habilidad vehicular.
- **Heroína**
  - Retraso: 10 s. Duración: 30 min.
  - Recupera hasta +45 HP.
  - Resistencia: 30% golpes, 10% disparos, 20% arresto.
  - 70% de probabilidad de +2 puntos de habilidad.
  - 90% de probabilidad de +$70 extra por delitos.
  - Reduce 40% el tiempo de desarme vehicular.
- **LSD**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +30 HP.
  - Resistencia: 10% golpes.
  - 75% de probabilidad de +2 puntos de habilidad.
- **Metanfetamina**
  - Retraso: 2 min. Duración: 10 min.
  - Recupera hasta +50 HP.
  - Resistencia: 20% golpes, 10% disparos.
  - 80% de probabilidad de +2 puntos de habilidad.
  - 80% de probabilidad de +$50 extra por delitos.
  - Reduce 30% el tiempo al forzar y desarmar vehículos.
- **Codeína**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +25 HP.
  - Resistencia: 20% golpes, 10% disparos.
- **Alprazolam**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +20 HP.
  - Resistencia: 10% golpes.
- **Paracetamol**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +15 HP.
  - Resistencia: 5% golpes.
- **Óxido nitroso**
  - Retraso: 1 min. Duración: 5 min.
  - Recupera hasta +15 HP.
  - Resistencia: 10% golpes.
  - 70% de probabilidad de +1 punto de habilidad.
- **Hongos**
  - Retraso: 3 min. Duración: 30 min.
  - Recupera hasta +15 HP.
  - Resistencia: 15% golpes.
  - Otorga +1 punto de habilidad.
- **Esteroides**
  - Retraso: 5 min. Duración: 15 min.
  - Recupera hasta +15 HP.
  - Resistencia: 30% golpes, 30% arresto.
  - Otorga +1 punto de habilidad.
- **Píldoras**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +15 HP.
  - Resistencia: 5% golpes.
- **Tabaco**
  - Retraso: 30 s. Duración: 5 min.
  - Recupera hasta +5 HP.
  - Sin resistencias.
  - Solo genera tabaquismo.
- **Alcohol**
  - Retraso: 2 min. Duración: 1 hora.
  - Recupera hasta +10 HP.
  - Resistencia: 10% golpes, 10% disparos, 30% arresto.
  - Provoca embriaguez, náuseas y vómitos según cantidad.
- **Ibuprofeno / Amoxicilina / Omeprazol / Losartan / Metformina / Salbutamol / Loratadina / Diclofenaco**
  - Retraso: 5 min. Duración: 30 min.
  - Recupera hasta +15 HP.
  - Resistencia: 5% golpes.

> Todas las drogas pueden recuperar vida **hasta 100 HP máximo** (excepto el fentanilo, que resta). Las resistencias mostradas son el máximo alcanzable con 100 de fuerza; con menos fuerza los porcentajes se reducen proporcionalmente. Mezclar más de 2 drogas provoca heridas graves y sobredosis.

<img width="511" height="153" alt="image" src="https://github.com/user-attachments/assets/791ec5df-f405-402a-af01-a3f6fe8ed0ce" />

## Estados del personaje

Al usar `/mirar` sobre un personaje, se muestran signos visibles según las drogas consumidas recientemente:

- **Marihuana** — apesta a marihuana, boca seca, ojos ligeramente enrojecidos.
- **Cocaína** — pupilas dilatadas, nariz algo moquienta.
- **Crack / Metanfetamina** — pupilas dilatadas, olor desagradable, sudando, habla rápido.
- **MDMA** — pupilas dilatadas, sudando, aprieta la mandíbula involuntariamente.
- **Fentanilo / Heroína** — pupilas dilatadas, boca seca, sudando, desorientado.
- **LSD** — pupilas dilatadas, boca seca, sudando, tiembla involuntariamente.
- **Codeína / Óxido nitroso / Hongos** — habla lento, poco responsivo, le cuesta mantener el balance.
- **Esteroides** — tiene acné.
- **Tabaco** — huele ligeramente a tabaco.
- **Alcohol** — huele ligeramente a alcohol.

<img width="247" height="75" alt="image" src="https://github.com/user-attachments/assets/9315d144-2758-4514-a7bb-46b9ad905d4e" />

### Comandos

/mirar [id] — revisa los estados físicos visibles de un personaje.

## Fuerza

La **fuerza** es la calidad o pureza de una droga (0 a 100). Determina qué tan potentes son sus efectos: una droga con fuerza cercana a **100** genera efectos máximos, mayor recuperación de vida, más resistencia y mejores bonificaciones; una con fuerza cercana a **0** es prácticamente inútil y apenas produce efecto.

La fuerza **disminuye cada día** de forma automática (entre 2 y 6 puntos diarios según la droga). Cuando una droga baja de 1 de fuerza, se destruye y desaparece del inventario. Por eso conviene consumirla o venderla antes de que pierda valor.

## Adicción

Cada consumo agrega puntos de adicción a la droga usada. Si alcanzas cierto nivel de adicción y pasan **24 horas** sin consumir, empiezas a sentir **abstinencia**: mensajes de ansiedad, náuseas, vómitos y pérdida de vida. Cuanto mayor la adicción, más fuerte el síndrome.

<img width="673" height="45" alt="image" src="https://github.com/user-attachments/assets/b07ff909-75b6-48e5-b4d7-ffb8ac2e1577" />

La adicción baja sola con el tiempo si dejas de consumir. También puedes usar **medicamentos de detoxicación** para reducirla, o **narcán** para casos de sobredosis con varias drogas activas. Casos especiales:

- **Tabaco** → tabaquismo
- **Alcohol** → alcoholismo

<img width="309" height="21" alt="image" src="https://github.com/user-attachments/assets/686df445-728d-4a26-9a94-bc0ec57c1ef4" />

### Comandos

/usardroga — al tener un medicamento de detoxicación o narcán en la mano derecha, se usa con este comando.

## Laboratorios de droga

Los laboratorios permiten fabricar drogas sintéticas. Solo los delincuentes pueden crear uno, y debe colocarse dentro de una **casa o almacén propio**. Cada personaje solo puede tener **un laboratorio** y hay un cooldown de **2 semanas (336 horas)** entre creaciones.

Los narcotraficantes (miembros de facciones ilegales destacadas) acceden a una variedad mayor de drogas fabricables. Sin serlo, solo podrás crear **óxido nitroso** y **crack**. Drogas fabricables en un laboratorio: óxido nitroso, cocaína, crack, MDMA, heroína, LSD y metanfetamina.

La cantidad máxima de ingredientes depende del tipo de propiedad (casa o almacén) y de tu habilidad de drogas.

> ⚠️ Cocinar **metanfetamina** tiene un **20% de probabilidad de generar una explosión** en el laboratorio. Para evitarla, un jugador dentro de la propiedad debe tener un **extintor en la mano derecha** al momento de la cocción.

### Comandos

/crearlaboratorio [confirmar] — crea un laboratorio de drogas en tu propiedad actual.
/destruirlaboratorio [confirmar] — destruye el laboratorio más cercano (dueño o autoridad).
/creardroga — abre el menú para fabricar drogas en el laboratorio cercano.
/narcotraficante — te marca como narcotraficante si perteneces a una facción ilegal destacada.
/falsificarreceta — crea una receta médica falsa de opioides (requiere habilidad y dinero).

## Lista de ingredientes

Cada gramo de droga fabricada consume **1 unidad de cada ingrediente** seleccionado en la receta. Los ingredientes se consiguen actualmente mediante **robos, compras a otros jugadores, saqueos o importación ilegal** dentro del servidor.

Ingredientes según la droga:

- **Cocaína:** Hoja de Coca, Queroseno, Ácido Sulfúrico, Amoniaco, Acetona, Potasio, Éter, Gasolina.
- **Crack:** Cocaína, Bicarbonato de Sodio, Carbonato de Amonio, Bicarbonato de Amonio.
- **Heroína:** Opio, Carbonato de Sodio, Ácido Muriático, Éter, Cafeína, Fentanilo.
- **LSD:** Ergot, Cafergot, Amoniaco, Alcohol Isopropílico.
- **MDMA:** Hoja de Sasafrás, Ácido Muriático, Alcohol Isopropílico, Ketamina, Metanfetamina.
- **Metanfetamina:** Efredina, Xileno, Tolueno, Píldoras Sudafed, Potasio, Éter, Acetona, Ácido Sulfúrico, Fósforo rojo, Fentanilo.
- **Óxido nitroso:** Sifón con N2O, Globo, Dispensador de crema.
- **Marihuana:** se obtiene cultivándola con semillas y abono.
- **Hongos:** se recogen directamente en zonas silvestres del mapa.

### Comandos

/plantacion [crear | mejorar | cuidar | examinar | cosechar | eliminar] — gestiona una plantación de marihuana (requiere semillas, abono, agua y fertilizante).
