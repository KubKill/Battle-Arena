# Battle-Arena

## Table of content
1. [Short description](#Short-description)
2. [Technologies](#Technologies)
3. [Launch](#Launch)
4. [UML class diagram](#UML-class-diagram)
5. [Content](#Content)
   - [Game logic](#Game-logic)
   - [Tests](#Tests)
6. [Database](#Database)
   - [Mapping](#Mapping)
   - [Repository-HQL](#Repository-HQL)
   
## Short description
Battle Arena is simple turn-based auto battler game without GUI. It's been created with the purpose of learning code testing libraries, Docker and Hibernate.

## Technologies
* JAVA 17
* Maven, Docker
* JUnit 5.9, Mockito 4.7
* MySQL 8
* JPA, Hibernate 6.1

## Launch
To start the project follow steps:
1. Make sure you have the Docker intalled.
2. Open terminal, change current library to the project library and type "docker-compose up".
   - (Docker will set up the projects container and pull up images if needed.)
3. Run class:
   - "GameNoDB" to check how the game logic is working (There is example fight created.)
   - "QueriesOnDatabase" to check results of available queries working on the game database.
   
## UML class diagram
![Battle Arena class diagram](https://user-images.githubusercontent.com/66681683/189502101-5a61e8fb-27f0-42c2-9288-8b3b0bb9a544.png)

## Content

### Game logic

#### Avatar, Bag
Avatar is a creature designed to fight with other avatars. Avatar has properties like initiative points, max health points, current health points and name. 
Avatar can have a bag. One bag.

#### Item, Weapon
Items can be picked up only by avatars who have a bag. Weapon are Items. Each item has name and description. Weapons additionaly stores inforamtion about its maximal damage. If weapon is in bag, then it can be equiped and used to damage a oponnent.

#### Guild, Crest
Guilds can be created. Guilds have name and level properties. Guild can be joined by many different avatars and one avatar can join many guilds. Each guild has its own Crest. Crest stores inforamtion about its color and symbol it presents. Crest can't exist without its guild.

#### Battle, Message
Battle can be arrange between two different avatars. Fight can be started. Each fight is proceded in turns. Only one move by avatar is permitted on each round. Once the fight is initiated order of fight is set. Avatar with higher initiative points moves first every turn. Avatar attacks the oponnent with weapon during his turn. The damage done with weapon is a random numer starting from 0 and ending on weapons upper damage bound property. Fight last as many rounds as both avatars are alive. Once current health points of a avatar drops to zero or below the fight is over and his opponent is declared winner.

Course of the fight is described in the battle logs that are presented on the terminal with methods provided by the class Message.

![battle log](https://user-images.githubusercontent.com/66681683/189529025-9c606648-a455-413a-b73c-7a9d1d5359ac.png)

#### Range
Range is a class that stores inforamtion about the bottom and up line of the range. It's used in other classes to validate values of some properties.

### Tests
There are test written checking constructors and public methods of game logic classes. They are stored in the "test" folder in project folder in classes representing each logic class. Ex. "FightTest".

Test were created with help of JUnit5 and Mokito libraries.

### Database
MySQL set up with the docker-compose file is used in the project. ORM used in the project is Hibernate.

Initialization of connection and providing session is done with "InitDbConnection" class.
Class "SeedDb" seeds database with data.

#### Mapping
Technicques used in mapping classes to tables in database are:
1. OneToMany, OneToOne, ManyToMany, Embedded associations.
2. Lazy loading on the associations.
3. Inheritance - joined.
4. Cascades merge and persists. 

#### Repository HQL
"QueryTrainingRepository" class provides various methods accesing data and returning objects from the database.
