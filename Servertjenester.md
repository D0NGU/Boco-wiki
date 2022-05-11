Tjeneren tilbyr en rekke resurser. Disse ressursene leveres oftest i form av JSON-objekter, og kan nås gjennom forskjellige endepunkter. 

Som en regel returnerer serveren alltid en HTTP status. Denne statusen indikerer om kallet ble gjennomført riktig. Statusene som blir returnert er som angitt av [REST APIen](https://www.restapitutorial.com/lessons/httpmethods.html).



## Endepunkter

- [Innlogging](#innlogging)
- [Bruker](#bruker)
- [Produkt](#produkt)

### Innlogging
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| POST | /api/login | JSON: [Login request](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/LoginRequest.java) | autentiserings token | Sjekker om brukeren ligger i databasen. <br>Hvis burker finnes og passordet er riktig <br>returneres en autentiseringsnøkkel |
| POST | /api/forgot_password | Request parameter: email | Boolean | Sender en glemt passord email til brukeren. <br>Sjekker om emailen kunne sendes. Returnerer true hvis det lykkes og false hvis det feiler |
| PUT | /api/reset_password | Request parametere: token, password | Boolean | Setter passored lik det innsendte passored, bruker token for å validere bruker |

### Bruker
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| GET | /api/users |  | Liste med brukere | Finner alle registrerte brukere |
| POST | /api/user/save | JSON: [User](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) | Brukeren som ble laget | Legger til en ny bruker i databasen |
| DELETE | /api/user/delete | Request parametere: <br>userId og password | Streng med konfirmasjon om at bruker ble slettet | Sletter en gitt bruker fra databasen. Sjekker at passordet er riktig for å forhindre at en bruker sletter en bruker den ikke eier. |
| POST | /api/user/edit | JSON: [editUserRequest](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/EditUserRequest.java) | Endret [user](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) | Endrer en bruker å returnerer den nye versjonen |
| GET | /api/user/get/{email} | Path variabel: email | [User](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) med gitt email | Finner en bruker basert på email |
| GET | /api/user/{userId}/vertified | Path variabel: userId | Boolean | Sjekker om en bruker er verifisert. <br>Returnere true eller false |
| GET | /api/user/get | Request parameter: userId | [User](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/User.java) med gitt id | Finner bruker med oppgitt id |
| POST | /api/user/{userId}/description | Path variabel: userId <br>JSON: descirption(String) |  | Legger til en beskrivelse for en eksisterende bruker |
| GET | /api/user/{userId}/description | Path variabel: userId | JSON: descirption(String) | Finner beskrivelsen til en bruker |
| PUT | /api/{userId}/picture | Path variable: userId <br>JSON: [ImgString](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/ImgString.java) | Verifikasjon tekst | Lagrer ett profil bilde i databasen, hvis det alt ligger ett blir det endret |
| GET | /api/{userId}/picture | Path variable: userId | base64 encoded bilde | Finner profilbilde til gitt bruker |

### Produkt
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| POST | api/products | JSON: [Product](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Product.java) | Verifikasjons melding | Legger til ett produkt i databasen |
| PUT | api/products/{productId} | Path variabel: productId <br>JSON: [Product](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Product.java) | Verifikasjons melding | Endrer ett gitt produkt i databasen |
| GET | api/products/{productId} | Path variabel: productId | [Product](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Product.java) | Finner ett gitt produkt i databasen |
| GET | api/products/{productId}/availability | Path variabel: productId | Liste med [availability windows](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/AvailabilityWindow.java) | Finner en liste med fra til dato vinduer hvor ett produkt er ledig |
| POST | api/products/{productId}/image | Path variabel: productId <br>JSON: list med [product image](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/ProductImage.java) | Verifikasjons melding | Legger til nye bilder for ett produkt |
| GET | api/products/search | Request parametre: q(søke ord) frivillig<br>category frivillig<br>sortBy ascending(true/false) | Sortert liste med [produkter](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Product.java) | Lager en sortert liste med produkter basert på forskjellige request variabler. Noen av variablene kan stå som null. |
| GET | api/products/user/{userId} | Path variabel: userId | List med [usersProducts](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/UsersProducts.java) | Finner alle produktene som hører til en bruker |
| GET | api/products/user/{userId}/history | Path variabel: userId | Liste med [produkter](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Product.java) | Finner alle produktene en bruker har leid |
| DELETE | api/products/{userId}/delete | Path variabel: userId, Reqeust variabel productId | Verifikasjons streng | Sletter ett gitt produkt hvis userId er produktets eier. |

### Listings
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| GET | api/listing/{productId | Path variabel: productId | Gitt [Listing](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Listing.java) | Finner en listing for ett gitt produkt. En listing er ett kompositt av all info relevant for ett gitt produkt |

### Kategorier
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| GET | api/categories | | Liste med [categories](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Category.java) | Finner alle kategoriene i database | 
 
### Varslinger
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| GET | api/alerts/user/{userid} | Path variable: userId | Brukers [alerts](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Alert.java) | Finner alle varslene for en bruker |
| POST | api/alerts/user/{userid}/newAlert | Path variable: userId, JSON: [alert](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Alert.java) | Verifikasjons melding |Legger til en ny varsel på en bruker |
| GET |api/alerts/user/{userid}/unseen | Path variable: userId | Brukers usette [alerts](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Alert.java) | Finner alle varslene som en bruker ikke har sett |
| PUT | api/alerts/seen/{alertId} | Path variable: alertId | Verifikasjons melding | Endrer en gitt varsling til sett |
| DELETE | api/alerts/{alertId}| Path variable: alertId | Verifikasjons melding | Sletter en gitt varsling |

### Kontakt skjema
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| POST | api/contact | JSON: [contactForm](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/ContactForm.java) | Verifikasjons melding | Lagrer en ny kontakt annonse |

### Leieavtaler
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| POST | api/rentals | JSON: [rental](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Rental.java) | Verifikasjons melding | Legger til en ny rental i databasen, hvis mulig |
| GET | api/rentals/product/{id} | Path variabel: id | Liste med [rentals](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Rental.java) | Finner alle leie avtaler for ett produkt |
| GET | api/rentals/product/{id}/{accepted} | Path variabel: id, accepted | Liste med [rentals](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Rental.java) | Finner alle leie avtaler for ett produkt hvor accepted er true/false |
| GET | api/rentals/user/{id} | Path variabel: id | Liste med [rentals](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Rental.java) | Finner alle leie avtaler med gitt bruker id |
| PUT | api/rentals/accepted/{rentalId} | Path variabel: rentalId | Verifikasjons melding | Aksepterer en leie avtale, hvis produktet er ledig i perioden |
| DELETE | api/rentals/{rentalId} | Path variabel: rentalId |  Verifikasjons melding | Sletter en leieavtale |

### Anmeldelser
| Metode | Endepunkt | Variabler | Respons | Sammendrag |
|--------|-----------|-----------|---------|------------|
| POST | api/review | [review](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Review.java) | Verifikasjons melding | Legger til en ny anmeldelse og lager en varsel for anmeldt bruker |
| GET | api/review/{reviewId} | Path variabel: reviewId | JSON: [review](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Review.java | Finner anmeldelse med gitt id |
| GET | api/review | Request parametere: subject (integer, frivillig), author (integer, frivillig) | Liste med [reviews](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/blob/main/src/main/java/ntnu/idatt/boco/model/Review.java) | Finner anmeldelser for en bruker, eller for en forfatter. Kan også finne for både forfatter og subjekt|
| GET | api/review/user/{userId}/average | Path variabel: userId | Double | Finner totale gjennomsnitts ratingen for en bruker | 
| GET | api/review/user/{userId}/average | Path variabel: userId | Double | Finner eier ratingen for en bruker | 
| GET | api/review/user/{userId}/average | Path variabel: userId | Double | Finner leier ratingen for en bruker |
| GET | api/review/user/{userId}/amount | Path variabel: userId | Integer | Finner antal reviews |

Liste over alle ressursene her.

Ta med endepunkter her