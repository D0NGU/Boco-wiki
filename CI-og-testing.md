## Kontinuerlig integrasjon (CI)

Kontinuerlig integrasjon for både klient og tjener skjer gjennom [GitLab Pipelines](https://docs.gitlab.com/ee/ci/pipelines/).

Pipelines sørger for å kjøre kommandoer i forskjellige faser. For både klient og tjener er det to faser hvor prosjektet henholdsvis kompileres og testes. Dersom noe går galt (avhengighet finnes ikke, en test feiler, osv.) vil hele pipelinen mislykkes. Det er også en egen fase for å generere JavaDoc og laste det opp til GitLab.

GitLab Pipelines benyttes altså for å sjekke at funksjoner fortsatt fungerer etter hver commit og før hver merge.

## Testing

Etterhvert som kode ble skrevet ble det også skrevet tester. Disse enhettestene tester mindre deler av programmet, slik at man ser dersom noe har endret seg.

#### Type tester

For å skrive og kjøre enhetstester ble det brukt to forskjellige test-rammeverk. For server-applikasjonen ble det brukt [JUnit](https://junit.org/junit5/), og på klientsiden ble det brukt [Jest](https://jestjs.io/). Jest er et rammeverk for enhetstesting som støtter Vue.

#### Hvordan kjøre tester

Etter prosjektene er [installert lokalt](Installasjon) kan man henholdsvis kjøre

```cmd
  npm run test:unit
```
eller
```cmd
  mvn clean test
```
for å teste klient eller tjener.

#### Testdekning

På både klient og serversiden blir det generert en rapport for test-dekningsgrad. Denne dekningsgraden blir så plukket opp av GitLab etter pipeline kjører. Dekningsgraden forteller oss blant annet hvor mange linjer av kode om blir kjørt under testing.

###### Backend

For å finne dekningsgrad for JUnit testene må vi benytte et eksternt bibliotek. [JaCoCo](https://www.jacoco.org/jacoco/) er et slikt bibliotek, og genererer en detaljert dekningsrapport.

[![pipeline status](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/badges/main/pipeline.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/commits/main) 
[![coverage report](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/badges/main/coverage.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/commits/main)

###### Frontend

Jest gjør det lett å hente dekningsgrad for testene. Ved å sette **collectCoverage** i jest.config.js vil Jest generere data for testdekning.

[![pipeline status](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/badges/main/pipeline.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/-/commits/main)
[![coverage report](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/badges/main/coverage.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/-/commits/main)