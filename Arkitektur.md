
![SystemArchitecture](uploads/cf09a61be0b5e4ccd76c9430b70ccdbb/SystemArchitecture.png)


## Klient
Klienten i dette prosjektet er en vue basert javascript klient. Klienten burker axios sitt bibliotek for rest forespørseler for å kommunisere med tjenesten. Forespørreslene varier om de bruker JSON objekter eller query og path variabler for komunikasjon.

## Tjener
Tjeneren er bygget på Spring boot som er ett bibliotek for rest APIer. Tjeneren støtter Open authentication med JWT tokens for sikkerhet. APIet støtter mange forskjellige endepunkter og har en rekke funksjoner for å returne data i forskjellige modeller. APIet komuniserer kan kommunisere både med en H2 in memory database, eller en mySQL database. For att en klients forespørsel skal nå databasen må den gå igjenomm 4 lag. I første omgang når tjener sikkerhets laget som sjekker at klienten har en autorisert token. Hvis ikke returner tjeneren en 403(UNAUTHORISED) melding. Deretter behandler en kontroller forespørselen, om det er behov for mer komplisert logikk blir en service klasse involvert. Til slutt brukes en reposotiry klasse for å hente ønsket data fra databasen.

## Lagring
Hvis tjeneren er satt opp for å kommuniser med mySQl, kobles apiet opp mot en database i NTNUs mySQL server. Databasen sikkrer persistens for lagring av brukere, produkter, utleieavtaler og anmeldelser. I H2 profilen kobles tjeneren opp mot en h2 in memory database. Denne databasen er hovedsakelig for testing siden den ikke støtter persistens