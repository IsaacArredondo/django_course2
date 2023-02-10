# django_course2

Este proyecto es la continuación de curso Django del canal de youtube uskokrum2010, donde partimos del video 17.

### Primero creamos el entorno virtual e instalamos los requerimentos

```
conda create -n Django
conda activate Django
conda install Django
conda install Python
```

### Creamos el proyecto y la aplicación

```
django-admin startproject Universidad
cd Universidad
mkdir Aplicaciones
cd Aplicaciones
django-admin startapp Academico
```

### Ahora creamos el modelo Curso

El modelo curso será como nuestra tabla en la aplicación Academico, cabe mencionar que es necesario dirigirnos al archivo "settings.py" y en la parte de INSTALLED_APPS debemos agregar la ruta de nuestra aplicación a la lista:

```
'Aplicaciones.Academico',
```

Tambien en la parte de DATABASES cambiamos el nombre de la base de datos al siguiente:

```
'Universidad.sqlite3'
```

Y verificamos que todo este correcto con el comando:

```
python manage.py check Academico
```

Cabe mencionar que tuve que cambiar el nombre de la App en la class AcademicoConfig del archivo "apps.py" de "Academico" a 'Aplicaciones.Academico" por un error de reconocimiento.

### Migración y Creación de la Base de Datos

Para poder hacer la migración de nuestro modelo a una base de datos usamos el comando:

```
python manage.py migrate #migramos las tablas por defecto de django
python manage.py makemigrations #con este comando creamos el archivo "0001_initial.py" de nuestro modelo
```

Ahora para ver la sentencia del modelo creado en formato SQL usamos el comando:

```
python manage.py sqlmigrate Academico 0001
```

Y para ejecutr el archivo "0001_initial.py" y verlo reflejado en la base de datos aplicamos nuevamente el comando:

```
python manage.py migrate
```

## Insertar valores en la tabla de nuestro modelo

Primero debemos ingresar al shell de python desde la terminal con el comando:

```
python manage.py shell
```

Ahora importamos el modelo Curso en la consola interactiva con el comando:

```
from Aplicaciones.Academico.models import Curso
```

Y creamos e insertamos tres cursos, lo que en SQL sería 'INSERT INTO', aquí sería:

```
cur1 = Curso(nombre = 'Programacion Avanzada', creditos = 4)
cur1.save()
cur2 = Curso(nombre = 'Teoria de Bases de Datos', creditos = 5)
cur2.save()
```

Y una opción en una sola linea puede ser solo con el comandoÑ

```
cur3 = Curso.objects.create(nombre = 'Redes y conectividad', creditos = 5)
```

## Actualizacion de datos

Para actualizar los datos de un registro podemos dirigirnos a sus atributos, por ejemplo:

```
cur4 = Curso.objects.create(nombre = 'Sistemas Operativos', creditos = 3)
cur4.creditos = 5
cur4.save()
```

En caso de salir de la consola interactiva y volver a entrar, para poder modificar un registro de la base de datos, podemos usar la siguiente sentencia para traerlo a la consola, por ejemplo:

```
cur = Curso.objects.get(id=2)
print(cur.nombre) # para verificar
```