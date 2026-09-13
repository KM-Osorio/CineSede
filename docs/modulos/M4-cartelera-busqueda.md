# M4: Cartelera y búsqueda de funciones

## Objetivo

Permitir al público consultar, buscar y revisar funciones publicadas antes de iniciar una reserva.

## Responsable

PENDIENTE

## Responsabilidades

- Mostrar funciones publicadas.
- Buscar y filtrar.
- Mostrar el detalle de cada función.
- Mostrar disponibilidad actualizada.
- Revalidar precio y disponibilidad antes de reservar.
- Solicitar autenticación al iniciar una compra.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M4-01 | El sistema debe permitir que cualquier visitante consulte las funciones publicadas sin iniciar sesión. | MVP |
| RF-M4-02 | El visitante debe poder buscar y filtrar funciones por fecha, organización, sede, tipo de actividad y precio. | MVP |
| RF-M4-03 | El sistema debe mostrar el detalle de una función, incluyendo actividad, sede, sala, horario, precio, modalidad de aforo y disponibilidad actualizada. | MVP |
| RF-M4-04 | Al iniciar una reserva, el sistema debe comprobar nuevamente el precio y la disponibilidad y solicitar el inicio de sesión cuando el visitante todavía no esté autenticado. | MVP |

## Clases propias

Este módulo no introduce clases persistentes. Consulta `ActividadCultural`, `Funcion`, `Organizacion`, `Sede` y `Sala`. Los filtros y resultados pueden representarse con DTO.

## Reglas de negocio

1. Solo se muestran funciones publicadas o agotadas.
2. Una función agotada puede mostrarse, pero no ofrecerse para compra.
3. La disponibilidad mostrada es informativa hasta que M5 crea la reserva.
4. Una función cancelada debe desaparecer de la oferta comprable.
5. El visitante puede consultar sin cuenta.
6. Para reservar se requiere una cuenta de `Cliente`.
7. El MVP no incluye favoritos, planes ni recomendaciones automáticas.

## Flujos

### M4-A Consulta de cartelera

1. El visitante abre la cartelera.
2. Filtra las funciones.
3. Abre el detalle de una función.
4. El sistema muestra precio, ubicación y disponibilidad.
5. El visitante selecciona comprar.
6. El sistema revalida la información.
7. Si no existe sesión, solicita iniciar sesión.
8. Transfiere la función seleccionada a M5.

## Dependencias y contratos

- Expone `ICarteleraService` para consultar, buscar, filtrar y mostrar el detalle y la disponibilidad de funciones publicadas.
- Depende de M2 para datos de organización, sede y sala.
- Depende de M3 para actividades y funciones publicadas.
- Consulta a M5 para mostrar disponibilidad actualizada.
- Solicita a M1 la autenticación cuando un visitante inicia una compra.
- Transfiere a M5 la función seleccionada tras revalidar el precio y la disponibilidad.

## Riesgo principal

Consultas y filtros sobre funciones publicadas. Complejidad: baja.

## Estado de implementación

No iniciado.
