.. git

********************
GIT
********************

Existen herramientas que permiten tener un registro de las distintas
versiones de un conjunto de archios que se va modificando con el
tiempo.  Esto es muy útil para el desarrollo de códigos o de proyectos
de software.  Además de que permiten volver a versiones anteriores,
estos sistemas son muy útiles para tener una copia de respaldo usando
servicios en la nube y para compartir código fácilmente.

Los sistemas de control de versión son:

- Locales: sólo accesibles desde una PC local
- Centralizados: varias PC se conectan a un servidor central que
  guarda el historial completo
- Compartidos: varias PC guardan el historial completo

Para cada uno de esos sistemas hay herramientas o programas que lo
implementan:

- Locales: copias locales "a mano", RCS
- Centralizados: CVS, Subversion (SVN), Performance
- Compartidos: Git, Mercurial, Bazaar, Darcs

Usaremos GIT, que es uno de los más populares en la actualidad (por
ejemplo se usa para el desarrollo del kernel de Linux).

Existen además plataformas web o servicios de intranet para
administrar o almacenar los repositorios.  Ejemplos de servicios web
para GIT son: GitHub, GitLab, Assembla.  Usaremos GitHub.


Estados de los archivos en Git
==============================

En un área de trabajo (e.g., un directorio) que incluye control de
versión con Git, hay archivos en distintos estados:

- no incluidos en el control de version (untracked): forman parte del área de
  trabajo pero no del repositorio de Git.
- modificados: los archivos del repositorio que hay sido modificados
- marcados (staged): los archivos modificados que hay sido marcados
  para ser luego agregados a una nueva versión.
- sometidos (comitted): los archivos agregados a la base de datos en
  alguna versión.


Uso de Git
==========

Se puede usar Git de dos formas:

- Línea de comandos
- GUIs (incluyendo varios IDEs, como VSCODE o Spyder)

La línea de comandos ofrece todas las funcionalidades de Git, mientras
que en general las GUIs ofrecen algunas.


Instalación y configuración inicial
===================================

La instalación se realiza según el sistema (Linux, Windows, MacOS).

La configuración inicial se hace con el comando::

   $ git config

Las operaciones de red de Git usan un identificador de cada usuario,
por lo que lo pimero que hay que hacer es definir la identidad::

   $ git config --global user.name "John Doe"
   $ git config --global user.email johndoe@example.com

Otra cosa importante es el editor para interactuar con diferentes
pasos del proceso::

   $ git config --global core.editor vim

Se puede elegir el editor favorito, como vim, nano, emacs, gedit, etc.

Los parámetros de configuración se pueden ver con::

   $ git config --list



Git en línea de comandos
========================

Aquí veremos los comandos básicos para trabajar con Git.

Para obtener la ayuda::

   $ git help

y para un comando en particular::

   $ git help add
   $ git add -h

En general se inicia un repositorio clonando uno existente o creando
uno nuevo de manera local. Lo más fácil es crear un reposotorio en GitHub 
y luego clonarlo. Para ello::

   $ git clone URL

donde el URL es el correspondiente al proyecto en GitHub.


Para agregar archivos (pasar el área "staged")::

   $ git add archivo

Para agregar esos archivos a la base de datos del control de versión::

   $ git commit -m "mensaje"

Para saber el estado de los archivos::

   $ git status


Para obtener una lista de las versiones a las que se puede acceder::

   $ git log

Este comando devuelve los nombres de los commits (generados
automáticamente, mediante una HASH del tipo SHA1), 
como así también el autor, fecha y comentarios.
Una versión resumida que da solamente el nombre::

   $ git log --oneline

Se puede volver a una de las versiones identificadas con el ID del
commit::

   $ git checkout 833372b

Luego de revisar una versión anterior, se puede volver a la última
versión con::

   $ git checkout master

donde "master" es el nombre de la rama principal.  Si se quiere
desarrollar una versión "alternativa" del código, se puede hacer otra
rama.  Por ejemplo, supongamos que la lista de commits es la
siguiente (basado en el video de la clase)::

   46e89c8 (HEAD -> master, origin/master, origin/HEAD) Corregi errores de ortografia
   959f79a agrego prueba.py
   833372b Initial commit

queremos volver al segundo commit y hacer un desarrollo en paralelo::

   $ git checkout 959f79a
   $ git checkout -b remix


Una revisión completa de las funcionalidades de Git se puede encontrar
en el libro `Pro Git <https://git-scm.com/book/en/v2>`_.

