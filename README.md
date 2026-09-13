# Desarrollo del Sistema Web [EntreFunciones]

EntreFunciones es un proyecto universitario de Programación 3 para desarrollar, en equipo, una plataforma web que permita publicar actividades culturales y vender entradas de organizaciones pequeñas con una o varias sedes.

> **Nombre definitivo:** **EntreFunciones**, conforme al título del documento académico.

## Especificación funcional

La [especificación funcional](docs/ESPECIFICACION-FUNCIONAL.md) es una **V1 candidata para aprobación del equipo**. Define 29 requisitos funcionales distribuidos entre seis módulos.

El modelo mínimo identifica 15 clases de dominio y 1 enum administrativo central, `TipoRolAdministrativo`. El catálogo completo de estados y tipos de la especificación reúne 12 enums.

La primera entrega se conserva sin modificaciones en [docs/entrega-01/](docs/entrega-01/README.md). Esta especificación orienta el desarrollo futuro y no sustituye ni modifica los documentos originales de esa entrega.

## Módulos vigentes

- **M1:** [Gestión de cuentas roles y auditoría](docs/modulos/M1-cuentas-roles-auditoria.md).
- **M2:** [Gestión de organizaciones sedes y salas](docs/modulos/M2-organizaciones-sedes-salas.md).
- **M3:** [Gestión de actividades culturales y funciones](docs/modulos/M3-actividades-funciones.md).
- **M4:** [Cartelera y búsqueda de funciones](docs/modulos/M4-cartelera-busqueda.md).
- **M5:** [Reservas pagos y emisión de entradas](docs/modulos/M5-reservas-pagos-entradas.md).
- **M6:** [Soporte de ventas y reportes comerciales](docs/modulos/M6-soporte-reportes.md).

Consulta el [índice de módulos](docs/modulos/README.md) para revisar su distribución, clases propias y complejidad.

## Arquitectura exigida por el curso

- Backend desarrollado en **Java**.
- Frontend desarrollado en **C#**.
- Persistencia y componentes de base de datos en **SQL**.
- Comunicación entre frontend y backend mediante servicios **REST o SOAP**; la elección continúa pendiente.

Los frameworks, el sistema de compilación y la estructura interna del código aún están pendientes.

## Estructura principal

- [Backend Java](backend-java/README.md)
- [Frontend C#](frontend-csharp/README.md)
- [Base de datos](database/)
- [Documentación académica](docs/)
- [Especificación funcional](docs/ESPECIFICACION-FUNCIONAL.md)
- [Módulos](docs/modulos/README.md)
- [Alcance pendiente](docs/ALCANCE-PENDIENTE.md)
- [Decisiones](docs/DECISIONES.md)
- [Equipo](docs/EQUIPO.md)
- [Guía de contribución](CONTRIBUTING.md)

## Clonar el repositorio

Con GitHub CLI:

```bash
gh repo clone KM-Osorio/CineSede
cd CineSede
```

Con Git sobre HTTPS:

```bash
git clone https://github.com/KM-Osorio/CineSede.git
cd CineSede
```

El repositorio es privado, por lo que cada integrante debe tener acceso concedido y autenticarse en GitHub.
