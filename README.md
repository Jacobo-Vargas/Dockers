# Proyecto Final: Infraestructura Computacional

## Descripción General

Este proyecto tiene como objetivo la consolidación de la infraestructura de una organización mediante la implementación de **virtualización** en un servidor tipo torre de gran capacidad. La organización actualmente posee tres servidores tipo torre con servicios variados, que se replicarán en contenedores en el nuevo servidor para mejorar la eficiencia y centralizar la administración.

## Objetivos del Proyecto

- **Consolidar** los servicios en un solo servidor mediante virtualización.
- Implementar contenedores con servicios **Apache**, **MySQL** y **Nginx**.
- Utilizar **Docker** y **Podman** para crear y gestionar contenedores.
- Configurar **RAID** y **LVM** para la gestión de volúmenes persistentes.
- Documentar la configuración, pruebas y funcionamiento en una **bitácora** y alojar el repositorio en **GIT**.

## Requerimientos

- **Servidor tipo torre** de capacidad avanzada.
- **Docker y Podman** instalados para la creación de contenedores.
- Tres servicios básicos a implementar en contenedores:
  - **Apache**: Servidor web
  - **MySQL**: Base de datos
  - **Nginx**: Servidor proxy inverso
- Configuración de **RAID lv1** y **LVM** para la gestión de volúmenes persistentes en los contenedores.


## Creación de RAIDs

- **Comando para creación de RAIDs:** 
  - sudo mdadm --create --verbose /dev/**nombre** --level=**nivelRaid** --raid-devices=**numeroDiscos** /dev/**disco**
- En la siguiente imagen se puede observar la creación de los RAIDs 

## Autores
- Esta guia fue desarrollada por los estudiantes:
    - Jacobo Vargas García
    - Juan Jose Contretas
 
![imagen](https://github.com/user-attachments/assets/5cdac65c-3aeb-4c4e-8e72-99a931fb1511)

## Creación de grupo y volumenes lógicos
- **Comando para crear volúmenes fisícos:**
  - sudo pvcreate **nombre** /dev/**RAID** 

![imagen](https://github.com/user-attachments/assets/0840e9b8-a884-463c-87ab-52057f89d425)

- **Comando para crear grupo de volúmenes:**
  - sudo vgcreate **nombre** /dev/**RAID**

![imagen](https://github.com/user-attachments/assets/1477d476-e039-4b66-920c-86cf3f17ed36)

- **Comando para crear volúmenes lógicos:**
  - sudo lvcreate -l **capacidad** -n **nombreVolumen** **nombreGrupo**

![imagen](https://github.com/user-attachments/assets/bdf7e2d1-485f-4a08-8e43-c6eb767f9a8d)

- **Comando para dar formato a los voúmenes creados:**
  - sudo mkfs.**formato** /dev/**grupo**/**volumen**
 
![imagen](https://github.com/user-attachments/assets/2369c380-2001-4150-97df-707488d147f8)

## Creación y montaje de los volúmenes creados
- **Comando para crear directorios:**
  - mkdir /mnt/**directorio**
- **Comando para montar volúmenes:**
  - mount /**rutaDeVolumen** /**puntoDeMontaje**

![imagen](https://github.com/user-attachments/assets/e307aca9-37ed-4af2-9a88-c642802e7223)

## Creación de los DockerFile para mysql, nginx y apache
  - **DockerFile mysql**
  ![imagen](https://github.com/user-attachments/assets/41a9c327-3c67-41f8-861d-d4361538cb04)

  - **DockerFile nginx**
  ![imagen](https://github.com/user-attachments/assets/f83c8221-8cb3-4d61-847f-dd95358aff83)
  
  - **DockerFile apache**
  ![imagen](https://github.com/user-attachments/assets/24f26d52-683d-4f63-b0e6-c2a350edc1bd)

## Construcción de imagénes
- **Comando para crear imágenes:**
  - docker build -t **nombreImagen** -f **imagenCreada** .

  **Construcción de image-apache**
  ![imagen](https://github.com/user-attachments/assets/46e63f93-0f39-4deb-aa60-a0bfb19afd8d)

  **Construcción de image-nginx**
  ![imagen](https://github.com/user-attachments/assets/7df19e4f-5222-453d-9097-739cec225a2a)

  **Construcción de image-mysql**
  ![imagen](https://github.com/user-attachments/assets/39d6eae2-2ab3-4630-a098-c9061eb55f59)

## Ejecución de las imagenes creadas
- **Comando para ejecutar una imagen usando un volumen para mapear los archivos que usa el contenedor**
  - docker run -d --name **nombre_contenedor** -v /**volumen**:**directorio_logico** -p **puerto de uso**:**puerto_expuesto_en_el_DockerFile** **nombre_imagen**
  ![imagen](https://github.com/user-attachments/assets/6fc7f060-ebd1-412a-a2ab-9bbeb9bb6437)

- **Prueba de los contenedores ejecutados**
  - Esta es la prueba de los contenedores ejecutados usando la información alojada en el volumen lógico que se creó 
  ![imagen](https://github.com/user-attachments/assets/c8f1467f-ff4f-4061-9d8b-099c01e81a3f)
  
  - Archivos que se modificaron con la pagina de prueba
  ![imagen](https://github.com/user-attachments/assets/cb52ec95-c173-4fc1-92c5-8ee2463a8fff)

-**Prueba de el contenedor de mysql**
  - Se puede evidenciar en la imágen que el se hizo una conexion a mysql y se ejecuto un comando para ver las bases de datos que existen se observa **infradb** la cual fue creada desde el DockerFile y de este mismo modo se usó la contraseña definida para la base de datos la cual fue **rootpassword** 
  ![imagen](https://github.com/user-attachments/assets/26e3e419-db8e-430f-a317-b89aceea2dc4)


## Creación de imágenes a partir de los DockerFile existentes con Podman
- **Comando para crear las imágenes:**
  - podman build -t **nombre** -f **archivo_DockerFile**
  .**apache**
  ![imagen](https://github.com/user-attachments/assets/c0b87a50-4ca6-41c1-b9f4-10df7880a461)

  -**nginx**
  ![imagen](https://github.com/user-attachments/assets/a369fb68-d674-4d3e-97ed-5338c60f17c2)

  -**mysql**
  ![imagen](https://github.com/user-attachments/assets/59b1bb36-9ee2-4955-842e-4b80c478b1c3)

- **Images creadas tanto en podman como en docker**
  ![imagen](https://github.com/user-attachments/assets/751568bf-815e-4dde-83f1-475ffcfeaa10)















