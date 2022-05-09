## [KLIENT](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend)
### Bibliotek & Rammeverk

[Vue.js](https://vuejs.org/) er et [JavaScript](https://www.javascript.com/) rammeverk for å lage grensesnitt. Det bygger på standard HTML, CSS og JavaScript og gir en komponent-basert modell for brukergrensesnitt. 

Videre benyttes biblioteket [Vuetify](https://vuetifyjs.com/en/). Dette biblioteket bygger videre på Vue.js med flere komponenter.

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



## [SERVER](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend)

### Bibliotek & Rammeverk

Serverapplikasjonen er bygd med Java og benytter seg av [Apache Maven](https://maven.apache.org/) for å administrere prosjektet. Maven standardiserer byggingen, laster ned avhengigheter og automatiserer flere deler av prosjektet.

Det populære rammeverket [Spring](https://spring.io/), da spesifikt _Spring Boot_, blir også brukt. Dette rammeverket sørger blant annet for database-transaksjoner og administrasjon av [REST](https://restfulapi.net/)-tjenester og endepunkter.

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