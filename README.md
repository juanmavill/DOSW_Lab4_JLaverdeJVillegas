## Resolución de Preguntas
## a. ¿Qué es un arquetipo (Archetype) en Maven?

Un arquetipo en Maven es básicamente una plantilla o modelo que permite crear la estructura inicial de un proyecto de manera automática. Sirve para no tener que empezar desde cero cada vez que se crea un proyecto nuevo, ya que genera carpetas, archivos y configuraciones básicas necesarias para comenzar a trabajar.

## b. ¿Para qué sirve el arquetipo maven-archetype-quickstart?

El arquetipo maven-archetype-quickstart sirve para crear un proyecto Java básico con una estructura estándar. Este incluye carpetas como src/main/java y src/test/java, además de un archivo pom.xml configurado inicialmente. Es útil cuando se quiere empezar rápido con un proyecto sencillo sin configuraciones complejas.

## c. ¿Cuál es el comando con el cual se puede crear un proyecto basado en un arquetipo Maven?

El comando general para crear un proyecto basado en un arquetipo es mvn archetype:generate. A partir de ese comando Maven solicita algunos datos como el groupId, artifactId y el arquetipo que se desea utilizar, y luego genera el proyecto automáticamente.

## d. ¿Qué es un pull request en GitHub?

Un pull request en GitHub es una solicitud que se hace para proponer cambios en un repositorio. Generalmente se utiliza cuando se trabaja con ramas, y se quiere que los cambios realizados en una rama sean revisados antes de integrarlos a la rama principal como main. Permite discutir, revisar y mejorar el código antes de fusionarlo.

## e. ¿Cómo se crea un pull request en GitHub?

Para crear un pull request primero se deben subir los cambios a una rama diferente a la principal. Luego, en la página del repositorio en GitHub, se selecciona la opción “Compare & pull request”. Allí se escribe un título, una descripción de los cambios realizados y finalmente se envía la solicitud para revisión.

## f. ¿Cómo se aprueba un pull request en GitHub?

Un pull request se aprueba cuando un colaborador con permisos de revisión entra al pull request, revisa los cambios y selecciona la opción de aprobar. Después de la aprobación, si no hay conflictos, se puede hacer el merge para integrar los cambios a la rama principal.

## g. Bibliografía (Norma APA)

Apache Maven. (2023). Introduction to the Standard Directory Layout. Recuperado de [https://maven.apache.org](https://maven.apache.org)

Apache Maven. (2023). Introduction to Archetypes. Recuperado de [https://maven.apache.org](https://maven.apache.org)

GitHub. (2023). About pull requests. Recuperado de [https://docs.github.com](https://docs.github.com)

GitHub. (2023). Creating a pull request. Recuperado de [https://docs.github.com](https://docs.github.com)

### 4. Comando utilizado para generar el proyecto:
mvn archetype:generate -DgroupId=edu.dosw.lab -DartifactId=DOSW-Laboratorio4 -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
