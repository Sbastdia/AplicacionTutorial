# django_tutorial
Tutorial django: https://docs.djangoproject.com/en/3.1/intro/tutorial01/

En cada carpeta hay un fichero .txt con el paso a paso de cada ejercicio.
A continuación, escribo el enunciado de cada ejercicio.

TAREA 1: Entorno de desarrollo

Vamos a desarrollar la aplicación del tutorial de django 3.2. Vamos a configurar tu equipo como entorno de desarrollo para trabajar con la aplicación, para ello:

Realiza un fork del repositorio de GitHub: https://github.com/rubences/TutorialBasico
Crea un entorno virtual de python3 e instala las dependencias necesarias para que funcione el proyecto.
Comprueba que vamos a trabajar con una base de datos sqlite. ¿Qué fichero tienes que consultar?. ¿Cómo se llama la base de datos que vamos a crear?
Crea la base de datos. A partir del modelo de datos se crean las tablas de la base de datos.
Crea un usuario administrador.
Ejecuta el servidor web de desarrollo y entra en la zona de administración (\admin) para comprobar que los datos se han añadido correctamente.
Crea dos preguntas, con posibles respuestas.
Comprueba en el navegador que la aplicación está funcionando, accede a la url \polls.
Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea. Y pantallazos que demuestren que la aplicación está funcionando. (2 puntos)




TAREA 2: Entorno de producción

Vamos a realizar el despliegue de nuestra aplicación en un entorno de producción, para ello vamos a utilizar nuestro VPS, sigue los siguientes pasos:

Clona el repositorio en el VPS.
Crea un entorno virtual e instala las dependencias de tu aplicación.
Instala el módulo que permite que python trabaje con mysql:

  (env)$ pip install mysqlclient
Crea una base de datos y un usuario en mysql.
Configura la aplicación para trabajar con mysql, para ello modifica la configuración de la base de datos en el archivo settings.py:

  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': 'myproject',
          'USER': 'myprojectuser',
          'PASSWORD': 'password',
          'HOST': 'localhost',
          'PORT': '',
      }
  }
Como en la tarea 1, realiza la migración de la base de datos que creará la estructura de datos necesarias. Comprueba que se han creado la base de datos y las tablas.
Crea un usuario administrador.
Elige un servidor de aplicaciones python y configura nginx como proxy inverso para servir la aplicación.
Debes asegurarte que el contenido estático se está sirviendo: ¿Se muestra la imagen de fondo de la aplicación? ¿Se ve de forma adecuada la hoja de estilo de la zona de administración?.
Desactiva en la configuración el modo debug a False. Para que los errores de ejecución no den información sensible de la aplicación.
Muestra la página funcionando. En la zona de administración se debe ver de forma adecuada la hoja de estilo.
En este momento, muestra al profesor la aplicación funcionando. Entrega una documentación resumida donde expliques los pasos fundamentales para realizar esta tarea y pantallazos donde se vea que todo está funcionando. (4 puntos)




TAREA 3: Modificación de nuestra aplicación

Vamos a realizar cambios en el entorno de desarrollo y posteriormente vamos a subirlas a producción. Vamos a realizar tres modificaciones, pero recuerda que primero lo haces en el entrono de desarrollo, y luego tendrás que llevar los cambios a producción:

Modifica la página inicial donde se ven las encuestas para que aparezca tu nombre: Para ello modifica el archivo django_tutorial/polls/templates/polls/index.html.
Modifica la imagen de fondo que se ve la aplicación.
Vamos a crear una nueva tabla en la base de datos, para ello sigue los siguientes pasos:

Añade un nuevo modelo al fichero polls/models.py:

  class Categoria(models.Model):
  	Abr = models.CharField(max_length=4)
  	Nombre = models.CharField(max_length=50)

  	def __str__(self):
  		return self.Abr+" - "+self.Nombre
Crea una nueva migración.
Y realiza la migración.
Añade el nuevo modelo al sitio de administración de django:

Para ello cambia la siguiente línea en el fichero polls/admin.py:

  from .models import Choice, Question
Por esta otra:

  from .models import Choice, Question, Categoria
Y añade al final la siguiente línea:

  admin.site.register(Categoria)
Despliega el cambio producido al crear la nueva tabla en el entorno de producción.
Explica los cambios que has realizado en el entorno de desarrollo y cómo lo has desplegado en producción para cada una de las modificaciones (4 puntos). Entrega pantallazos donde se vea que todo está funcionando.




TAREA 4: Instalando un CMS en Django

En esta tarea vamos a desplegar un CMS python. Tienes que realizar la instalación de un CMS python basado en django (puedes encontrar varios en el siguiente enlace. Según la dificultad de la instalación tendrás más o menos notas:

Fácil (un 7): Django CMS, Wagtail CMS, CodeRed CMS
Medio (un 8,5): Mezzanine (Es fácil pero la instalación da un error que tendrás que solucionar).
Difícil (un 10): FeinCMS, Django-Fiber
Instala el CMS en el entorno de desarrollo. Debes utilizar un entorno virtual.
Personaliza la página (cambia el nombre al blog y pon tu nombre) y añade contenido (algún artículo).
Guarda los ficheros generados durante la instalación en un repositorio github. Guarda también en ese repositorio la copia de seguridad de la bese de datos. Ten en cuenta que en el entorno de desarrolla vas a tener una base de datos sqlite, y en el entorno de producción una mariadb, por lo tanto es recomendable para hacer la copia de seguridad y recuperarla los comandos: python manage.py dumpdata y python manage.py loaddata, para más información.
Realiza el despliegue de la aplicación en tu entorno de producción (servidor web y servidor de base de datos en KVM/openstack). Utiliza un entorno virtual. Utiliza el servidor de aplicaciones python que no hayas usado en la práctica anterior. El contenido estático debe servirlo el servidor web. La aplicación será accesible en la url python.tunombre.gonzalonazareno.org.


