# M1: Gestión de cuentas roles y auditoría

## Objetivo

Gestionar el registro de clientes, la autenticación, las cuentas administrativas, sus responsabilidades, alcances y auditoría.

## Responsable

PENDIENTE

## Responsabilidades

- Crear clientes mediante el registro público.
- Iniciar y cerrar sesión.
- Recuperar el acceso a una cuenta.
- Mantener cuentas de clientes y administradores.
- Crear cuentas administrativas.
- Asignar y revocar responsabilidades administrativas.
- Aplicar el alcance organizacional.
- Registrar operaciones administrativas críticas.

## Requisitos funcionales

| ID | Requisito | Prioridad |
|---|---|---|
| RF-M1-01 | El sistema debe permitir que un visitante registre una cuenta con nombre, correo y contraseña, creando exclusivamente una cuenta de tipo `Cliente`. | MVP |
| RF-M1-02 | El sistema debe permitir que clientes y administradores inicien y cierren sesión, y recuperen el acceso mediante su correo registrado. | MVP |
| RF-M1-03 | Un administrador con `GESTION_CUENTAS` debe poder buscar, bloquear, reactivar y desactivar cuentas de clientes y administradores. | MVP |
| RF-M1-04 | Un administrador con `GESTION_CUENTAS` debe poder crear cuentas administrativas y asignar o revocar sus responsabilidades. `ORGANIZADOR` debe vincularse con una organización. | MVP |
| RF-M1-05 | El sistema debe restringir las operaciones según el tipo y alcance de la asignación administrativa, y registrar en `RegistroAuditoria` los cambios de cuentas y responsabilidades. | MVP |

## Clases propias

- `Usuario`
- `Cliente`
- `Administrador`
- `AsignacionRolAdministrativo`
- `RegistroAuditoria`

Enums propios: `EstadoUsuario` y `TipoRolAdministrativo`.

## Reglas de negocio

1. El correo debe ser único entre las cuentas activas.
2. La contraseña se almacena mediante un mecanismo de protección; nunca como texto original.
3. El registro público crea solamente cuentas de `Cliente`.
4. Las cuentas de `Administrador` se crean internamente.
5. Un administrador puede tener varias asignaciones activas.
6. `ORGANIZADOR` requiere una organización como alcance.
7. Una cuenta bloqueada o desactivada no puede iniciar nuevas sesiones.
8. Cada operación debe comprobar el tipo de rol y su alcance.
9. Los cambios de cuenta o asignación deben quedar auditados.

## Flujos

### M1-A Registro de cliente

1. El visitante ingresa nombre, correo y contraseña.
2. El sistema valida el formato y la unicidad del correo.
3. Crea una cuenta de tipo `Cliente`.
4. El cliente inicia sesión.

**Resultado:** cliente autenticado, sin responsabilidades administrativas.

### M1-B Mantenimiento de cuentas administrativas

1. Un administrador con `GESTION_CUENTAS` busca una cuenta o crea un administrador.
2. Selecciona una responsabilidad administrativa.
3. Si selecciona `ORGANIZADOR`, elige la organización correspondiente.
4. El sistema guarda `AsignacionRolAdministrativo`.
5. Registra al responsable, la fecha y el cambio en `RegistroAuditoria`.

**Resultado:** facultad administrativa asignada sin crear otro tipo de usuario.

## Dependencias y contratos

- Expone `IGestionCuentasService` para registrar clientes, autenticar, recuperar acceso, mantener cuentas administrativas, asignar responsabilidades, consultar autorizaciones y registrar auditoría.
- Depende de M2 para validar la organización obligatoria que delimita una asignación `ORGANIZADOR`.
- Proporciona autenticación y autorización por responsabilidad y alcance a M2, M3, M4, M5 y M6.
- Registra las operaciones administrativas críticas y las correcciones comerciales indicadas por M6.

## Riesgo principal

Autorización por responsabilidad y alcance. Complejidad: media.

## Estado de implementación

No iniciado.
