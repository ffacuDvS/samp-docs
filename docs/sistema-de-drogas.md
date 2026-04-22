# Sistema de drogas

El sistema de drogas permite a los personajes consumir, fabricar y cultivar distintas sustancias. Cada droga tiene efectos propios, una duración, y puede generar adicción. Mezclar varias drogas o abusar de ellas puede causar sobredosis, heridas y deterioro de salud.

<img width="192" height="17" alt="image" src="https://github.com/user-attachments/assets/b6b2dd13-ecad-4b25-a30d-d20e9c515fba" />

- /usardroga [cantidad] — consume la droga que tengas en la mano derecha (0.1 a 1 gramos).
- /mirar [id] — muestra los estados visibles de un personaje.

## Efectos de las drogas

Cada droga tiene efectos distintos: recupera hasta cierto valor de vida, resistencia a golpes / disparos / arresto (en porcentaje), y bonificaciones delictivas. Los efectos tardan en activarse (**retraso**) y duran un tiempo (**duración**).

### Drogas recreativas e ilegales

| Droga | Retraso | Duración | HP | Golpes | Disparos | Arresto | Habilidad | Extra |
|---|---|---|---|---|---|---|---|---|
| **Marihuana** | 2 min | 30 min | +10 | 5% | 5% | — | 70% → +1 | — |
| **Cocaína** | 1 min | 5 min | +20 | 20% | 15% | — | 75% → +2 | 70% → +$30 por delitos |
| **Crack** | 10 s | 1 min 30 s | +30 | 20% | 25% | — | 85% → +2 | 75% → +$45 por delitos |
| **MDMA** | 5 min | 30 min | +15 | 10% | 10% | 10% | 80% → +2 | — |
| **Heroína** | 10 s | 30 min | +45 | 30% | 10% | 20% | 70% → +2 | 90% → +$70 por delitos; −40% desarme vehicular |
| **LSD** | 5 min | 30 min | +30 | 10% | — | — | 75% → +2 | — |
| **Metanfetamina** | 2 min | 10 min | +50 | 20% | 10% | — | 80% → +2 | 80% → +$50 por delitos; −30% forzar/desarmar vehículos |
| **Fentanilo** | 1 min | 1 hora | **−15** | 50% | 25% | 25% | 80% → +3 vehicular | ⚠️ Resta HP en vez de curar |
| **Hongos** | 3 min | 30 min | +15 | 15% | — | — | +1 fijo | — |
| **Óxido nitroso** | 1 min | 5 min | +15 | 10% | — | — | 70% → +1 | — |
| **Esteroides** | 5 min | 15 min | +15 | 30% | — | 30% | +1 fijo | — |

### Sustancias legales y cotidianas

| Sustancia | Retraso | Duración | HP | Golpes | Disparos | Arresto | Notas |
|---|---|---|---|---|---|---|---|
| **Tabaco** | 30 s | 5 min | +5 | — | — | — | Solo genera tabaquismo |
| **Alcohol** | 2 min | 1 hora | +10 | 10% | 10% | 30% | Provoca embriaguez, náuseas y vómitos |

### Medicamentos

| Medicamento | Retraso | Duración | HP | Golpes | Notas |
|---|---|---|---|---|---|
| **Codeína** | 5 min | 30 min | +25 | 20% | Analgésico opioide; bloquea consulta médica |
| **Alprazolam** | 5 min | 30 min | +20 | 10% | Ansiolítico |
| **Paracetamol** | 5 min | 30 min | +15 | 5% | Analgésico / antifebril |
| **Píldoras** | 5 min | 30 min | +15 | 5% | Genérico |
| **Ibuprofeno** | 5 min | 30 min | +15 | 5% | Antiinflamatorio |
| **Amoxicilina** | 5 min | 30 min | +15 | 5% | Antibiótico |
| **Omeprazol** | 5 min | 30 min | +15 | 5% | Antiácido |
| **Losartán** | 5 min | 30 min | +15 | 5% | Hipertensión |
| **Metformina** | 5 min | 30 min | +15 | 5% | Diabetes |
| **Salbutamol** | 5 min | 30 min | +15 | 5% | Trata la tos; bloquea consulta médica |
| **Loratadina** | 5 min | 30 min | +15 | 5% | Antialérgico (anula estornudos) |
| **Diclofenaco** | 5 min | 30 min | +15 | 5% | Analgésico / antiinflamatorio |

> Todas las drogas pueden recuperar vida **hasta 100 HP máximo** (excepto el fentanilo, que resta). Las resistencias mostradas son el máximo alcanzable con 100 de fuerza; con menos fuerza los porcentajes se reducen proporcionalmente. Mezclar más de 2 drogas provoca heridas graves y sobredosis.

---

## Signos visibles

<img width="511" height="153" alt="image" src="https://github.com/user-attachments/assets/791ec5df-f405-402a-af01-a3f6fe8ed0ce" />

Al usar `/mirar` sobre un personaje, se muestran signos visibles según las drogas consumidas recientemente:

| Droga | Signos visibles |
|---|---|
| **Marihuana** | Apesta a marihuana, boca seca, ojos ligeramente enrojecidos |
| **Cocaína** | Pupilas dilatadas, nariz algo moquienta |
| **Crack / Metanfetamina** | Pupilas dilatadas, olor desagradable, sudando, habla rápido |
| **MDMA** | Pupilas dilatadas, sudando, aprieta la mandíbula involuntariamente |
| **Fentanilo / Heroína** | Pupilas dilatadas, boca seca, sudando, desorientado |
| **LSD** | Pupilas dilatadas, boca seca, sudando, tiembla involuntariamente |
| **Codeína / Óxido nitroso / Hongos** | Habla lento, poco responsivo, le cuesta mantener el balance |
| **Esteroides** | Tiene acné |
| **Tabaco** | Huele ligeramente a tabaco |
| **Alcohol** | Huele ligeramente a alcohol |

<img width="247" height="75" alt="image" src="https://github.com/user-attachments/assets/9315d144-2758-4514-a7bb-46b9ad905d4e" />

/mirar [id] — revisa los estados físicos visibles de un personaje.

---

## Fuerza
La **fuerza** es la calidad o pureza de una droga (0 a 100). Determina qué tan potentes son sus efectos: una droga con fuerza cercana a **100** genera efectos máximos, mayor recuperación de vida, más resistencia y mejores bonificaciones; una con fuerza cercana a **0** es prácticamente inútil y apenas produce efecto.

La fuerza **disminuye cada día** de forma automática (entre 2 y 6 puntos diarios según la droga). Cuando una droga baja de 1 de fuerza, se destruye y desaparece del inventario. Por eso conviene consumirla o venderla antes de que pierda valor.

---

## Adicción
Cada consumo agrega puntos de adicción a la droga usada. Si alcanzas cierto nivel de adicción y pasan **24 horas** sin consumir, empiezas a sentir **abstinencia**: mensajes de ansiedad, náuseas, vómitos y pérdida de vida. Cuanto mayor la adicción, más fuerte el síndrome.

<img width="673" height="45" alt="image" src="https://github.com/user-attachments/assets/b07ff909-75b6-48e5-b4d7-ffb8ac2e1577" />

La adicción baja sola con el tiempo si dejas de consumir. También puedes usar **medicamentos de detoxicación** para reducirla, o **narcán** para casos de sobredosis con varias drogas activas. Casos especiales:

- **Tabaco** → tabaquismo
- **Alcohol** → alcoholismo

<img width="309" height="21" alt="image" src="https://github.com/user-attachments/assets/686df445-728d-4a26-9a94-bc0ec57c1ef4" />

/usardroga — al tener un medicamento de detoxicación o narcán en la mano derecha, se usa con este comando.

---

## Fabricación de drogas

Los laboratorios permiten fabricar drogas sintéticas. Solo los delincuentes pueden crear uno, y debe colocarse dentro de una **casa o almacén propio**. Cada personaje solo puede tener **un laboratorio** y hay un cooldown de **2 semanas (336 horas)** entre creaciones.

Los narcotraficantes (miembros de facciones ilegales destacadas) acceden a una variedad mayor de drogas fabricables. Sin serlo, solo podrás crear **óxido nitroso** y **crack**.

### Drogas fabricables en laboratorio

| Droga | Disponible para | Ingredientes |
|---|---|---|
| **Óxido nitroso** | Todos los delincuentes | Sifón con N₂O, Globo, Dispensador de crema |
| **Crack** | Todos los delincuentes | Cocaína, Bicarbonato de Sodio, Carbonato de Amonio, Bicarbonato de Amonio |
| **Cocaína** | Solo narcotraficantes | Hoja de Coca, Queroseno, Ácido Sulfúrico, Amoniaco, Acetona, Potasio, Éter, Gasolina |
| **Heroína** | Solo narcotraficantes | Opio, Carbonato de Sodio, Ácido Muriático, Éter, Cafeína, Fentanilo |
| **LSD** | Solo narcotraficantes | Ergot, Cafergot, Amoniaco, Alcohol Isopropílico |
| **MDMA** | Solo narcotraficantes | Hoja de Sasafrás, Ácido Muriático, Alcohol Isopropílico, Ketamina, Metanfetamina |
| **Metanfetamina** | Solo narcotraficantes | Efredina, Xileno, Tolueno, Píldoras Sudafed, Potasio, Éter, Acetona, Ácido Sulfúrico, Fósforo rojo, Fentanilo |

La cantidad máxima de ingredientes depende del tipo de propiedad (casa o almacén) y de tu habilidad de drogas.

> ⚠️ Cocinar **metanfetamina** tiene un **20% de probabilidad de generar una explosión** en el laboratorio. Para evitarla, un jugador dentro de la propiedad debe tener un **extintor en la mano derecha** al momento de la cocción.

Cada gramo de droga fabricada consume **1 unidad de cada ingrediente** seleccionado en la receta. Los ingredientes se consiguen actualmente mediante **robos, compras a otros jugadores, saqueos o importación ilegal** dentro del servidor.

### Obtención de drogas naturales

| Droga | Cómo se obtiene |
|---|---|
| **Marihuana** | Se cultiva con semillas, abono, agua y fertilizante mediante el sistema de plantaciones |
| **Hongos** | Se recogen directamente en zonas silvestres del mapa |

### Comandos

- /crearlaboratorio [confirmar] — crea un laboratorio de drogas en tu propiedad actual.
- /destruirlaboratorio [confirmar] — destruye el laboratorio más cercano (dueño o autoridad).
- /creardroga — abre el menú para fabricar drogas en el laboratorio cercano.
- /narcotraficante — te marca como narcotraficante si perteneces a una facción ilegal destacada.
- /falsificarreceta — crea una receta médica falsa de opioides (requiere habilidad y dinero).
- /plantacion [crear | mejorar | cuidar | examinar | cosechar | eliminar] — gestiona una plantación de marihuana (requiere semillas, abono, agua y fertilizante).
