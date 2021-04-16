# Platzi Downloader Tool

![Platzi Downloader Tool Preview](docs/images/platzi-downloader-menu.png)
Esta es una pequeña herramienta que hace mucho y que te ahorra una gran cantidad
de trabajo a la hora de descargar cursos de [**Platzi**](https://platzi.com)
## Instalaciones necesarias

*De momento solo se da referencia a la instalación en Sistemas GNU/Linux como
Debian GNU/Linux, Ubuntu, ArchLinux*

* **python 3.x.x**
    >Instalación en Debian GNU/Linux o Ubuntu
  
    Ejecuta: ```sudo apt-get install python3```
    
    >Instalación en ArchLinux y Manjaro
  
    Ejecuta: ```sudo pacman -S python```
  
    >Instalación en otros sistemas operativos o distribuciones
  
    Ingresa al [Sitio Oficial de Python](https://www.python.org/)
  
    Puedes ver esta [guia para Windows](https://tutorial.djangogirls.org/es/python_installation/) <br>


* **pip**
    >Instalación en Debian GNU/Linux o Ubuntu
  
    Ejecuta: ```sudo apt-get install python3-pip ```

    >Instalación en ArchLinux y Manjaro
  
    Ejecuta: ```sudo pacman -S python-pip```

    >Para otros sistemas operativos o distribuciones de GNU/Linux busca en Internet
    
    Puedes revisar esta [guia para Windows](https://www.liquidweb.com/kb/install-pip-windows/) <br>


* **youtube-dl**
    >Instalación en Debian GNU/Linux o Ubuntu
  
    Ejecuta: ```sudo apt-get install youtube-dl```
  
    >Instalación en ArchLinux y Manjaro
  
    Ejecuta: ```sudo pacman -S youtuble-dl```

    >Instalación en otros sistemas o plataformas
  
    Ingresa al sitio oficial de [youtube-dl](https://youtube-dl.org/) para más información sobre
    instalaciones. <br><br>

    Si realizas la instalación en Windows asegurarte de agregar el programa a la variable
    **PATH**, de este modo no se generaran problemas. <br><br>

    Para no tener problemas de dependencias es recomendable instalar la dependencia *python-pycryptodome*<br>


* **ffmpeg**
    >Instalación en Debian GNU/Linux o Ubuntu
  
    Ejecuta: ```sudo apt-get install ffmpeg```

    >Instalación en ArchLinux y Manjaro
  
    Ejecuta: ```sudo pacman -S ffmpeg```
  
    <br><br>
  
    ***Tip:** Si algo falla al momento de la instalación prueba actualizar los repositorios de tu distro*
  
## Instalación de módulos python necesarios
Los pasos de instalación que se muestran son probados solo en sistemas GNU/Linux
no es seguro que funcionen si tiene un sistema operativo diferente como Windows.

* **requests**
    >Ejecuta: ```pip3 install requests```
  
* **lxml**
    >Ejecuta ```pip3 install lxml```
  
* **colorama**
    >Ejecuta ```pip3 install colorama```
  
  
*Si al momento de la descarga te da un error prueba verifica si los módulos `json` y `re` 
están correctamente instalados.*

## Modo de empleo
**Clic para abrir el video**
[![alt text](https://raw.github.com/Devil64-Dev/platzi-dtool/master/docs/poster.png)](https://raw.github.com/Devil64-Dev/platzi-dtool/master/docs/guide.mp4)

***Notas:*** <br>
El archivo `cookies.txt` debe guardarse en la carpeta donde se encuentra el scipt
`platzi-dtool.py` para que el programa no genere errores.

Debido a que no tengo una suscripción en platzi no puede comprobar si el modo de descarga
masiva de cursos funciona correctamente, si hay algún error estén atentos que tan pronto
comienza el platzi day se corregirán lo antes posible.

Recomiendo que no descarguen los cursos en la carpeta donde se encuentra el programa
y el resto de archivos, creen una nueva carpeta limpia para que no tengan problema alguno.

**IMPORTANTE: Recomiendo que descarguen varios cursos a la vez, de ese modo puede aprovechar el maximo de la velocidad de descarga que brinde vuestra red.**

## Estructura de los directorios usados
Aquí una breve explicación de los directorios que se crearan y usaran para guardar los
cursos descargados.

* **Descargando una ruta de aprendizaje o escuela**
    
    Cuando se realizan este tipo de descargas se genera la siguiente estructura 
    de directorios:
  
        Convensiones usadas:
            [CN] = Digitos que se usan para numerar los cursos para que queden ordenados

            [COURSE_NAME] = Nombre del curso.

            [SN] = Numero de seccion, digito que permite ordenar una seccion

            [SECTION_NAME] = Se refiere al nombre de la sección dentro del curso

            [LN] = Numero que identifica a una leccion dentro de una seccion
  
            [LESSON_NAME] = Nombre de la leccion

    **Jerarquía de directorios**
    
    El número uno en la jerarquía es la carpeta del curso, la cual se nombre de la
    siguiente manera:<br>
  
        [CN] - [COURSE_NAME]

    Esto se hace para que se puedan ordenar y saber cual curso es él siguiente cuando se
    descargan rutas o escuelas de aprendizaje.
  
    Dentro de la carpeta del curso encontramos lo siguiente
  
        [CN] - [COURSE_NAME]
            [SN] - [SECTION_NAME]

    La estructura anterior hace referencia una sección dentro de un curso. Las secciones 
    van enumeradas para que se pueda saber que sección es primero y cual es última. <br><br>
  
    La siguiente estructura es:
  
        [CN] - [COURSE_NAME]
            [SN] - [SECTION_NAME]
                [LN] - [LESSON_NAME]
    
    La estructura anterior hace referencia a una lección que se encuentra contenida dentro de
    una sección la cual a su vez está contenida dentro de un curso. <br><br>
    Las lecciones se enumeran para que se puedan ordenar y se pueda saber con cual continuar, 
    el nombre de la lección en algunos casos no puede ser exacto, ya que algunos caracteres se reemplazan por otros
    o se eliminan para tener mayor compatibilidad un ejemplo es el caso del carácter `:`, que se reemplaza
    por la cadena ` -` (espacio + -). <br><br>
  
    La siguiente estructura se usa para almacenar la página de la lección, ya que en algunos
    casos esta contiene información como enlaces a otros recursos o resúmenes de la lección.
  
        [CN] - [COURSE_NAME]
            [SN] - [SECTION_NAME]
                [LN] - [LESSON_NAME]
                [LN] - extra_files

    Ya que algunas lecciones no son videos, se descargara la página web, la cual contiene
    el contenido de la lección tal como esta y se puede ver de forma offline, aunque se requiere 
    conexión a Internet para cargar imagines. <br><br>
  
    Cuando se descarga una lección de video, se descargara una página web, la cual es
    la página que se encuentra en la url de la clase, dicha página tiene el siguiente nombre.
  
        Estando en:
            [LN] - extra_files
                [LN] - webpage.html

    Otro archivo que se encontrará es un archivo llamado `000 - Preview.html`,
    este archivo se encuentra en la carpeta del curso, y se trata de la página del curso, 
    la puedes usar para saber cierta información del curs y también para saber como se estructura
    el curso aunque no haga falta.
  

* **Descargando un solo curso**
    
    Cuando en el archivo que contiene la información de la descarga solo hay un curso
    la carpeta de este curso no contiene una numeración solamente el nombre.
  
        [COURSE_NAME]
            [SN] - [SECTION_NAME]
                [LN] - [LESSON_NAME]
                [LN] - extra_files
  
    De tal modo la estructura del curso será como la siguiente.

Con eso se concluye la explicación de los directorios usados por las descargas.

## Recomendaciones de uso
* **Sistema operativo**
  
    Este programa fue probado en ArchLinux, pero puedo sugerir que se ejecutara sin problemas
    en cualquier otra distribución de Linux siempre que se tengan los programas y los módulos de
    python correctamente instalados. <br><br>
  
    *Puedes probar en Windows aunque no estoy muy seguro de que funcione bien, debido
    a que usa un sistema de archivos diferente a los sistemas de archivos Unix. <br>
    Si lo probaste y ocurrió algún error puedes abrir una discusión y poner la salida de la ejecución
    de ese modo podre arreglarlo rápidamente y dar soporte a usuarios de Windows*
  

* **Descargando**
    
    Si la descarga se pausa y no avanza más presiona `CTL + C` solo una vez, de este modo la descarga
    volverá a iniciarse y retomar desde el punto en el que encontraba. <br><br>
    Puedes usar `CTL + C` tantas veces que quieras pero solo si se está descargando
    un video sabras que se está descargando cuando ves un texto que dice "Status: Downloading video" or algo
    similar.<br><br>
  
    En carro de que la descarga se interrumpa, esta volverá a reiniciarse hasta que se haya
    descargado por completo, así que no tendrás problemas con esto.
    
  
## Solución de problemas
Si te genera un problema al momento de correr el programa abre el archivo _utils/text_utils.py_
y en la línea 6 deberás ver algo como esto: `TERMINAL_COLUMNS = os.get_terminal_size().columns`
cambia su valor a 80 o un número cercano a este.

Si estas en Windows y experimentas problemas con la creación y guardado de archivos,
puedes abrir una discusión y pones la salida del error, de ese modo me ayudaras a arreglar el error rápidamente.

## Información extra
Las herramientas usadas en el programa no son de mi propiedad, son herramientas de código
libre que llevan años funcionando aquí la lista de los programas que he usado:

* [**youtube-dl**](https://youtube-dl.org/)
* [**ffmpeg**](https://ffmpeg.org/)
* [**python**](https://www.python.org/)
* [**pip**](https://pypi.org/project/pip/)
 

Si te gusto el programa puedes darle una estrella.<br>
Si tienes alguna idea de como mejorar el programa, puedes abrir una discusión y comentar, tal vez
se pueda hacer algo. <br><br>


Esta herramienta la cree debido a que mi conexión a Internet es realmente mala y solo está
algo decente en horas de la noche, en las cuales ya no es posible aprovecharla debido al cansancio o al sueño. <br>
Me gusta mucho aprender pero trasnochar todos los días no es bueno para el cuerpo y la mente,
por eso me dije y si descargo las clases mientras duermo?, y así se creó este en 7 Dias xD

Ente proyectó no se hizo con intensiones de Piratería, ya que es solo una herramienta
para las personas que no pueden cuentan con una conexión a Internet estable y de este modo
pueden descargar las clases y verlas cuando quieran con más comodidad.