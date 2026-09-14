# M6: Soporte de ventas y reportes comerciales

## Objetivo

Atender incidencias ocurridas dentro del proceso de compra y generar reportes comerciales, sin administrar el acceso ni la asistencia al evento.

## Responsable

PENDIENTE

## Responsabilidades

- Recibir problemas reportados desde el historial de compra.
- Revisar la reserva, el pago y las entradas relacionadas.
- Asignar y resolver incidencias.
- Reemitir o anular entradas cuando exista un error de plataforma.
- Registrar devoluciones simuladas.
- Auditar correcciones manuales.
- Mostrar reportes comerciales al organizador.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M6-01 | El cliente debe poder reportar una incidencia relacionada con una reserva, pago o entrada desde su historial de compras. La incidencia debe quedar vinculada con la reserva. | MVP |
| RF-M6-02 | Un administrador con `SOPORTE_VENTAS` debe poder consultar las incidencias, asignarse como responsable, cambiar su estado y registrar su resolución. | MVP |
| RF-M6-03 | Cuando se compruebe un error de la plataforma, `SOPORTE_VENTAS` debe poder reemitir una entrada, anular una entrada incorrecta o registrar una devolución simulada. | MVP |
| RF-M6-04 | El sistema debe registrar en la auditoría las confirmaciones manuales de pagos, anulaciones, reemisiones y devoluciones simuladas. | MVP |
| RF-M6-05 | El organizador debe poder consultar reportes de entradas vendidas, ingresos y ocupación comercial de sus organizaciones, filtrados por sede, función y periodo. | MVP |

## Clases propias

- `IncidenciaCompra`

Enums propios: `TipoIncidenciaCompra`, `EstadoIncidencia` y `TipoSolucionIncidencia`.

Los reportes son consultas o DTO calculados; no requieren las clases `HechoVenta`, `HechoAsistencia`, `Indicador`, `SolicitudReporte` ni `ReporteGenerado`.

## Reglas de negocio

1. La incidencia se vincula con una reserva.
2. Desde la reserva se consultan el pago y las entradas relacionadas.
3. El cliente solo puede reportar problemas de sus propias compras.
4. `SOPORTE_VENTAS` es la única responsabilidad que permite ejecutar correcciones comerciales.
5. Toda corrección manual debe registrar responsable, fecha, motivo y resultado.
6. La devolución es simulada y no ejecuta una transferencia bancaria.
7. El organizador consulta únicamente sus organizaciones asignadas.
8. Los reportes utilizan pagos confirmados y entradas emitidas.
9. No se registran check-in, asistencia ni incidentes del evento.

## Flujos

### M6-A Atención de una incidencia

1. El cliente abre una reserva desde su historial.
2. Selecciona reportar un problema y registra su descripción.
3. El sistema crea `IncidenciaCompra`.
4. `SOPORTE_VENTAS` revisa la reserva, el pago y las entradas.
5. Registra la solución.
6. Si corresponde, confirma el pago, reemite o anula una entrada, o registra una devolución simulada.
7. El sistema audita la acción y comunica el resultado.

### M6-B Reporte comercial

1. El organizador selecciona organización, periodo, sede o función.
2. El sistema valida su asignación.
3. Calcula entradas vendidas, ingresos confirmados y ocupación comercial.
4. Muestra el resultado.

## Dependencias y contratos

- Expone `ISoporteVentasService` para registrar y resolver incidencias, aplicar las correcciones permitidas y consultar reportes comerciales.
- Depende de M1 para autorizar `SOPORTE_VENTAS` y `ORGANIZADOR`, comprobar alcance y registrar auditoría.
- Depende de M2 para validar la organización, sede y alcance de los reportes.
- Depende de M5 para consultar reservas, pagos y entradas, y para confirmar pagos, reemitir o anular entradas y registrar devoluciones simuladas.

## Riesgo principal

Correcciones auditadas y límites de alcance. Complejidad: media.

## Estado de implementación

No iniciado.
