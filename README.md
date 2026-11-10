# Sistema de gestión de horarios académicos

Aplicación web para cargar y consultar los horarios de clases de una institución educativa. Avisa cuando un aula o un profesor quedan superpuestos, muestra la semana completa y calcula cuántas horas se usa cada aula y cada profesor.

**Demo:** https://zoecorva.github.io/Sistema-de-Gesti-n-de-Horarios-Acad-micos/ (disponible cuando se activa GitHub Pages, ver más abajo)

<!-- Agregá acá una captura de pantalla: ![Vista semanal](captura.png) -->

## Qué se puede hacer

- **Crear, editar y borrar horarios** con materia, profesor, aula, día, hora de inicio y hora de fin.
- **Detectar conflictos:** no deja guardar una clase si el aula o el profesor ya están ocupados en ese día y horario, y explica con qué clase choca.
- **Ver la semana** de lunes a sábado, con filtros por profesor y por aula.
- **Ver estadísticas** de horas semanales por aula y por profesor.
- **Importar y exportar CSV**, para trabajar con planillas de Excel o Google Sheets.
- **Cargar datos de ejemplo** para probar la aplicación al instante.

## Cómo usarla

Abrí `index.html` en el navegador. No necesita instalar nada ni tener un servidor.

Los horarios se guardan en el navegador (`localStorage`), así que no se pierden al cerrar la página, pero solo se ven en el mismo navegador y dispositivo. Para pasarlos a otro lado, usá **Exportar CSV**.

### Formato del CSV

La primera fila tiene que tener estas columnas, en cualquier orden:

```
materia,profesor,aula,dia,horaInicio,horaFin
Matemática I,Prof. Gómez,Aula 101,Lunes,08:00,10:00
```

Se aceptan comas o punto y coma como separador (el que usa Excel en Argentina). Las filas con datos inválidos o con conflictos se omiten y la aplicación informa cuántas fueron.

## Cómo funciona la detección de conflictos

Dos clases chocan si pasan el mismo día, se superponen en el tiempo y comparten aula o profesor. Dos intervalos se superponen cuando cada uno empieza antes de que termine el otro:

```js
inicioA < finB && finA > inicioB
```

Una clase que termina a las 10:00 y otra que empieza a las 10:00 no se consideran superpuestas.

## Publicarla con GitHub Pages

1. Subí `index.html` y este `README.md` a la raíz del repositorio.
2. Entrá a *Settings → Pages*.
3. En *Source* elegí *Deploy from a branch*, la rama `main` y la carpeta `/ (root)`.
4. Esperá unos minutos y abrí el link que aparece en esa misma pantalla.

## Tecnologías

HTML, CSS y JavaScript sin librerías. Los datos se guardan con `localStorage`.

## Limitaciones y próximos pasos

- No hay usuarios ni roles: cualquiera que abra la página puede editar los horarios de su navegador.
- Solo gestiona horarios de clases; faltan exámenes y actividades extracurriculares.

Ideas para seguir:

- Login con roles de administrador, profesor y estudiante.
- Un servidor con Node.js, Express y MongoDB para guardar los datos en la nube y compartirlos entre usuarios.
- Exportar el horario a PDF o a Google Calendar.
- Tests automáticos para la detección de conflictos.

## Autora

Zoe Micaela Corvalán · [GitHub](https://github.com/zoecorva) · [LinkedIn](https://www.linkedin.com/in/zoecorva99/) · zoecorva99@hotmail.com
