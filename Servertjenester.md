### Ressursene som applikasjonen vår kan tilby:
Tjeneren tilbyr en rekke resurser som leveres i form av JSON objekter, som kan nås gjennom forskjellige endepunkter.
| Metode | Endepunkt | Variabler | Response | Sammendrag |
| ------ | ------ |------ |------ |------ |
| POST | /api/login| JSON: [Login request](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/LoginRequest.java) | autentiserings token | Sjekker om brukeren ligger i databaseb. <br> Hvis burker finnes og passordet er riktig <br> returneres en autentiseringsnøkkel
| GET | /api/users | | Liste med brukere | Finner alle registrerte [brukere](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) |
| POST | /api/user/save | JSON: [User](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) | [Brukeren som ble laget](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) | Legger til en ny bruker i databasen |


Liste over alle ressursene her.

Ta med endepunkter her