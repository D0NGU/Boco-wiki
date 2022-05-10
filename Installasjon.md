## [TJENER](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend)

#### Forutsetninger

For å kjøre applikasjonen lokalt kreves det følgende:
- [Java Development Kit (JDK) 11](https://adoptium.net/?variant=openjdk11) eller høyere
- [Apache Maven 3.8.5](https://maven.apache.org/download.cgi) eller høyere

JDK kreves for å kompilere og kjøre applikasjonen, mens Maven håndterer avhengighetene. 

Databaseløsning: <br>
Tjeneren kan enten benytte en innebygd H2 database eller en ekstern MySQL database som finnes på NTNUs servere. Det er altså ingen krav for lokal databaseløsning. Dersom det er behov for å bruke en annen databaseløsning kan dette konfigureres gjennom Spring Boot (enten ved å lage en ny profil eller ved å modifisere standardprofilen i _src/main/resources/application.properties_).

#### Innstallasjon & Kjøring

##### Kloning av repoet:

```bash
  # Via SSH
  git clone git@gitlab.stud.idi.ntnu.no:idatt2106_2022_08/backend.git

  # Via HTTPS
  git clone https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend.git
```

##### Kjøring:

For å kjøre applikasjonen lokalt bruk følgende kommandoer:

```cmd
  mvn install
  mvn spring-boot:run
```

For å kjøre applikasjonen mot MySQL serveren må programmet kjøres med 'mysql' profilen. Bruk følgende kommando istedet:

```cmd
  mvn spring-boot:run -'Dspring-boot.run.profiles=mysql'
```

## [KLIENT](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend)

#### Forutsetninger

For å kjøre klient applikasjonen trengs kun [Node.js 16](https://nodejs.org/en/download/) og node package manager (npm).

#### Miljøvariabler

Dersom klient og tjener ikke kjører på samme maskin må serverens addresse settes i klienten. Det er da bare å endre på variabelen 'baseURL' i filen src/service/ApiService.js silk at den peker til serveren.

#### Innstallasjon & Kjøring

##### Kloning av repoet:

```bash
  # Via SSH
  git clone git@gitlab.stud.idi.ntnu.no:idatt2106_2022_08/frontend.git

  # Via HTTPS
  git clone https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend.git
```

##### Innstaller avhengigheter:

```cmd
  npm ci
```

##### Kjøring:

For å bygge og kjøre applikasjonen i utviklingsmodus kjør:

```cmd
  npm run serve
```

For å kompilere optimaliserte filer (disse filene havner i /dist mappen):

```cmd
  npm run build
```