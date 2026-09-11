# CineSede

CineSede es un proyecto universitario de Programación 3 para desarrollar, en equipo, una aplicación web transaccional vinculada con la gestión y operación de una plataforma cinematográfica.

> **Nombre pendiente de confirmación:** “EntreFunciones” fue el nombre utilizado en la primera entrega. El equipo todavía debe confirmar si el nombre definitivo será **CineSede** o **EntreFunciones**.

## Estado actual

El proyecto se encuentra en la etapa de **definición y revisión del alcance**. Esta plantilla organiza el trabajo colaborativo, pero no incorpora funcionalidades ni decisiones tecnológicas aún no confirmadas.

No debe asumirse que todos los requisitos propuestos o candidatos formarán parte del alcance final. Solo deben implementarse requisitos después de que hayan sido revisados y confirmados por el equipo conforme a los lineamientos del curso.

## Módulos

- **M1:** Identidad, acceso y seguridad.
- **M2:** Organizaciones, sedes, salas y recursos.
- **M3:** Propuestas, curaduría y programación.
- **M4:** Cartelera, descubrimiento y guía cultural.
- **M5:** Comercio, reservas, pagos y entradas.
- **M6:** Operación, control de acceso y analítica.

## Arquitectura exigida por el curso

- Backend desarrollado en **Java**.
- Frontend desarrollado en **C#**.
- Persistencia y componentes de base de datos en **SQL**.
- Comunicación entre frontend y backend mediante servicios **REST o SOAP**; la elección está pendiente.

Los frameworks, el sistema de compilación y la estructura interna del código aún no están definidos.

## Estructura principal

- [Backend Java](backend-java/README.md)
- [Frontend C#](frontend-csharp/README.md)
- [Base de datos](database/)
- [Documentación académica](docs/)
- [Módulos](docs/modulos/)
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
