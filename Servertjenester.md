### Ressursene som applikasjonen vår kan tilby:
Tjeneren tilbyr en rekke resurser som leveres i form av JSON objekter, som kan nås gjennom forskjellige endepunkter.
| Metode | Endepunkt | Variabler | Response | Sammendrag |
| ------ | ------ |------ |------ |------ |
| POST | /api/login| JSON: [Login request](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/LoginRequest.java) | autentiserings token | Sjekker om brukeren ligger i databaseb. <br> Hvis burker finnes og passordet er riktig <br> returneres en autentiseringsnøkkel
| GET | /api/users | | Liste med brukere | Finner alle registrerte brukere|
| POST | /api/user/save | JSON: [User](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) | Brukeren som ble laget | Legger til en ny bruker i databasen |
| DELETE | /api/user/delete | Request parametere: <br> userId og password | Streng med konfirmasjon <br> om at bruker ble slettet | Sletter en gitt bruker fra databasen. Sjekker at<br> passordet er riktig for å forhindre at en bruker<br> sletter en bruker den ikke eier. |
| POST | /api/user/edit | JSON: [editUserRequest] (https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/EditUserRequest.java) | Endret [bruker](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java)| Endrer en bruker å returnerer den nye versjonen |



Liste over alle ressursene her.

Ta med endepunkter her