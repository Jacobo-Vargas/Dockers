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
