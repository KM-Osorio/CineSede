# M2: Gestión de organizaciones sedes y salas

## Objetivo

Registrar y mantener organizaciones, sedes, salas y mapas de butacas, respetando el alcance de cada organizador.

## Responsable

PENDIENTE

## Responsabilidades

- Registrar, verificar, activar y suspender organizaciones.
- Mantener la información de las organizaciones.
- Registrar y desactivar sedes.
- Registrar salas y su aforo máximo.
- Configurar butacas numeradas.
- Restringir cada cambio a la organización autorizada.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M2-01 | Un administrador con `GESTION_ORGANIZACIONES` debe poder registrar, verificar, activar, suspender y consultar organizaciones. | MVP |
| RF-M2-02 | Un administrador con `ORGANIZADOR` debe poder consultar y modificar únicamente las organizaciones que tenga asignadas. | MVP |
| RF-M2-03 | El organizador debe poder registrar, modificar y desactivar las sedes y salas de su organización, indicando dirección, nombre y aforo máximo. | MVP |
| RF-M2-04 | El organizador debe poder configurar las butacas de una sala indicando código, fila y número, sin permitir identificadores repetidos dentro de esa sala. | MVP |

## Clases propias

- `Organizacion`
- `Sede`
- `Sala`
- `Butaca`

Enum propio: `EstadoOrganizacion`.

## Reglas de negocio

1. Una organización puede tener varias sedes.
2. Una sede pertenece a una sola organización.
3. Una sala pertenece a una sola sede.
4. El aforo máximo de una sala debe ser positivo.
5. Una butaca pertenece a una sala.
6. El código de butaca es único dentro de la sala.
7. `ORGANIZADOR` controla todas las sedes de las organizaciones indicadas en sus asignaciones.
8. La desactivación no elimina el historial.
9. Este módulo no administra recursos técnicos, alquileres ni bloqueos de disponibilidad.

## Flujos

### M2-A Configuración de una organización

1. `GESTION_ORGANIZACIONES` registra y habilita la organización.
2. `GESTION_CUENTAS` asigna `ORGANIZADOR` a un administrador y establece su alcance.
3. El organizador registra una sede.
4. Registra sus salas y el aforo máximo.
5. Si la sala utiliza asientos numerados, configura las butacas.

**Resultado:** infraestructura disponible para programar funciones.

## Dependencias y contratos

- Expone `IGestionOrganizacionesService` para mantener organizaciones, sedes, salas y butacas, y consultar espacios configurados.
- Depende de M1 para comprobar `GESTION_ORGANIZACIONES`, `ORGANIZADOR` y el alcance organizacional.
- Proporciona a M1 las organizaciones que pueden delimitar asignaciones.
- Proporciona a M3 salas, aforos y butacas configuradas.
- Proporciona a M4 la organización, sede y sala que se muestran y filtran en cartelera.

## Riesgo principal

Jerarquía organización, sede, sala y butaca. Complejidad: media.

## Estado de implementación

No iniciado.
