# Proyecto
## Elementos necesarios para poder ejecutar el programa


Los elementos necesarios a instalar serán

- Editor de textos, como sublime text o Visual studio code
- XAMPP
- Composer
- Symfony
- Bootstrap

## Pasos a seguir para la instalación

- Primero deberemos instalar el editor de texto de preferencia, en mi caso, utilice Visual Studio Code, el cual lo podremos instalar desde el siguiente enlace https://code.visualstudio.com/download
- Posteriormente necesitaremos instalar el Paquete XAMMP, el cual nos dará acceso a la Base de Datos, lo descargamos desde el enlace https://www.apachefriends.org/es/download.html
- Para poder obtener Composer, lo descargamos desde el enlace https://getcomposer.org/download/ el cual nos dará acceso a la última versión
- Por último, para poder instalar Symfony, será necesario abrir el panel de comandos, y escribir las siguientes lines
> "symfony check:requirements" Permite saber si tu equipo tiene los elementos necesarios para poder usar Symfony
> "composer create-project symfony/skeleton:"6.1.*" my_project_directory" Creará una carpeta con los elementos necesarios para poder ejecutar Symfony

## Pasos a seguir para la elaboración del proyecto

Tras la creación de la carpeta, tenemos que abrir el panel de control de XAMPP, el cual nos permitirá activar la Base de Datos. Luego, modificamos el fichero ".env", para poder seleccionar el tipo de base de datos que estemos usando, el usuario y contraseña, para poder conectar el proyecto a la base de datos, de tal manera que quede así.

> DATABASE_URL="mysql://root:@127.0.0.1:3306/Images?serverVersion=10.4.19-MariaDBcharset=utf8mb4"

Una vez hecho esto, con el comando "symfony server:start", iniciamos el servidor en el que funcionará el proyecto, el cual será visible en el enlace "localhost:8000"

## Creación de los controladores

Para crear los controladores, debemos situarnos con el panel de comandos en la carpeta del proyecto y ejecutar el comando

> php bin/console make:controller NombreController

El framework symfony no incluye ningún componente para trabajar con bases de datos. Sin embargo proporciona integración con una librería llamada Doctrine

Para utilizar Doctrine hay que insatalarlo, junto con el bundle MakerBundle, que tiene las utilidades para generar código:

> composer require doctrine
> composer require maker --dev

Podemos crear la base de datos a mano, o utilizar la consola de symfony:

> bin/console doctrine:database:create

Podemos crear a mano las entidades, o utilizar la consola de symfony. Una entidad no es más que una clase decorada con decoradores de Doctrine.

> bin/console make:entity

Las entidades se guardan generalmente en el directorio src/Entity.

Tras crear los controladores y la base de datos, existe un comando para genear un CRUD completo a partir de una entidad de Doctrine:

> php bin/console make:crud Producto

## Modificación de la aplicación

Twig es un motor de plantillas para PHP.

Para activar el sistema de plantillas twig, si no lo tenemos instalado, hay que instalarlo.

> composer require twig

## Delimitadores

Su sintaxis incluye 3 delimitadores:

- Cometarios: {# ... #}

```twig
{# Esto es un comentario #}
```

- Para mostrar contenido (echo): {{ ... }}

```twig
<td>{{ fondo.editorial }}</td>
```

- Para ejecutar lógica: {% ... %}

```twig
{% for fondo in fondos %}
  ...
{% endfor %}
```

```twig
{% if autor.tipo == 'PERSONA' %}
  ...
{% endif %}
```
Las variables de tipo simple se acceden sin más.

Para acceder a atributos de objetos, elementos de arrays, etc, se utiliza el operador punto (.)

```
{{ fondo.titulo }}
```

Tras crear el crud, en la carpeta templates, se no habrá generado una carpeta con el  nombre de nuestra entidad, y podremos modificar la apariencia de la aplicación a placer, usando un fichero CSS, el cual generaremos dentro de la carpeta public/CSS.
