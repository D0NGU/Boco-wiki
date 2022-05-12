For sikkerhet har applikasjonen blitt sjekket opp mot OWASP sin liste over [Top Ten Web Application Security Risks](https://owasp.org/www-project-top-ten/).

## Adgangskontroll

Meningen med adgangskontroll er at brukere ikke skal kunne nå data/funksjoner som ikke var tiltenkt dem.

BoCo nettstedet benytter tokens for autentisering. Her blir [JWT](https://jwt.io/) (JSON web token) brukt for å digitalt signere hvert kall til serveren. Når brukeren har logget inn må hvert påfølgende kall inkludere en token. Denne tokenen tillater brukeren å nå flere funksjoner (som endepunktene for å lage/slette produkt) som brukeren skal ha tilgang til.

## Sensetiv dataeksponering

Siden BoCo nettsiden krever innlogging må det lagres noe informasjon om brukerene. Her må brukerene oppgi fullt navn, en epost-addresse og ett passord. Navn og epost lagres som ren tekst i databasen, mens passord krypteres på serversiden.

#### Passord

For å kryptere passordene benyttes en kjent hashing funksjon kalt [bcrypt](https://en.wikipedia.org/wiki/Bcrypt). Bcrypt hasher passordet med en gitt algoritme i tillegg til å inkludere et salt for å beskytte mot oppslag i '[rainbow tables](https://en.wikipedia.org/wiki/Rainbow_table)'.

Inndata til bcrypt funksjonen er passordet, mens utdataen er en string på formen:

`$2a$10$0hPXuqJNow2KA5KZy.2XmezgbLvemDCCjPQbhlLRG204LNDkaYV5.`

Denne stringen består av

- `$2a$`: Bcrypt identifikatoren
- `10`: Kostnad, altså hvor mange ganger passordet hashes (her 2<sup>10</sup> = 1024 ganger). 
- `0hPXuqJNow2KA5KZy.2Xme`: Tilfeldig salt (Radix64 kodet)
- `zgbLvemDCCjPQbhlLRG204LNDkaYV5.`: Beregnet hash (Radix64 kodet)

<pre>
$2a$10$0hPXuqJNow2KA5KZy.2XmezgbLvemDCCjPQbhlLRG204LNDkaYV5.
\_/ \/ \____________________/\_____________________________/
Alg Kost       Salt                        Hash
</pre>

Dersom databasen komprimeres vil angreperne kun finne denne typen string, og det vil ta mer tid/krefter for å finne brukerenes faktiske passord.

## Kodeinjeksjon

En av de større sikkerhetshullene kommer i form av kodeinjeksjon. Dette er når f.eks. inndata ikke sjekkes før det sendes inn til databasen.

#### SQL-injeksjon

I BoCo klienten vil alt av inndata sjekkes før det sendes til serveren. Dette vil si at det ikke er mulig å injisere SQL-setninger fra inndata-feltene på nettstedet. På serversiden benyttes APIen kalt Java Database Connectivity (JDBC). JDBC er det som kobler til og kjører spørringer mot databasen. Ved hjelp av prepared statements skal muligheten for injection angrep være redusert.

## Scripting på nettstedet (XSS)

På klientsiden blir rammeverket Vue benyttet. Vue håndterer innsetting av alt HTML-innhold, og sørger for at eventuell kode ikke blir tolket som JavaScript og kjørt av nettleseren.