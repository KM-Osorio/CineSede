# Guía de contribución

Esta guía explica el flujo de trabajo de Git y GitHub para el equipo de CineSede. Todos los integrantes deben seguirlo para mantener el historial ordenado y evitar que una tarea sobrescriba el trabajo de otra persona.

## 1. Regla principal

- `main` contiene la versión integrada y estable del proyecto.
- Nadie debe ejecutar `push` directamente sobre `main`.
- Cada cambio se desarrolla en una rama de trabajo creada desde una versión actualizada de `main`.
- Toda rama de trabajo termina en un Pull Request dirigido a `main`.
- Al menos otro integrante debe revisar el Pull Request antes del merge.
- Las ramas de trabajo no se integran entre ellas. Cada una se incorpora directamente a `main` mediante su propio Pull Request.
- Después del merge, la rama de trabajo puede eliminarse.

`main` es la única rama permanente. No se deben crear ramas permanentes como `develop` o `release`.

## 2. Configuración inicial

Antes de realizar el primer commit, configura tu identidad de Git:

```bash
git config --global user.name "Nombre Apellido"
git config --global user.email "correo@ejemplo.com"
```

Cada integrante debe reemplazar los datos de ejemplo por el nombre y el correo asociados con su propia cuenta de GitHub. Esta configuración normalmente se realiza una sola vez por computadora.

## 3. Clonar el repositorio

Para descargar el proyecto por primera vez:

```bash
git clone https://github.com/KM-Osorio/CineSede.git
cd CineSede
```

La clonación se hace una sola vez por computadora. Para obtener cambios posteriores se utiliza `git pull`; no es necesario volver a clonar el repositorio.

## 4. Tipos de rama

Solo se permiten estos tres prefijos, respetando exactamente sus mayúsculas y minúsculas:

| Prefijo    | Uso                                                       | Ejemplo                            |
| ---------- | --------------------------------------------------------- | ---------------------------------- |
| `feature/` | Añadir una funcionalidad, documentación o mejora nueva    | `feature/m1-recuperacion-password` |
| `bugFix/`  | Corregir un error encontrado durante el desarrollo normal | `bugFix/m3-validacion-horario`     |
| `hotFix/`  | Corregir urgentemente un error crítico presente en `main` | `hotFix/m5-duplicacion-entradas`   |

Los nombres de las ramas deben:

- Usar minúsculas después del prefijo.
- Separar las palabras con guiones.
- Incluir el módulo cuando corresponda, por ejemplo `m1` o `m5`.
- Ser breves y descriptivos.

Para añadir documentación nueva se utiliza, por ejemplo:

```text
feature/docs-guia-git
```

Para corregir un error de documentación:

```text
bugFix/docs-corregir-enlace
```

No se debe utilizar el prefijo `docs/`.

## 5. Comenzar una tarea

Toda tarea comienza desde una versión actualizada de `main`:

```bash
git checkout main
git pull origin main
git checkout -b feature/m1-descripcion-corta
```

- El primer comando cambia a `main`.
- El segundo descarga los últimos cambios de `main`.
- El tercero crea la rama de trabajo y cambia hacia ella.

Para una corrección normal, el flujo equivalente es:

```bash
git checkout main
git pull origin main
git checkout -b bugFix/m3-descripcion-corta
```

Para una corrección crítica y urgente presente en `main`:

```bash
git checkout main
git pull origin main
git checkout -b hotFix/m5-descripcion-corta
```

Nunca se debe crear una rama nueva desde otra rama de trabajo.

## 6. Revisar y guardar cambios

Antes de crear un commit, revisa exactamente qué archivos y líneas cambiaste:

```bash
git status
git diff
git add ruta/del/archivo
git status
git commit -m "feat(m1): descripcion breve"
```

`git add ruta/del/archivo` prepara únicamente el archivo indicado. El comando `git add .` añade todos los cambios encontrados y solo debe utilizarse después de revisar cuidadosamente `git status` para confirmar que ningún archivo ajeno a la tarea será incluido.

Ejemplos de mensajes de commit:

```text
feat(m1): agregar recuperación de contraseña
fix(m3): corregir validación de horarios
docs: documentar flujo de ramas
refactor(m5): simplificar validación de entradas
test(m2): agregar pruebas de capacidad de sala
```

`bugFix` y `hotFix` son nombres de ramas. Los commits que corrigen errores normalmente utilizan el tipo `fix`.

## 7. Subir la rama

La primera vez que se sube una rama se ejecuta:

```bash
git push -u origin feature/m1-descripcion-corta
```

La opción `-u` vincula la rama local con la rama remota. En los siguientes envíos de esa misma rama bastará con:

```bash
git push
```

## 8. Crear el Pull Request

Después de subir la rama, crea el Pull Request en GitHub y comprueba que muestre:

```text
base: main
compare: feature/m1-descripcion-corta
```

Luego:

1. Completa la plantilla del Pull Request.
2. Explica qué cambió.
3. Indica cómo verificaste el cambio.
4. Solicita la revisión de al menos un compañero.
5. Resuelve las observaciones antes del merge.
6. No mezcles tareas distintas en el mismo Pull Request.

El código debe compilar y la aplicación debe ejecutarse sin errores antes del merge, cuando corresponda.

## 9. Corregir un Pull Request abierto

Si un compañero solicita cambios, corrígelos en la misma rama y ejecuta:

```bash
git status
git add ruta/del/archivo
git commit -m "fix: atender observaciones del pull request"
git push
```

No abras otro Pull Request. Los nuevos commits que subas a la misma rama aparecerán automáticamente en el Pull Request existente.

## 10. Después del merge

Cuando GitHub indique que el Pull Request fue integrado, actualiza tu copia local y elimina la rama local:

```bash
git checkout main
git pull origin main
git branch -d feature/m1-descripcion-corta
```

La rama remota puede eliminarse usando el botón `Delete branch` de GitHub.

## 11. Comandos de consulta

Estos comandos permiten revisar el estado del repositorio sin guardar cambios:

| Comando                          | Para qué sirve                                                       |
| -------------------------------- | -------------------------------------------------------------------- |
| `git status`                     | Muestra la rama actual y los archivos modificados o preparados.      |
| `git branch`                     | Lista las ramas locales e identifica la rama actual.                  |
| `git log --oneline --graph --all` | Muestra de forma compacta el historial y la relación entre ramas.     |
| `git diff`                       | Muestra los cambios que todavía no se han preparado para un commit.  |
| `git remote -v`                  | Muestra las direcciones configuradas para descargar y subir cambios. |

## 12. Acciones prohibidas

- No hacer `git push origin main`.
- No usar `git push --force`.
- No mezclar dos funcionalidades diferentes en una rama.
- No crear una rama nueva desde otra rama de trabajo.
- No subir contraseñas, tokens, credenciales ni archivos `.env`.
- No modificar el módulo de otra persona sin coordinarlo.
- Si aparece un conflicto, no borrar cambios a ciegas: detenerse y coordinar con el equipo.

## 13. Coordinación y seguridad

### Coordinación entre módulos

- Nadie debe modificar el módulo asignado a otro integrante sin coordinarlo previamente con esa persona.
- Los contratos, datos o interfaces compartidos entre módulos deben ser revisados y aprobados por todas las personas afectadas.
- Las decisiones que cambien el alcance o la arquitectura deben registrarse en `docs/DECISIONES.md`.

### Seguridad y limpieza del repositorio

No se deben subir:

- Contraseñas, tokens, claves o credenciales.
- Archivos con variables de entorno reales, incluidos los archivos `.env`.
- Archivos generados por compilación.
- Configuraciones personales del IDE.

Si una credencial o cualquier otro dato sensible se publica accidentalmente, se debe avisar inmediatamente al equipo y revocar o rotar la credencial. Eliminar el dato en un commit posterior no es suficiente porque seguirá presente en el historial.
