- # Asignatura | Desarrollo de Sistemas Informáticos
- # Institución | Universidad de La Laguna
- # Autor | Joel Francisco Escobar Socas
    - # Contacto | alu0101130408@ull.edu.es
- # __Práctica 2: Instalación y configuración de Visual Studio Code__
- ## Introducción
   Vamos a llevar a cabo la instalación y la configuración de Visual Studio Code el cual será el espacio de trabajo que usaremos para desarrollar las prácticas en esta asignatura.
- ## Desarrollo
  - ### Pasos Previos
  
    Antes de comenzar con la configuración lo que haremos será instalar el Visual Studio Code (conocido también como VSC o Visual ). En mi caso ya lo tenía instalado debido a que es el editor que uso en la mayor parte de las asignaturas debido a su potencia y su comodidad a la hora de usarlo. 
    - Para descargarlo puede usar el comando 
        ```
        $ sudo apt install code
        ``` 
    - También con el comando:
        ```
        $ sudo snap install code --classic
        ```
    - Otra alternativa, que fue la que yo use de hecho fue desde la tienda de Software de Ubuntu:
        ![Imagen de la herramienta de tienda](https://github.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct02-vscode-JoelEscobarULL/blob/main/P2_images/logo%20tienda.png?raw=true)
        
        Le damos a la "lupa" que es la herramienta de buscar y escribimos "visual studio code" 
        ![Imagen de la tienda de ubuntu](https://github.com/ULL-ESIT-INF-DSI-2021/ull-esit-inf-dsi-20-21-prct02-vscode-JoelEscobarULL/blob/main/P2_images/visual%20studio%20code.png?raw=true)
        
        Clickeamos encima del primero y le damos a "instalar" y se instalará automaticamente
    
    - O por el bien desde la propia página de Visual Studio Code: [Link a la página de descarga](https://code.visualstudio.com/download)
   
  - ### Configuración del SSH-Remote

    Una vez hayamos instalado y configurado el Visual Studio Code vamos a comenzar a aplicar la configuración de Visual Studio Code para conectarnos a nuestra máquina virtual del IaaS. Para hacerlo hay que tener en cuenta que en la práctica anterior teniamos que tener configurado el archivo `~/.ssh/config` y añadir a este archivo la máquina virtual de la asignatura, el archivo quedará al final similar a:
    ![Imagen SSH remote]()
    Una vez tengamos este archivo configurado en nuestra máquina local ahora tocará instalar en el Visual Studio una Extensión, Puede hacer uso de este [link](https://code.visualstudio.com/docs/editor/extension-gallery) si no sabe instalar extensiones dentro de visual studio. 
    Nos vamos a la sección de Extensions y buscamos "SSH-Remote" una extensión que permite conectarnos a una máquina virtual  que este en el `~/.ssh/config` y le damos al botón de 'install' una vez instalado seguimos estos pasos:
    1. Apretamos F1 en Visual Studio o bien ctrl + Shift + P.
    2. Una vez se nos abrá el menú lo que haremos será escribir ssh y le damos a la opción de "Configure SSH Hosts..."
    3. Seleccionamos nuestra máquina y nos conectaremos automaticamente
    Y lo que haremos será abrir la terminal de la nueva ventana que se ha abierto, para ello bastará con teclear `Ctrl + j` y dentro de la terminal escribimos `$ Hostname` y aparecerá la máquina a la que estamos conectados. 
    ![Imagen de hostname]().
  - ### Extensión de Live Share
    Ahora iremos a instalar la extensión de Live Share que permite compartir proyectos en tiempo real y como hicimos anteriormente nos vamos a la herramienta de "Extensions", escribimos Live Share y instalamos la primera extensión que aparece y le damos a "install".
    Además tener en cuenta que para instalar extensiones en la máquina local, primero tendrá que desconectarse de la máquina remota. Luego, podrá instalar las mismas extensiones en la máquina remota, si fuera necesario, volviendo a conectarse a la misma.

  - ### Primer Proyecto en TypeScript
    Antes de comenzar con el proyecto en si, lo que deberiamos hacer es instalar la extensión EsLint tal y como hemos instalados las otras extensiones, este extensión nos va a permitir realizar comprobaciones de estilo sobre ficheros que incluyan código fuente en JavaScript y TypeScript, una vez instalado, instalamos también el compilador de TypeScript usando npm con el comando:
    ```
    $ npm install --global typescript
    ```
    ![imagen npm install]()
    
    Una vez instalado ejecutamos los siguientes comandos en orden:
    ![imagen de los comandos para typescript]().
    
    El comando npm init --yes permite crear un fichero denominado package.json, el cual se usa para establecer las dependencias de desarrollo y ejecución del proyecto a modo de paquetes de los que depende el proyecto actual. 
    Vamos a abrir la carpeta, con la opción de `File` y luego `Open folder`o bien con la combinación de `Ctrl + K`y seleccionamos "hello-word" y se abrira una pestaña donde podemos ver el contenido en la parte del explorer, si por casualidad no lo tiene abierto, lo pueden abrir con la combinación `Ctrl + B`. Si no tenía un espacio de trabajo creado previamente, se creará uno nuevo y se añadirá el directorio al mismo. Guarde el espacio de trabajo seleccionando la opción `Save Workspace As...` del menú `File`, escriba un nombre de fichero y pulse el botón OK.
    Creamos un nuevo fichero con `Ctrl + N` y lo guardamos con `Ctrl + S`o bien podemos crearlo en el icono de una pagina con un + encima del nombre del espacio de trabajo en el explorer y le ponemos el nombre de `tsconfig.json`. o bien podemos hacer los siguientes comandos
    ```
    $ touch tsconfig.json
    $ vim tsconfig.json
    ```
    Y añadimos lo siguiente:
    ![imagen json config]()
    
    Básicamente, estas opciones de configuración le indican al compilador de TypeScript que:
    1. Queremos generar código compatible con uno de los últimos estándares de JavaScript
    2. Que el código JavaScript producto de la compilación se almacenará en un directorio `dist`.
    3. Que el código fuente escrito en TypeScript se encuentra en el directorio `src`.
    4. Que se indica un estándar para cargar código desde ficheros independientes
   
   En la terminal de Visual Studio Code (Ctrl + J) escriba los siguientes comandos:
   ![comandos iniciales]().
   Abrimos el fichero que acabamos de crear llamado "index.ts" y añadimos estas líneas de código en Type Script:
   ![codigo en type script]().
   Y lo compilamos en la terminal de VSC con el siguiente comando:
   ```
   $ tsc
   ```
   Tras la ejecución se abra creado la carpeta `dist`y el fichero index.js en el espacio de trabajo, ahora vamos a ejecutar en la terminal el siguiente comando:
   ```
   $ node dist/index.js
   ```
   Tras la ejecución obtendremos por salida de la terminal el "Hola mundo" que habiamos programado previamente con TypeScript en el espacio de trabajo
   ![resultado_hola mundo]().
    
    
- ## Dificultades Encontradas
  En mi caso la única dificultad que encontré fue una configuración que me olvide de linux, el cual fue modificar el ~/.ssh/config y añadir la máquina virtual al fichero, tras hacerlo queda algo así:
  (imagen ssh config)
- ## Bibliografía
  - [ULL](https://www.ull.es/) 
  - [Libro Essential TypeScript](https://learning.oreilly.com/library/view/essential-typescript-from/9781484249796/html/Part_1.xhtml)
  - [Github Pages](https://lab.github.com/githubtraining/github-pages)
  - [Introducción a Markdown](https://guides.github.com/features/mastering-markdown/)
  - [Visual Studio Code](https://code.visualstudio.com/)
  - [Github](https://github.com/)
  - [IaaS](https://iaas.ull.es/ovirt-engine/)
  - [Conexión SSH Remota en Visual Studio Code](https://code.visualstudio.com/docs/remote/ssh-tutorial)
  - [Tutorial Extensiones en Visual Studio Code](https://code.visualstudio.com/docs/editor/extension-gallery)
  - [Documentación LiveShare en Visual Studio Code](https://docs.microsoft.com/en-us/visualstudio/liveshare/)
