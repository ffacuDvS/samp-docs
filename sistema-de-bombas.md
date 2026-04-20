# Sistema de bombas

## Introducción

El sistema de **bombas telefónicas** (también llamado "TNT" internamente) permite colocar explosivos que se **detonan a distancia mediante una llamada de teléfono**. Cada bomba guarda un número asociado y, cuando ese número recibe una llamada, el explosivo se activa.

Es un sistema pensado tanto para el **roleplay criminal** (sabotaje, atentados, trampas) como para el trabajo de **detectives y fuerzas del orden**, que disponen de herramientas para localizar y desactivar los artefactos antes de que exploten.

## Cómo funciona la detonación

- La bomba queda vinculada a un **número de teléfono de 8 dígitos** (rango válido: entre `10000000` y `99999999`). Llamadas a números fuera de ese rango **no detonan nada**, para evitar activaciones accidentales.
- Al recibir la llamada al número asociado, el objeto bomba se elimina y tras una **cuenta atrás de 3 segundos** se genera:
  - Una **explosión en cascada** a distintas alturas sobre el punto de colocación y alrededores.
  - Un **cono de fuego** con señales de tráfico desplegadas automáticamente por el LSFD alrededor del cráter.
  - Un **aviso automático por radio** al LSPD y a los paramédicos:
    > *"Se ha reportado una explosión en [zona]."*

Esto significa que, aunque la detonación sea silenciosa hasta la llamada, **una vez que explota la policía y los servicios médicos son avisados de inmediato**.

## Desactivación de bombas

Cualquier personaje puede intentar desactivar una bomba cercana si cumple los requisitos. No es una habilidad exclusiva de detective: se premia la inversión en electrónica.

### Requisitos

- **Kit de desactivación de bombas** (objeto 943) en la **mano derecha**.
- Ser **detective privado** **o** tener al menos **5 de habilidad de electrónica**.
- Estar **a 5 metros o menos** de la bomba (**radio de detección**: 5 m).

### Minijuego de cables

Al usar el comando, el juego abre un diálogo con **3 cables** (rojo, amarillo y verde) y debes elegir **cuál cortar**:

- El servidor elige **al azar** cuál es el cable incorrecto.
- **Probabilidad de éxito: 2/3 (≈66,7 %)** — cortas uno de los dos cables correctos y desactivas la bomba.
- **Probabilidad de fallo: 1/3 (≈33,3 %)** — cortas el cable trampa y la **bomba detona en el acto**, aplicándote a ti la explosión completa.

Una desactivación exitosa deja el objeto inerte; un fallo activa la misma secuencia que una detonación normal, incluyendo el aviso automático a LSPD y LSFD.

### Comando

- `/desactivarbomba` — inicia el proceso de desactivación de la bomba más cercana.

## Relación con otros sistemas

- **[Sistema de detectives privados](sistema-de-detectives-privados.md)**: los detectives obtienen el kit de desactivación a través de `/equipodet` en el Ammu-Nation de Market, y pueden usarlo aunque no estén en servicio de ninguna facción.
- **Policía y paramédicos**: reciben automáticamente el aviso por radio cuando una bomba detona, lo que convierte cada explosión en un evento de respuesta activa para LSPD y LSFD.

> **Aviso de roleplay:** las bombas son un recurso de alto impacto. Úsalas dentro de tramas coherentes y con antagonistas que tengan margen para reaccionar; recuerda que el sistema de detección y desactivación existe precisamente para dar contrajuego, no para ser un simple atajo ofensivo.
