********************
Empezando con python
********************

Para trabajar con python es recomendable usar entornos virtuales.  Las
instalaciones de Anaconda tienen también asociados entornos virtuales,
aunque la sintaxis es algo diferente.



Instalación de python
======================

Hay numerosos tutoriales que explican como instalar python.

Entre las opciones disponibles, las más populares son instalar python
desde el `repositorio oficial <https://www.python.org/>`_ o instalar
una distribución de `Anaconda <https://docs.anaconda.com/>`_.

Python es un lenguaje de alto nivel y de propósito general.

Anaconda es una distribución de python y de R que incluye muchas
herramientas para trabajar en ciencias de datos y en aprendizaje
automático.  Las distribuciones de Anaconda incluyen muchos paquetes
que posiblemente no necesitamos.

Todas las herramientas de Anaconda se pueden instalar desde python.

Manejadores de paquetes
==========================

El manejador de paquetes de Anaconda se llama `conda`, mientras que el
de python se llama `pip`.

Para instalar un paquete, por ejemplo `numpy <https://numpy.org/>`_::

   pip install numpy


Los paquetes de python forman parte de un repositorio de paquetes
llamado `pypi (Python Package Index)<https://pypi.org/>`_.  Allí se
pueden encontrar cientos de miles de paquetes par diferentes
propósitos.


Cómo preparar un entorno virtual
================================

Los entornos virtuales permiten experimentar con paquetes de python
sin riesgo de afectar al sistema en el que se está trabajando.
También permite tener diferentes entornos para trabajar con diferentes
versiones de python o de los paquetes.

Pare crear un entorno virtual, llamado "MyVE":

``virtualenv MyVE``

o bien, con las versiones más nuevas de python:

``python -m venv MyVE``

Una vez que está creado, se puede acceder al mismo ejecutando el
script "activate", que está ubicado en la carpeta creada:

``source MyVE/bin/activate``

Muchos proyectos tienen asociado un archivo que indica los paquetes
requeridos, usualmente se llama "requirements.txt":

``pip install -r requirements.txt``


Entornos virtuales con Anaconda
===============================

``conda create --name MyVE``

y para activarlo:

``conda activate MyVE``

Usando Anaconda se puede trabajar con una colección de entornos
virtuales, sin tener que acceder a las carpetas creadas para cada
entorno.  Por ejemplo, si tenemos dos entornos virtuales, podemos
pasar de uno a otro desde cualquier lugar:

``conda activate MyVE_1``

``conda activate MyVE_2``

`Más información sobre los entornos virtuales de anaconda <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#creating-an-environment-with-commands>`_

Esto también es posible con las instalaciones de python en el sistema
(sin anaconda) usando la herramienta virtualenvwrapper.

Virtualenvwrapper
=================

`virtualenvwrapper <https://virtualenvwrapper.readthedocs.io/en/latest/>`_ es un conjunto de extensiones de `virtualenv <https://pypi.org/project/virtualenv/>`_
que permiten administrar entornos virtuales y mejorar el flujo de
trabajo.

Los pasos a seguir son:

1. Crear una carpeta (oculta) donde se almacenarán las configuraciones
   de los EV::

      mkdir ~/.virtualenvs

2. Instalar los paquetes necesarios.  Por ejemplo en sistemas basados
   en Debian::

      apt install virtualenvwrapper
      pip install virtualenvswrapper

si no está el pip, instalar: (virtualenv y python-setuptools)::

      sudo apt install python3-pip

3. Editar el archivo del shell bash::

      export WORKON_HOME=$HOME/.virtualenvs
      export VIRTUALENVWRAPPER_VIRTUALENV=/usr/local/bin/virtualenv
      export VIRTUALENVWRAPPER_VIRTUALENV_ARGS='--no-site-packages'
      export VIRTUALENVWRAPPER_PYTHON=$(which python3)                                                                                      

Hay varias cosas que pueden fallar.  Aquí una breve lista de
resolución de problemas::

Que puede fallar:

1) virtualenvwrapper

   La ubicacion del script virtualenvwrapper.sh depende de la
   distribucion de linux:

   Mint:
   source /usr/local/bin/virtualenvwrapper.sh

   CBPP:
   source $HOME/.local/bin/virtualenvwrapper.sh


2) virtualenv

   en la variable VIRTUALENVWRAPPER_VIRTUALENV
   poner la ubicación de virtualenv:

   $ which virtualenv


3) python

   Si da este error:

    source $HOME/.local/bin/virtualenvwrapper.sh
   /usr/local/bin/python3: Error while finding module specification for 'virtualenvwrapper.hook_loader' (ModuleNotFoundError: No module named 'virtualenvwrapper')
   virtualenvwrapper.sh: There was a problem running the initialization hooks.

   If Python could not import the module virtualenvwrapper.hook_loader,
   check that virtualenvwrapper has been installed for
   VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3 and that PATH is
   set properly.

   probar hacer esto:

   reemplazar:
   export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3
   por:
   export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python


Más info:

- `Si da errores <https://stackoverflow.com/questions/33216679/usr-bin-python3-error-while-finding-spec-for-virtualenvwrapper-hook-loader>`_.

- `Command reference for wirtualenvwrapper <https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html>`_

- `Virtualenvwrapper readthedocs (Documentación) <https://virtualenvwrapper.readthedocs.io/en/latest/>`_



Cómo se usa:

* mkvirtualenv --python=$(which python3) MyVE
* lsvirtualenv
* workon MyVE
* rmvirtualenv MyVE



Repositorios y control de versión
=================================

Dos de las acciones más útiles a la hora de desarrollar códigos son
las de compartir y llevar un registro de versiones.

Para ello existen los llamados repositorios, que además de brindar una
ubicación en la nuba donde compartir códigos brindan distintas
herramientas.

Algunos de los repositorios más usados en la actualidad son:

- `GitHub <https://github.com/>`_
- `GitLab <https://gitlab.com/>`_
- `Assembla <https://www.assembla.com/home>`_
- `Anaconda Cloud <https://anaconda.org/>`_

Estos repositorios trabajan con `sistemas de control de versión <https://en.wikipedia.org/wiki/Version_control>`_, por
ejemplo:

- `GIT <https://git-scm.com/>`_
- `SVN <https://subversion.apache.org/>`_

En esta materia usaremos la combinación GitHub, que trabaja con GIT.



Usando git con GitHub
=====================


Un buen tutorial sobre `GitHub <https://guides.github.com/introduction/flow/>`_.


En la version simple, cuando solo un usuario edita:

1. git clone (one time only)
2. git pull
3. edit files
4. add files to the version control stack
5. commit changes
6. push changes
7. go to 2.

 

Varios usuarios:

1. git clone (one time only)
2. git pull
3. edit files
4. add files to the version control stack
5. before commit, git pull and resolve conflicts (if any)
5. commit changes
6. push changes
7. go to 2.

