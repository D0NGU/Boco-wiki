## [FRONTEND](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend)
### Bibliotek

### Rammeverk

### Filstruktur

```
frontend
   ├───assets
   ├───public
   │   └───img
   └───src
       ├───assets
       │   └───images
       ├───components
       │   ├───Listing
       │   │   └───Rental
       │   ├───LogIn
       │   ├───Misc
       │   ├───Notification
       │   └───UserProfile
       ├───plugins
       ├───router
       ├───service
       ├───store
       └───views
```

## [BACKEND](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend)

### Bibliotek
Serverapplikasjonen er bygd med Java og benytter seg av [Apache Maven](https://maven.apache.org/).

### Rammeverk
På serversiden benyttes det populære rammeverket [Spring](https://spring.io/), da spesifikt Spring Boot. 

### Filstruktur
Filstrukturen følger [Maven Standard Directory Layout](https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html).

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
       │   │               ├───model
       │   │               ├───repository
       │   │               ├───security
       │   │               │   └───filter
       │   │               └───service
       │   └───resources
       └───test
           ├───java
           │   └───ntnu
           │       └───idatt
           │           └───boco
           │               ├───controller
           │               ├───repository
           │               └───service
           └───resources
```
