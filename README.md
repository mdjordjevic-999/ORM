# DEZSYS_GK862_WAREHOUSE_ORM

## Marko Djordjevic 4CHIT

### Docker Container erstellen

```
docker pull mysql
```
Mysql pullen

```
docker run --name MySQL -e MYSQL_ROOT_PASSWORD=root -p 3306:3306-d mysql
```
Container bereitstellen

```
mysql> create database db_example;
mysql> create user 'springuser'@'%' identified by 'ThePassword';
mysql> grant all on db_example.* to 'springuser'@'%';
```
Datenbank bereitstellen

### Bereitstellung der applocation.properties Datei
```
spring.application.name=accessing-data-mysql
spring.jpa.hibernate.ddl-auto=create
spring.datasource.url=jdbc:mysql://localhost:3306/db_example
spring.datasource.username=springuser
spring.datasource.password=ThePassword
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```
Den Abschnitt einfach in das File hinzufügen

### Demo Code
Auf folgender Webseite kann man den Demo Code abrufen inklusive Anleitung wie man alles einstellt:
https://spring.io/guides/gs/accessing-data-mysql

![image](https://github.com/mdjordjevic-999/ORM/assets/105716799/d2731708-ba25-4553-b04a-6058ff9da5c0)
Controller Klasse

### Output
Mit folgendem Befehl kann man jetzt Daten hinzufügen
```
Invoke-WebRequest -Uri http://localhost:8080/demo/add -Method Post -Body @{name="Test"; email="test@student.tgm.ac.at"}
```

Diese sind auf "http://localhost:8080/demo/all" aufrufbar.


### Questions

- What is ORM and how is JPA used?
- ORM (Object-Relational Mapping) is a technique for converting data between incompatible systems using object-oriented programming. JPA (Java Persistence API) is a specification for ORM in Java, providing a framework for managing relational data in applications.
- What is the application.properties used for and where must it be stored?
- `application.properties` is used to configure application settings in a Spring Boot application and must be stored in the `src/main/resources` directory.
- Which annotations are frequently used for entity types? Which key points must be observed?
- Frequently used annotations for entity types include `@Entity`, `@Table`, `@Id`, and `@GeneratedValue`. Key points to observe are defining the primary key with `@Id` and mapping the entity to a database table with `@Table`.
- What methods do you need for CRUD operations?
- Methods needed for CRUD operations are `save()` for create, `findById()` or `findAll()` for read, `save()` for update, and `deleteById()` for delete.
