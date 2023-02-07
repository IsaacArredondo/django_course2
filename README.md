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
python manage.py migrate
```