# Taller de creación de los objetos de la Base de Datos SQL y/o NOSQL

Juan Camilo Alvrez Saavedra

Servicio NAcional de Aprendizaje- SENA

Tecnico de Programacion de Software (3069978)

Miguel Angel Lopz Cacho

20 de Noviembbre

### Introduccion

El presente documento tiene como objetivo principal el desarrollo de un modelo de datos relacional y no relacional para una solución de software orientada a la gestión de información relacionada con el Mundial de Fútbol de la FIFA. A partir de los datos proporcionados sobre equipos, confederaciones, jugadores, clubes y partidos, se construirá una estructura que permita representar esta información de manera eficiente, precisa y escalable.


### Objetivo Generale
Diseñar y construir un modelo de datos relacional y no relacional que permita administrar y gestionar de manera eficiente la información relacionada con el Mundial de Fútbol de la FIFA, garantizando la integridad, flexibilidad y escalabilidad de los datos.

#### Objetevis Especificos 
1.Analizar la información proporcionada sobre equipos, jugadores, confederaciones, clubes y partidos para identificar las estructuras de datos necesarias.

2.Diseñar el modelo físico de datos relacional mediante herramientas de modelado que aseguren la normalización y relaciones adecuadas entre las entidades.

3.Construir el modelo no relacional en formato JSON, adaptando la información a un esquema jerárquico que facilite consultas rápidas y específicas.

45.Generar scripts DDL y DML para la creación y manipulación de ambos modelos en los sistemas gestores de bases de datos seleccionados (MySQL y MongoDB).

5.Validar que los modelos diseñados permitan almacenar y gestionar los datos suministrados sin pérdida de información, proporcionando soporte a los requerimientos del caso práctico.




### Desarrollo

##### 1. Análisis de los datos suministrados

Los datos proporcionados corresponden a una tabla con información clave sobre los equipos participantes en el Mundial de Rusia 2018, incluyendo su país, abreviatura y confederación. Esta información inicial se utilizará para diseñar una base de datos que permita administrar no solo los equipos y sus confederaciones, sino también datos adicionales como jugadores, clubes y partidos, siguiendo las especificaciones del caso.

##### 2. Modelo Relacional

###### 2.1 Diseño del Modelo Relacional

El diseño del modelo relacional está representado en el siguiente diagrama (imagen proporcionada). Este modelo considera las siguientes entidades principales:

Confederaciones: Almacena las confederaciones a las que pertenecen los equipos.
Equipos: Contiene información básica de los equipos participantes.
Jugadores: Almacena los datos de los jugadores y su relación con equipos y clubes.
Clubes: Representa los clubes a los que pertenecen los jugadores.
Partidos: Define los encuentros entre equipos, especificando el equipo local, el equipo visitante y la fecha del partido.

######  2.2 Scripts para creación (DDL)

Creación de la tabla Confederaciones:

CREATE TABLE IF NOT EXISTS confederaciones (
    id INT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL
) ENGINE=INNODB;

Creación de la tabla Equipos:

CREATE TABLE IF NOT EXISTS equipos (
    id INT PRIMARY KEY,
    abrevacion VARCHAR(3) NOT NULL,
    nombre_pais VARCHAR(50) NOT NULL,
    confederacion_id INT,
    FOREIGN KEY (confederacion_id) REFERENCES confederaciones(id)
) ENGINE=INNODB;


Creación de la tabla Jugadores:

CREATE TABLE IF NOT EXISTS jugadores (
    id INT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    edad INT,
    equipo_id INT,
    club_id INT,
    FOREIGN KEY (equipo_id) REFERENCES equipos(id),
    FOREIGN KEY (club_id) REFERENCES clubes(id)
) ENGINE=INNODB;

Creación de la tabla Clubes:

CREATE TABLE IF NOT EXISTS clubes (
    id INT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    pais VARCHAR(50) NOT NULL
) ENGINE=INNODB

Creación de la tabla Partidos:

CREATE TABLE IF NOT EXISTS partidos (
    id INT PRIMARY KEY, 
    equipo_local_id INT,
    equipo_visitante_id INT,
    fecha DATE,
    FOREIGN KEY (equipo_local_id) REFERENCES equipos(id),
    FOREIGN KEY (equipo_visitante_id) REFERENCES equipos(id)
) ENGINE=INNODB;

###### 2.3 Scripts de inserción (DML)

Datos de prueba para Confederaciones:

INSERT INTO Confederaciones (id, nombre) VALUES 
(1, 'CONMEBOL'),
(2, 'UEFA'),
(3, 'CONCACAF'),
(4, 'CAF'),
(5, 'AFC');


Datos de prueba para Equipos:

INSERT INTO Equipos (id, abreviacion, nombre_pais, confederacion_id) VALUES
(1, 'ARG', 'Argentina', 1),
(2, 'AUS', 'Australia', 2),
(3, 'BEL', 'Belgium', 2),
(4, 'BRA', 'Brazil', 1),

Datos de prueba para Clubes:

INSERT INTO clubes (id, nombre, pais) VALUES 
(1, 'Barcelona', 'Spain'),
(2, 'Bayern Munich', 'Germany'),
(3, 'PSG', 'France'),
(4, 'Chelsea', 'England'),

Datos de prueba para Jugadores:

INSERT INTO Jugadores (id, nombre, edad, equipo_id, club_id) VALUES
(1, 'Lionel Messi', 31, 1, 1),
 (2, 'Sergio Aguero' , 30, 1, 9),
 (3, 'Angel Di Maria' , 30, 1, 3),
(4, 'Manuel Neuer' ,32, 12, 2),

###### 2.4 Validación del Modelo Relacional

El modelo relacional permite representar toda la información inicial sin pérdida de datos. Las relaciones entre equipos y confederaciones, así como entre jugadores y clubes, están correctamente definidas mediante claves foráneas, garantizando la integridad referencial.

##### Base sw datos SQL

##### Diagrama Entidad Relacion

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168740/Workflow_Diagram_yvivff.png)

### Modelo Racional

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168773/diagrama_btfq0u.png)

###### Evidencias



![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168780/trabajo_1_x6d4u3.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168778/trabajo_2_hwagwv.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168777/trabajo_3_llpqje.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168777/trabajo_4_hq5v23.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168777/trabajo_5_xvbptb.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168777/trabajo_6_fdujub.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168777/trabajo_7_svsy4g.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168773/trabajo_8_hautaw.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168773/trabajo_9_hycvw0.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168772/trabajo_10_hkwget.png)

![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168772/trabajo_11_jdza4s.png)


##### 3. Modelo No Relacional

###### 3.1 Diseño del Modelo No Relacional

El modelo no relacional se diseñó en formato JSON, considerando las necesidades del caso. A continuación, se muestra un ejemplo de estructura de documento:

Coleccion "Equipos"

db.Equipos.insertOne({
  _id: "ARG",
  nombre: "Argentina",
  confederacion: "CONMEBOL",
  jugadores: [
    { nombre: "Lionel Messi", edad: 31, club: "Barcelona" },
    { nombre: "Ángel Di María", edad: 30, club: "PSG" },
    { nombre: "Sergio Aguero", edad: 30, club: "City" }
  ]
});


Colección "Confederaciones"

{
  "_id": "CONMEBOL",
  "nombre": "Confederación Sudamericana de Fútbol",
  "region": "Sudamérica"
}


Colección "Partidos"    

{
  "_id": 1,
  "equipo_local": "ARG",
  "equipo_visitante": "BRA",
  "fecha": "2018-06-15",
  "resultado": {
    "goles_local": 1,
    "goles_visitante": 0
  }
}


Colección "Clubes"

{
  "_id": "Barcelona",
  "pais": "España",
  "jugadores": ["Lionel Messi", "Gerard Piqué"]
}


###### 3.2 Validación del Modelo No Relacional

El modelo no relacional permite almacenar información estructurada y no estructurada de manera flexible, integrando datos sobre equipos, jugadores y partidos en un único documento, lo que facilita consultas rápidas y escalabilidad.


###### Evidencias 

 ![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168772/Trabajo_12_wknler.png)
 
  ![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732168772/trabajo_13_dhngtn.png)
  
   ![Texto Alternativo](https://res.cloudinary.com/dlqkmo1h3/image/upload/v1732173882/trabajo_14_geanpt.png)


### Conclusiones

Ambos modelos, relacional y no relacional, cumplen con los requerimientos planteados para administrar la información del Mundial de Fútbol, garantizando la representación completa de los datos sin pérdida de información.


El modelo relacional asegura la integridad de los datos y su consistencia mediante el uso de claves foráneas y relaciones normalizadas, mientras que el modelo no relacional ofrece mayor flexibilidad y rapidez en consultas específicas, adaptándose a necesidades jerárquicas y escalabilidad.


El uso de MySQL para el modelo relacional y MongoDB para el no relacional demostró que la elección del sistema gestor depende de los objetivos del sistema, destacando las fortalezas de cada enfoque en la gestión y almacenamiento de datos.



### Referencias

Manual de MySQL:
Oracle Corporation. (2024). MySQL Documentation. Recuperado de https://dev.mysql.com/doc/

Manual de MongoDB:
MongoDB Inc. (2024). MongoDB Documentation. Recuperado de https://www.mongodb.com/docs/

Fundamentos de Bases de Datos:
Silberschatz, A., Korth, H. F., & Sudarshan, S. (2020). Database System Concepts (7ª ed.). McGraw-Hill.

Curso Oficial de MongoDB:
MongoDB Inc. (2024). MongoDB University Courses. Recuperado de https://university.mongodb.com/

Diseño de Modelos Relacionales:
Date, C. J. (2020). An Introduction to Database Systems (8ª ed.). Pearson Education
