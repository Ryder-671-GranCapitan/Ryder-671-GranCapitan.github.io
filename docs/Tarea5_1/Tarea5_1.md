# Práctica 5.1
## Configuración de un servidor DN
#### Javier Rider Jimenez

### Repositorio DEAW
1. Crear un repositorio en GitHub .
2. Clonar repositorio en local.

![crear](./Imagenes/screenshot.0.jpg)

![clonar](./Imagenes/screenshot.2.jpg)

### README
1. Crear README.md.

![crear](./Imagenes/screenshot.3.jpg)

### Commit inicial
1. Realizar un commit inicial.

![commit](./Imagenes/screenshot.4.jpg)


### Push inicial
1. Subir los cambios al repositorio remoto.

![push](./Imagenes/screenshot.5.jpg)

### Ignorar archivos
1. Crear fichero `privado.txt`.
2. Crear carpeta `privada`.
3. Añadir `.gitignore` para ignorar los ficheros creados.
![ignorar](./Imagenes/screenshot.01.jpg)
![ignorar](./Imagenes/screenshot.02.jpg)
![ignorar](./Imagenes/screenshot.03.jpg)

### Añadir fichero 1.txt
1. Añadir fichero `1.txt` al repositorio local.

```bash
echo "Hola" > 1.txt
git add 1.txt
git commit -m "Añadido fichero 1.txt"
git push
```

![1.txt](./Imagenes/screenshot.8.jpg)

### Crear el tag v0.1
1. Crear un tag `v0.1`.
2. Subir los cambios al repositorio remoto.

![añadir](./Imagenes/screenshot.6.jpg)

![tag](./Imagenes/screenshot.7.jpg)

### Uso social de GitHub
1. Preguntar los nombres de usuario de GitHub de 2 de tus compañeros de clase, búscalos, y sígueles.
2. Seguir los repositorios DEAW del resto de tus compañeros.
3. Añadir una estrella a los repositorios DEAW del resto de tus compañeros.

no he considerado en hacer este apartado 

### Crear una tabla
Crear una tabla de este estilo en el fichero README.md con la información de varios de tus compañeros de clase:

![1.txt](./Imagenes/screenshot.8.jpg)

## Colaboradores
Poner a [github.com/raul-profesor](https://github.com/raul-profesor) como colaborador del repositorio DEAW.

## Notas
Este ejercicio es continuación del anterior por lo que tendréis que seguir trabajando en el repositorio DEAW.

También tendréis que ir poniendo los comandos que habéis tenido que utilizar durante todos los ejercicios y las explicaciones y capturas de pantalla que consideréis necesarias en el informe.

![social](./Imagenes/screenshot.9.jpg)

![social](./Imagenes/screenshot.10.jpg)

## Crear una rama v0.2
1. Crear una rama `v0.2`.
2. Posiciona tu carpeta de trabajo en esta rama.

```bash
git branch v0.2
git checkout v0.2
```

## Añadir fichero 2.txt
1. Añadir un fichero `2.txt` en la rama `v0.2`.

![rama](./Imagenes/screenshot.11.jpg)

## Crear rama remota v0.2
1. Subir los cambios al repositorio remoto.

![rama](./Imagenes/screenshot.12.jpg)

## Merge directo
1. Posicionarse en la rama `main`.
2. Hacer un merge de la rama `v0.2` en la rama `main`.

![merge](./Imagenes/screenshot.13.jpg)

## Merge con conflicto
1. En la rama `main` poner `Hola` en el fichero `1.txt` y hacer commit.
2. Posicionarse en la rama `v0.2` y poner `Adios` en el fichero `1.txt` y hacer commit.
3. Posicionarse de nuevo en la rama `main` y hacer un merge con la rama `v0.2`.
4. Arreglar el conflicto anterior y hacer un commit.

![merge con conflicto](./Imagenes/screenshot.14.jpg)

![merge con conflicto](./Imagenes/screenshot.15.jpg)

![merge con conflicto](./Imagenes/screenshot.16.jpg)

![merge con conflicto](./Imagenes/screenshot.17.jpg)

![merge con conflicto](./Imagenes/screenshot.18.jpg)

![merge con conflicto](./Imagenes/screenshot.19.jpg)

![merge con conflicto](./Imagenes/screenshot.20.jpg)

## Listado de ramas
1. Listar las ramas con merge y las ramas sin merge.
![listado](./Imagenes/screenshot.21.jpg)

## Arreglar conflicto

## Borrar rama
1. Crear un tag `v0.2`.
2. Borrar la rama `v0.2`.
![listado](./Imagenes/screenshot.22.jpg)
![listado](./Imagenes/screenshot.23.jpg)
![listado](./Imagenes/screenshot.24.jpg)
![listado](./Imagenes/screenshot.25.jpg)

## Listado de cambios
1. Listar los distintos commits con sus ramas y sus tags.

![listado](./Imagenes/screenshot.26.jpg)
