# Guía de contribución

## Flujo de trabajo

1. La rama `main` debe mantenerse estable.
2. Cada tarea debe trabajarse en una rama separada creada desde una versión actualizada de `main`.
3. Las ramas deben seguir uno de estos formatos:
   - `feature/m1-descripcion`
   - `fix/m3-descripcion`
   - `docs/descripcion`
4. Todo cambio debe incorporarse mediante un pull request.
5. Antes de integrar código, este debe compilar y ejecutarse sin errores.

## Coordinación

- Nadie debe modificar el módulo asignado a otro integrante sin coordinarlo previamente con esa persona.
- Los contratos, datos o interfaces compartidos entre módulos deben ser revisados y aprobados por todas las personas afectadas.
- Las decisiones que cambien el alcance o la arquitectura deben registrarse en `docs/DECISIONES.md`.

## Seguridad y limpieza del repositorio

No se deben subir:

- Contraseñas, tokens, claves o credenciales.
- Archivos con variables de entorno reales.
- Archivos generados por compilación.
- Configuraciones personales del IDE.

Si un dato sensible se publica accidentalmente, debe avisarse inmediatamente al equipo y revocarse o rotarse la credencial; eliminarlo en un commit posterior no basta.

## Pull requests

Cada pull request debe tener un alcance acotado, completar la plantilla establecida e indicar cómo se verificó el cambio. Las observaciones de revisión deben resolverse antes de integrar el cambio en `main`.
