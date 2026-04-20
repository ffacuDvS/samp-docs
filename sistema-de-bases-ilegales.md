# Sistema de bases ilegales

## Introducción

Las **bases ilegales** son propiedades que pasan a ser propiedad de una **facción criminal oficial o destacada**, y que funcionan como centros de operaciones y almacenamiento para el grupo. Cualquier tipo de propiedad sirve: crackhouses, clubes nocturnos, casas particulares, almacenes o negocios.

El objetivo del sistema es premiar la **organización y constancia** de las facciones consolidadas, dándoles un espacio inmersivo, más seguro frente a la policía y con ventajas mecánicas para el consumo de drogas pesadas.

### Comandos

- /baseilegal — sin argumentos, muestra la base ilegal actual de tu facción (si existe). Solo líderes pueden asignarla o retirarla.
- /baseilegal [id propiedad] — (solo líder) inicia la asignación de una propiedad tuya como base ilegal. Requiere confirmación con `/baseilegal [id] confirmar`.
- /baseilegal [id propiedad] retirar — (solo líder) desvincula la propiedad como base ilegal y la devuelve al líder. Respeta el cooldown de 14 días.
- /almacen — gestiona el almacén de la base (ver permisos abajo).

## Asignación y cooldown

Para asignar una base ilegal:

- El jugador debe ser **líder** de una facción ilegal **oficial** o **destacada**.
- La propiedad debe ser **de su propiedad personal** (o de su cónyuge si están casados).
- La facción **no debe tener** ya otra base ilegal asignada.
- Se requiere confirmación doble con el parámetro `confirmar`.

Al asignarla:

- La propiedad deja de tener dueño individual y pasa a pertenecer a la facción.
- Todos los miembros de la facción reciben **llaves automáticamente** al entrar al radio de la propiedad.
- Se inicia un **cooldown de 14 días** durante el cual la base no se puede cambiar.

Al retirarla (tras el cooldown):

- La propiedad vuelve al líder como dueño.
- La facción pierde toda referencia a esa base.

## Permisos y roles

El acceso a la base ilegal se comporta del siguiente modo:

| Rol | Acceso | Almacén (meter) | Almacén (retirar) |
|---|---|---|---|
| **Líder** de la facción | Sí (como dueño) | Sí | Sí |
| **Miembro** de la facción | Sí (como inquilino) | Sí | No |
| Otros jugadores | Según reglas normales de la propiedad | — | — |

## Beneficios para facciones destacadas u oficiales

### Invisibilidad frente a la policía

- La base ilegal **no aparece en el ordenador policial** como propiedad regular.
- Cualquier incidente (balaceras, heridos de bala, reportes automáticos al 911) generado **dentro de la base** o en el interior de su perímetro **no crea alerta policial**: el incidente se descarta por completo.

Esto vale tanto dentro de la propiedad (en su interior virtual) como en el exterior dentro de un **radio de 15 metros** alrededor de la entrada.

### Bonificaciones por consumo de drogas pesadas

Consumir drogas dentro de la base ilegal desbloquea una lotería aleatoria. El personaje debe estar **vivo** y consumir al menos **0,5 gramos acumulados** para participar plenamente. Consumir menos de esa cantidad reduce las probabilidades en **−10 %**.

| Sustancia | Resultado | Probabilidad base |
|---|---|---|
| Crack o heroína | +1 a +3 **puntos de experiencia** | 7 % |
| Fentanilo | +1 **moneda premium** | 1,5 % |
| Fentanilo | +1 **punto de rol positivo** | 0,1 % |

Los puntos de rol se registran en el historial del personaje con el motivo `"Consumir fentanilo en el entorno de [facción]"`, vinculado a la facción dueña de la base.

> **Nota:** fuera de una base ilegal, el consumo de drogas puede activar en su lugar la recompensa estándar de **zona de pandilla** (ver [Sistema de zonas de pandilla](sistema-de-zonas-de-pandilla.md)).
