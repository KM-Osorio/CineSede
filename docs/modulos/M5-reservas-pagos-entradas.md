# M5: Reservas pagos y emisión de entradas

## Objetivo

Gestionar la reserva temporal de butacas o cupos, el pago simulado y la emisión de entradas sin sobreventa.

## Responsable

PENDIENTE

## Responsabilidades

- Seleccionar butacas o cantidades.
- Crear reservas temporales.
- Liberar disponibilidad al vencer.
- Registrar pagos simulados.
- Confirmar o rechazar códigos de pago.
- Emitir entradas únicas.
- Mostrar al cliente su historial de compras.
- Impedir sobreventa y duplicación.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M5-01 | Un cliente autenticado debe poder seleccionar butacas específicas en una función numerada o indicar una cantidad de entradas en una función de aforo general. | MVP |
| RF-M5-02 | El sistema debe crear una `Reserva` temporal con fecha de expiración y retener las butacas o cupos seleccionados durante ese periodo. | MVP |
| RF-M5-03 | Cuando una reserva expire, se cancele o no complete el pago, el sistema debe liberar automáticamente sus butacas o cupos. | MVP |
| RF-M5-04 | El sistema debe generar un código de pago simulado y registrar el resultado del intento. Un administrador con `SOPORTE_VENTAS` debe poder confirmar o rechazar el código registrado. | MVP |
| RF-M5-05 | Después de confirmar el pago, el sistema debe confirmar la reserva y emitir una entrada con código único por cada cupo comprado, asociándola con una butaca cuando corresponda. | MVP |
| RF-M5-06 | El sistema debe impedir que una misma confirmación genere entradas duplicadas y evitar que las reservas activas y entradas emitidas superen el aforo de la función. | MVP |
| RF-M5-07 | El cliente debe poder consultar el estado de sus reservas, pagos y entradas emitidas. | MVP |

## Clases propias

- `Reserva`
- `Pago`
- `Entrada`

Enums propios: `EstadoReserva`, `EstadoPago` y `EstadoEntrada`.

No se requieren `InventarioAforo`, `Orden`, `DetalleOrden`, `PoliticaCancelacion` ni `Reembolso` como clases separadas. La información mínima de cantidad, precio, total y estado permanece en `Reserva` y `Pago`.

## Reglas de negocio

1. En una función numerada, la reserva retiene butacas.
2. En una función general, la reserva retiene una cantidad de cupos.
3. La retención pertenece a `Reserva`, no a `Entrada`.
4. La reserva activa reduce temporalmente la disponibilidad.
5. Al expirar, cancelar o fallar el pago, la disponibilidad se libera.
6. Una entrada solo se emite después de confirmar el pago.
7. Una entrada se asocia con una butaca únicamente en modalidad numerada.
8. La confirmación del pago debe ser idempotente.
9. Las reservas activas y entradas emitidas no pueden superar el aforo.
10. EntreFunciones no almacena datos bancarios reales.

## Flujos

### M5-A Compra con butacas numeradas

1. El cliente selecciona una o varias butacas.
2. El sistema comprueba su disponibilidad.
3. Crea una reserva temporal y muestra el vencimiento.
4. Genera un código de pago simulado.
5. `SOPORTE_VENTAS` confirma o rechaza el código.
6. Si se confirma, el sistema confirma la reserva.
7. Emite una entrada por cada butaca.

### M5-B Compra de aforo general

1. El cliente indica la cantidad de entradas.
2. El sistema verifica que existan suficientes cupos.
3. Crea una reserva temporal por la cantidad.
4. Ejecuta el mismo flujo de pago simulado.
5. Emite una entrada por cada cupo confirmado, sin asociar butacas.

### M5-C Reserva expirada o pago rechazado

1. Vence la reserva o se rechaza el pago.
2. La reserva cambia a `EXPIRADA` o `CANCELADA`.
3. El sistema libera las butacas o cupos.
4. No emite entradas.

## Dependencias y contratos

- Expone `IGestionVentasService` para crear y vencer reservas, registrar y validar pagos simulados, y emitir, consultar y anular entradas.
- Depende de M1 para autenticar al cliente y autorizar `SOPORTE_VENTAS`.
- Depende de M2 y M3 para las butacas, la modalidad, el aforo y los datos vigentes de la función.
- Recibe de M4 la función seleccionada después de revalidar precio y disponibilidad.
- Proporciona a M4 la disponibilidad comercial actualizada.
- Proporciona a M6 las reservas, pagos y entradas necesarios para soporte y reportes.

## Riesgo principal

Vencimiento, concurrencia e idempotencia. Complejidad: alta.

## Estado de implementación

No iniciado.
