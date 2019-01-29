# Tecnología Spring: Proyecto TPV - Back-end
#### Back-end con Tecnologías de Código Abierto (SPRING)
#### [Máster en Ingeniería Web por la U.P.M.](http://miw.etsisi.upm.es)
[![Build Status](https://travis-ci.org/miw-upm/betca-tpv-spring.svg?branch=develop)](https://travis-ci.org/miw-upm/betca-tpv-spring)
![Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=es.upm.miw%3Abetca-tpv-spring&metric=alert_status)
> Proyecto Back-end completo para el uso de la tecnología Spring.  
> El Front-end se desarrolla en Angular en el proyecto [betca-tpv-angular](https://github.com/miw-upm/betca-tpv-angular).  
### Tecnologías necesarias
`Java` `Maven` `Spring` `Mongodb`
### Clonar el proyecto
 Clonar el repositorio en tu equipo, **mediante consola**:
```sh
> cd <folder path>
> git clone https://github.com/miw-upm/betca-tpv-spring
```
Importar el proyecto mediante **IntelliJ IDEA**
1. **Import Project**, y seleccionar la carpeta del proyecto
1. Marcar **Create Project from external model**, elegir **Maven**
1. **Next** … **Finish**
### Ecosistema
`Git` `GitHub` `Travis-CI` `Sonarclud` `Heroku` `mLab`
> Se utilizará un flujo de trabajo ramificado (_**Git Workflow**_). Una **historia** por alumno, organizada como un **proyecto** [https://github.com/miw-upm/betca-tpv-spring/projects]& [https://github.com/miw-upm/betca-tpv-angular/projects]. Cada **historia** se dividirá en **tareas**, cada **tarea** será una **issue#** que será el nombre de la **rama**.  
**Se recomienda aportaciones frecuentes a la rama `develop`** :sweat_smile:
#### Metodología de trabajo
 :one: Organización de la **historia** y **tareas** en el proyecto de GitHub mediante **notas**. Elegir la **nota** a implementar, convertina en **issue#**, configurarla y :muscle:
 :two: Mirar el estado del proyecto [![Build Status](https://travis-ci.org/miw-upm/betca-tpv-spring.svg?branch=develop)](https://travis-ci.org/miw-upm/betca-tpv-spring) en [Travis-CI](https://travis-ci.org/miw-upm/betca-tpv-spring/builds)
 :three: Sincronizar la rama **develop** con la remota **origin/develop**:
 ```sh
> git checkout develop
> git pull origin develop
 ```
:four: Si se comienza la tarea, se crea la rama y se activa
 ```sh
> git checkout -b issue#xx
 ```
 Si se continúa, y se necesita actualizar la rama:
  ```sh
> git checkout issue#xx
> git merge -m "Merge develop into issue #xx" develop
 ```
:five: Programar la tarea o una parte de ella, lanzar **TODOS LOS TESTS** y asegurarse que no hay errores.
:six: Actualizar **develop** con nuestro cambios, pero antes asegurarse que no ha evolucionado respecto del inicio de la tarea:
 ```sh
> git fetch --all
> git checkout develop
> git merge --no-ff -m "Merge issue #xx into develop" issue#xx
```
:seven: Resolver los conflictos, observar el flujo de ramas, y si todo ha ido bien... subirlo 
```sh
> git push --all
 ```
 #### Travis-CI
Integración continua con **Travis-CI**. Se despliega para pruebas con el servicio de BD de mongodb y ejecución de los test: Unitarios y de Integración
```yaml
language: java
jdk:
- oraclejdk8
branches:
  only:
  - develop
  - /^release-.*$/
  - master
notifications:
  email:
    recipients:
    - j.bernal@upm.es
services:
  - mongodb
script:
- mvn org.jacoco:jacoco-maven-plugin:prepare-agent verify  #Test unitario y de integracion en el perfil "dev" y con covertura
```
