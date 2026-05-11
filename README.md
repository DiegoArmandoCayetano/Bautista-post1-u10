Productos Service — Análisis SonarQube

Proyecto académico de la asignatura Patrones de Diseño de Software (Unidad 10), donde se realiza análisis de calidad de código utilizando SonarQube y JaCoCo sobre una aplicación Spring Boot con errores intencionales.

Objetivo del proyecto

Configurar un proyecto Spring Boot con código intencionalmente imperfecto, ejecutar análisis estático con SonarQube, integrar JaCoCo para cobertura de pruebas y documentar los hallazgos encontrados en el dashboard.

Tecnologías utilizadas
Java 21
Spring Boot
Maven
SonarQube (Docker)
JaCoCo
H2 Database
Lombok
Ejecución del proyecto
1. Levantar SonarQube con Docker

docker run -d
--name sonarqube
-p 9000:9000
-e SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
sonarqube:community

Acceder en el navegador a:
http://localhost:9000

Credenciales:
usuario: admin
contraseña: admin

2. Ejecutar el proyecto Spring Boot

mvn clean install
mvn spring-boot:run

3. Ejecutar análisis en SonarQube

mvn clean verify sonar:sonar -Dsonar.token=TU_TOKEN

Estado inicial del análisis

Categoría: Bugs — Cantidad: X — Rating: ?
Categoría: Vulnerabilidades — Cantidad: X — Rating: ?
Categoría: Code Smells — Cantidad: X — Rating: ?
Cobertura: X%

Hallazgos principales
Bug 1: Retorno de null en búsqueda

Archivo: ProductoService.java
Método: buscar(Long id)
Descripción: El método retorna null si el producto no existe, lo que puede causar NullPointerException en otras capas.
Severidad: Major

Code Smell 1: Método con demasiadas responsabilidades

Archivo: ProductoService.java
Método: procesarProducto(...)
Descripción: El método realiza validaciones, creación de objeto y lógica de negocio en un solo bloque, aumentando la complejidad.
Severidad: Major

Code Smell 2: Inyección sin constructor

Archivo: ProductoService.java
Descripción: Uso de @Autowired en atributo en lugar de inyección por constructor.
Severidad: Minor

Capturas del dashboard

Dashboard general SonarQube: docs/sonar-dashboard.png
Detalle de bugs: docs/sonar-bugs.png

Estructura del proyecto

src/
└── main/
└── java/
└── com.universidad.productosservice/
├── domain/
├── service/
└── repository/

docs/
├── sonar-dashboard.png
└── sonar-bugs.png

Autor:
Diego Armando Cayetano
