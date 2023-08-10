# Proyecto con Spring Data JPA
1. Se creó el proyecto en spring initializr con:
   - Gradle - Groovy, Java 17, spring boot 3.1.2.
   - Dependencias: Lombok, Spring data JPA, Spring web y MySQL Driver.
   - Recordar tener seleccionado en la configuración global de IntelliJ como en la del propio proyecto java en su versión 17 (Ver en Settings, Build, Execution and Deployment, Build Tools, Gradle y en el Gradle JVM tener selecciona el JAVA_HOME con la versión 17 o superior) y en el lado de la aplicación (Clic derecho a la app, Project Settings, Project y en SDK tener la versión 17 o superior).
   - La base de datos es en MySQL
2. Crear la estructura de paquetes en "com.spring.pizza", se puede crear con el comando: `mkdir -p {web/controller,persistence/{entity,repository},service}`
3. Para la base de datos podemos usar Docker en lugar de instalar MySQL:
   - Creamos el volumen: `docker volume create mysql-volume`
   - Ejecutamos el contenedor de MySQL: `docker run -d -p 3306:3306 -v mysql-volume:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=admin --name mysql-container mysql:latest`
   - Se puede probar la conexión
4. En "application.properties"
   - Para colocar la BD en Postgres "spring.datasource.driver-class-name=org.postgresql.Driver" y "spring.datasource.url=jdbc:postgresql://localhost:<port>:<NombreDeBaseDeDatos>". También el archivo de build.gradle: "runtimeOnly 'org.postgresql:postgresql'"
   - El parámetro "spring.jpa.hibernate.ddl-auto=update": Permite crear las tablas a partir de los entities y no borra la información, sino que sondea que estamos haciendo y lo va replicando en la BD en términos de estructura como relaciones, tablas.
   - El parámetro "spring.jpa.show-sql=true": Ver en consola todo lo que hagamos en el proyecto como afecta la base de datos

