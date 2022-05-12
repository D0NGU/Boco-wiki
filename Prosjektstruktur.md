## [KLIENT](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend)
### Bibliotek & Rammeverk

[Vue.js](https://vuejs.org/) er et [JavaScript](https://www.javascript.com/) rammeverk for å lage grensesnitt. Det bygger på standard HTML, CSS og JavaScript og gir en komponent-basert modell for brukergrensesnitt. 

Videre benyttes biblioteket [Vuetify](https://vuetifyjs.com/en/). Dette biblioteket bygger videre på Vue.js med flere komponenter.

##### Bibliotek:

- **vue**: Rammeverk for å lage nettapplikasjoner
- **vuetify**: Vue bibliotek med flere komponenter
- **vue-router**: Vue sin offisielle router
- **vue-axios**: Bibliotek for HTTP kommunikasjon
- **vuex**: Håndterer nettsidens 'state'
- **vue-cookie**: Plugin for å håndtere cookies
- **vue-pwa**: Vue støtte for Progressive Web Apps (PWA)
- **jest**: Rammeverk for JavaScript testing


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

##### Bibliotek:

- **Maven**: Administereing og bygging av applikasjon
- **Spring Boot**: For å lage nettverksapplikasjoner med 'Spring framework'
- **Spring Security**: Rammeverk for autentisering og tilgangskontroll
- **JWT**: Java implementasjon av JSON Web Token (JWT)
- **Spring Data JDBC**: Funksjonalitet for å samhandle med databaser
- **H2 Database**: En innebygd Java SQL database
- **MySQL**: For å koble til eksterne MySQL databasesystem
- **Spring Mail**: For å kunne sende epost
- **JUnit**: Rammeverk for testing i Java.
- **JaCoCo**: For å generere test-rapporter med kodedekning

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