# Battle-Arena

## Table of content
1. [Short description](#Short-description)
1. [Technologies](#Technologies)
2. [Launch](#Launch)
3. [UML class diagram](#UML-class-diagram)
4. [Content](#Content)
   - [Game logic](#Game-logic)
   - [Repository](#Repository)
   
## Short description
Battle Arena is simple turn-based auto battler game without GUI. It's been created with the purpose of learning code testing libraries, Docker and Hibernate.

## Technologies
* JAVA 17
* Maven, Docker
* JUnit 5.9, Mockito 4.7
* MySQL 8
* Hibernate 6.1

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

### Repository
