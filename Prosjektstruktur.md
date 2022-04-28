## [FRONTEND](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend)
### Bibliotek

### Rammeverk

### Filstruktur

_!! Skjermbilde av filstrukturen til frontend her_

## [BACKEND](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend)

### Bibliotek
Serverapplikasjonen er bygd i Java 11 og benytter seg av [Apache Maven](https://maven.apache.org/).

### Rammeverk
På serversiden benyttes det populære rammeverket [Spring](https://spring.io/), da spesifikt Spring Boot. 

### Filstruktur
Filstrukturen følger [Maven Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html).

_TEMP - FIKS NÅR GOOD_

```
backend
   ├───assets
   └───src
       ├───main
       │   ├───java
       │   │   └───ntnu
       │   │       └───idatt
       │   │           └───boco
       │   │               ├───controller
       │   │               ├───exceptions
       │   │               ├───filter
       │   │               ├───model
       │   │               ├───repository
       │   │               ├───security
       │   │               ├───service
       │   │               └───usrRepo
       │   └───resources
       └───test
           ├───java
           │   └───ntnu
           │       └───idatt
           │           └───boco
           │               ├───controller
           │               ├───repository
           │               ├───security
           │               └───service
           └───resources
```
