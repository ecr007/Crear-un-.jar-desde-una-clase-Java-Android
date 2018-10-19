# Crear un .jar desde una clase Java Android

## 1 Descarga del proyecto.

Como hemos dicho en la introducción, Google aún no distribuye la librería a través del sdk de Android, por lo que lo tendremos que descargar por nuestra cuenta. Para ello, vamos a usar git para clonar el repositorio de Volley y tener una copia del código fuente en nuestro equipo.

Ej: Desde un terminal con git instalado hacemos: git clone https://android.googlesource.com/platform/frameworks/volley

<img src="https://rawcdn.githack.com/ecr007/Crear-un-.jar-desde-una-clase-Java-Android/master/imagen-1.jpeg?raw=true" />

Cuando termine tendremos en la carpeta que hayamos hecho el clone una nueva carpeta con el nombre volley y con el código fuente necesario para que podamos contruir la librería.

## 2 Con Apache Ant.

Lo que vamos a hacer con Ant es generar un jar que luego podremos añadir como dependencia en el proyecto Android en el que necesitemos usarlo.

Vamos a ver el contenido de proyecto:

<img src="https://rawcdn.githack.com/ecr007/Crear-un-.jar-desde-una-clase-Java-Android/master/imagen-2.jpeg?raw=true" />

Ejecutamos android update project -p . (el punto al final también hay que añadirlo) para modificar el proyecto con los datos locales: por ejemplo donde se encuentra nuestra instalación del sdk.

<img src="https://rawcdn.githack.com/ecr007/Crear-un-.jar-desde-una-clase-Java-Android/master/imagen-3.jpeg?raw=true" />

Y una vez que tenemos el proyecto listo, lo compilamos con Ant para generar un jar. Ejecutamos ant jar.

<img src="https://rawcdn.githack.com/ecr007/Crear-un-.jar-desde-una-clase-Java-Android/master/imagen-4.jpeg?raw=true" />

<img src="https://rawcdn.githack.com/ecr007/Crear-un-.jar-desde-una-clase-Java-Android/master/imagen-5.jpeg?raw=true" />

Si todo ha ido bien y tenemos un bonito BUILD SUCCESFUL entonces tendremos un jar llamado volley.jar en el directorio bin que podremos usar para importar en Android Studio.


## 2.1 Importando el proyecto.

Para usar la librería creamos una carpeta lib y copiamos el jar que acabamos de generar en esa carpeta.

Las últimas versiones de Android Studio vienen ya configuradas para que use esa carpeta como dependencias (como ocurría con Eclipse). Si no es nuestro caso, añadimos la dependencia nosotros a mano o a través del asistente de Android Studio. Nos tiene que quedar el fichero build.gralde así:

```shell
dependencies {  
    compile 'com.android.support:appcompat-v7:+'  
  
    compile files('libs/volley.jar')  
}
```

Fuente: https://www.adictosaltrabajo.com/2014/03/11/android-volley/#03.2.2
