# M3: Gestión de actividades culturales y funciones

## Objetivo

Registrar actividades culturales y programar sus funciones con sala, horario, precio, modalidad y aforo.

## Responsable

PENDIENTE

## Responsabilidades

- Mantener las actividades culturales de cada organización.
- Programar funciones.
- Verificar cruces de horario en una sala.
- Verificar el aforo.
- Publicar y cancelar funciones.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M3-01 | El organizador debe poder registrar y modificar actividades culturales indicando título, descripción y tipo de actividad. | MVP |
| RF-M3-02 | El organizador debe poder programar funciones indicando sala, fecha, horario, precio, aforo de venta y modalidad de aforo. | MVP |
| RF-M3-03 | Antes de registrar una función, el sistema debe validar que no exista otra función en la misma sala durante un horario superpuesto y que el aforo de venta no supere el aforo máximo. | MVP |
| RF-M3-04 | El organizador debe poder publicar o cancelar una función. Solamente las funciones publicadas deben aparecer en la cartelera. | MVP |

## Clases propias

- `ActividadCultural`
- `Funcion`

Enums propios: `TipoActividadCultural`, `EstadoFuncion` y `ModalidadAforo`.

El tipo de actividad es un atributo enumerado de `ActividadCultural`; una película o una obra teatral no requiere una subclase independiente.

## Reglas de negocio

1. Una actividad cultural pertenece a una organización.
2. Una actividad puede tener varias funciones.
3. Una función pertenece a una actividad y a una sala.
4. Dos funciones no pueden superponerse en la misma sala.
5. El aforo de venta no puede superar el aforo máximo de la sala.
6. Una función numerada utiliza las butacas configuradas para la sala.
7. Una función general vende cantidades de cupos sin asignar butaca.
8. Solo el organizador de la organización propietaria puede modificar la actividad o función.

## Flujos

### M3-A Programación de una función

1. El organizador registra o selecciona una actividad cultural.
2. Selecciona sala, fecha y horario.
3. Define precio, aforo de venta y modalidad.
4. El sistema valida horario y capacidad.
5. El organizador guarda y publica la función.

**Resultado:** función disponible para la cartelera.

## Dependencias y contratos

- Expone `IGestionProgramacionService` para mantener actividades culturales y programar, validar, publicar y cancelar funciones.
- Depende de M1 para comprobar la asignación `ORGANIZADOR` y su alcance.
- Depende de M2 para obtener organizaciones, salas, aforos máximos y butacas.
- Proporciona a M4 las actividades y funciones publicadas.
- Proporciona a M5 la función, el precio, la modalidad y el aforo de venta que deben revalidarse.

## Riesgo principal

Cruces de horarios, modalidad y aforo. Complejidad: media.

## Estado de implementación

No iniciado.
