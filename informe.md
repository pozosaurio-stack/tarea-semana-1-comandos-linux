# Práctica N.º 1: Comandos de Linux

**Estudiante:** Pedro Pozo  
**Semana:** 1  
**Fecha de ejecución:** 13 de octubre de 2026  
**Entorno utilizado:** Git Bash en Windows (Bash 5.2.37).

## 1. Título

Creación, copia, movimiento, redirección y eliminación de archivos mediante comandos de Linux.

## 2. Tiempo de duración

La ejecución de los pasos de creación y manipulación, junto con las primeras comprobaciones, registró **73 segundos (aproximadamente 1,2 minutos)** en la sesión de Git Bash. Este tiempo corresponde a la ejecución de los comandos; no incluye la elaboración del informe, la publicación en GitHub ni la grabación del audio.

## 3. Fundamentos

Los comandos de esta práctica se plantean para una terminal interactiva de Git Bash. Una terminal permite escribir instrucciones para trabajar con archivos y directorios. La organización de las carpetas ayuda a separar documentos, imágenes y scripts, mientras que las rutas indican dónde actúa cada instrucción. La shell interpreta esas instrucciones, sus argumentos y los operadores que relacionan su entrada y salida. [Manual de Bash](https://www.gnu.org/software/bash/manual/bash.html).

El comando `pwd` muestra la ubicación actual y `cd` cambia el directorio de trabajo. Esto permite interpretar correctamente las rutas relativas. `mkdir` crea carpetas; por ejemplo, `mkdir proyecto_comandos` crea el directorio principal. Después de entrar con `cd proyecto_comandos`, la instrucción `mkdir documentos imagenes scripts` crea las tres subcarpetas dentro de él. [Manual de Bash](https://www.gnu.org/software/bash/manual/bash.html) y [GNU: mkdir](https://www.gnu.org/software/coreutils/manual/html_node/mkdir-invocation.html).

El comando `echo` escribe texto en la salida estándar. Al agregar `>`, esa salida se dirige a un archivo: se crea si no existe y, normalmente, se reemplaza su contenido si ya existe. En cambio, `>>` añade texto al final. Por eso, para escribir tres líneas en `notas.txt`, se puede utilizar `>` en la primera y `>>` en las siguientes. [Manual de Bash](https://www.gnu.org/software/bash/manual/bash.html).

El comando `cp` copia un archivo y conserva el original. Así, `cp documentos/notas.txt scripts/backup_notas.txt` permite obtener una copia con otro nombre. Por su parte, `mv` cambia la ubicación o el nombre de un archivo; después de moverlo correctamente, deja de estar en su ubicación anterior. [Manual de GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html).

El comando `cat` envía el contenido de uno o varios archivos a la salida estándar. Con `cat documentos/notas.txt > documentos/resumen.txt`, ese contenido se escribe en otro archivo. El nombre “resumen” no significa que el comando resuma el texto: únicamente reproduce su contenido. [GNU: cat](https://www.gnu.org/software/coreutils/manual/html_node/cat-invocation.html).

El comando `rm` elimina archivos, como la copia temporal solicitada. `rmdir` elimina directorios vacíos y devuelve un error si contienen elementos. Esta diferencia permite elegir el comando adecuado para cada parte de la práctica. [Manual de GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html) y [GNU: rmdir](https://www.gnu.org/s/coreutils/manual/html_node/rmdir-invocation.html).

Finalmente, `history` muestra el historial disponible en la shell. En `history | tee tarea-s1-pedro_pozo.txt`, la tubería `|` conecta esa salida con la entrada de `tee`, que muestra los datos y los guarda. El historial registra comandos, pero no demuestra por sí solo que se ejecutaron correctamente; para comprobarlo hacen falta resultados y evidencias. [GNU: historial](https://www.gnu.org/s/bash/manual/html_node/Bash-History-Facilities.html) y [GNU: tee](https://www.gnu.org/s/coreutils/manual/html_node/tee-invocation.html).

![Estructura inicial y recorrido de los archivos](evidencias/01-estructura.svg)

*Figura 1. Diagrama conceptual de la estructura inicial y de las operaciones sobre la copia de notas.txt.*

![Redirecciones y tubería](evidencias/02-flujo-datos.svg)

*Figura 2. Diagrama conceptual de la redirección, la adición y la tubería con tee.*

## 4. Conocimientos previos

- Abrir una terminal y escribir un comando con sus argumentos.
- Reconocer la diferencia entre un archivo y un directorio.
- Comprender que una ruta relativa depende del directorio actual.
- Identificar el uso de las comillas para escribir texto con espacios.
- Utilizar un navegador y una cuenta de GitHub para entregar el repositorio.

## 5. Objetivos a alcanzar

1. Crear la estructura `proyecto_comandos` con las carpetas `documentos`, `imagenes` y `scripts`.
2. Crear un archivo de tres líneas, copiarlo, cambiar el nombre de la copia y moverla a otra carpeta.
3. Aplicar redirecciones para conservar y ampliar el contenido de un archivo, eliminar elementos y exportar el historial mediante una tubería.

## 6. Equipo necesario

- Computador con Windows.
- Git Bash instalado. La versión utilizada de Bash fue **5.2.37**.
- Git instalado, versión **2.53.0.windows.2**, para publicar el repositorio.
- Editor de texto compatible con Markdown.
- Navegador, conexión a Internet y cuenta de GitHub.
- Micrófono o teléfono para grabar el audio personal solicitado.

Git Bash proporciona Bash y herramientas de estilo Unix en Windows. Fue el entorno empleado; no se utilizó Ubuntu WSL en esta ejecución.

## 7. Material de apoyo

- Enunciado de la tarea autónoma de la semana 1, proporcionado en el aula virtual.
- [Plantilla del informe de la asignatura](https://github.com/maguaman2/informe-tendencias/blob/main/informe.md).
- [Manual de Bash](https://www.gnu.org/software/bash/manual/bash.html).
- [Manual de GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html).
- [Documentación de tee](https://www.gnu.org/s/coreutils/manual/html_node/tee-invocation.html).

## 8. Procedimiento

Se empleó una carpeta nueva de trabajo y una sesión interactiva de Git Bash con historial independiente. Los comandos siguientes corresponden a la ejecución registrada. Se mantuvo el nombre **`imagenes` sin tilde** en todas las rutas, tal como aparece en la creación de la estructura del enunciado.

Las figuras 1 y 2 son diagramas explicativos. Las figuras 3 a 6 muestran una transcripción visual del registro real de ejecución, presentada en un visor. Todas las imágenes tienen 800 píxeles de ancho.

### Paso 1. Crear la estructura de carpetas

```bash
mkdir proyecto_comandos
cd proyecto_comandos
mkdir documentos imagenes scripts
ls -R
```

Se comprobó la presencia de las tres subcarpetas dentro de `proyecto_comandos`. Desde este punto, los comandos de la práctica se ejecutaron dentro de esa carpeta.

### Paso 2. Crear notas.txt y escribir tres líneas

```bash
echo "Primera linea: creacion de archivos en Linux." > documentos/notas.txt
echo "Segunda linea: copia y movimiento de archivos." >> documentos/notas.txt
echo "Tercera linea: uso de redireccionamiento." >> documentos/notas.txt
cat documentos/notas.txt
```

El primer comando creó el archivo. Los dos siguientes añadieron líneas sin reemplazar las anteriores. Se usó texto sin tildes dentro de los archivos para simplificar su lectura en la terminal.

![Creación de carpetas y notas](evidencias/03-creacion.png)

*Figura 3. Registro de la creación de las carpetas y de las tres líneas de notas.txt.*

### Paso 3. Copiar, renombrar y mover el archivo

```bash
cp documentos/notas.txt scripts/backup_notas.txt
ls scripts
mv scripts/backup_notas.txt imagenes/
ls scripts imagenes
```

`cp` creó una copia con el nombre `backup_notas.txt`, manteniendo el original en `documentos`. Después, `mv` trasladó la copia a `imagenes`. La comprobación mostró el respaldo en `imagenes` y la carpeta `scripts` vacía.

![Copia y movimiento](evidencias/04-copia-movimiento.png)

*Figura 4. Registro de la copia con otro nombre y su traslado a imagenes.*

### Paso 4. Redireccionar y añadir contenido

```bash
touch documentos/resumen.txt
cat documentos/notas.txt > documentos/resumen.txt
echo "Cuarta linea: contenido agregado sin sobrescribir." >> documentos/resumen.txt
cat documentos/resumen.txt
wc -l documentos/notas.txt documentos/resumen.txt
```

`touch` creó el archivo vacío y la redirección copió en él el contenido de `notas.txt`. La última línea se añadió con `>>`. Se verificaron **tres líneas en notas.txt y cuatro en resumen.txt**. El archivo llamado `resumen.txt` contiene una copia ampliada; no se realizó un resumen automático del texto.

![Redirección y número de líneas](evidencias/05-redireccion.png)

*Figura 5. Contenido de resumen.txt y comprobación del número de líneas.*

### Paso 5. Eliminar el respaldo y la carpeta vacía

```bash
rm imagenes/backup_notas.txt
ls -A imagenes
rmdir imagenes
ls -R
```

Primero se eliminó el archivo de respaldo. `ls -A imagenes` no mostró elementos, lo que permitió comprobar que la carpeta estaba vacía. Después, `rmdir` la eliminó. El archivo original y `resumen.txt` permanecieron en `documentos`.

![Estado final de la práctica](evidencias/06-resultado-final.png)

*Figura 6. Eliminación del respaldo y estructura final de la práctica.*

### Paso 6. Guardar el historial utilizando una tubería

Desde `proyecto_comandos`, la instrucción de entrega es:

```bash
history | tee ../tarea-s1-pedro_pozo.txt
```

`history` produce la lista de comandos de la sesión y la tubería `|` la entrega a `tee`. Este último muestra la lista en la terminal y la guarda en el archivo situado un nivel por encima del proyecto. El nombre del archivo debe contener el nombre y apellido del estudiante.

El historial completo se exportó al archivo `tarea-s1-pedro_pozo.txt`. Incluye las comprobaciones y las exportaciones realizadas durante la práctica.

### Paso 7. Preparar el repositorio y el audio

El repositorio incluye el informe Markdown, el historial, las evidencias y los archivos resultantes. El audio se entrega aparte en el aula virtual, conforme al enunciado: debe ser un **MP3 de 60 segundos** que explique con palabras del estudiante lo aprendido.

## 9. Resultados esperados

Los resultados esperados y las comprobaciones de la ejecución fueron los siguientes:

| Comprobación | Resultado observado |
|---|---|
| Creación de documentos, imagenes y scripts | Las tres carpetas se crearon y se listaron. |
| Creación de notas.txt | Se verificaron tres líneas. |
| Copia con otro nombre | Se creó scripts/backup_notas.txt. |
| Movimiento del respaldo | La copia apareció en imagenes y dejó de estar en scripts. |
| Redirección y adición | resumen.txt conservó las tres líneas originales y añadió una cuarta. |
| Eliminación del respaldo | backup_notas.txt fue eliminado. |
| Eliminación de imagenes | rmdir se ejecutó después de comprobar que estaba vacía. |
| Historial mediante tubería | El historial real se guardó con history y tee. |

La estructura al terminar la práctica fue:

```text
proyecto_comandos/
├── documentos/
│   ├── notas.txt
│   └── resumen.txt
└── scripts/
```

**Nota sobre GitHub:** Git no versiona directorios vacíos. Después de terminar la práctica se añadió un archivo vacío `.gitkeep` en `scripts` únicamente para conservar esa carpeta en el repositorio. Este marcador no es parte de las operaciones de copia y movimiento.

La ejecución permite distinguir tres efectos: copiar conserva el archivo original, mover cambia la ubicación de un archivo y redireccionar controla dónde se escribe la salida de un comando. También se comprobó que `>>` agrega contenido y que `rmdir` se utiliza para directorios vacíos.

## 10. Bibliografía

- Free Software Foundation. (s. f.). *Bash reference manual*. https://www.gnu.org/software/bash/manual/bash.html
- Free Software Foundation. (s. f.). *GNU coreutils manual*. https://www.gnu.org/software/coreutils/manual/coreutils.html
- Free Software Foundation. (s. f.). *Redirections*. En *Bash reference manual*. https://www.gnu.org/software/bash/manual/html_node/Redirections.html
- Free Software Foundation. (s. f.). *Pipelines*. En *Bash reference manual*. https://www.gnu.org/software/bash/manual/html_node/Pipelines.html
- Free Software Foundation. (s. f.). *tee: Redirect output to multiple files or processes*. En *GNU coreutils manual*. https://www.gnu.org/s/coreutils/manual/html_node/tee-invocation.html
- maguaman2. (s. f.). *Plantilla de informe de práctica* [Repositorio de GitHub]. https://github.com/maguaman2/informe-tendencias
