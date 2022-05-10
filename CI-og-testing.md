## Kontinuerlig integrasjon (CI)

Kontinuerlig integrasjon for både klient og tjener skjer gjennom [GitLab Pipelines](https://docs.gitlab.com/ee/ci/pipelines/).

Pipelines sørger for å kjøre kommandoer i forskjellige faser. For både klient og tjener er det to faser hvor prosjektet henholdsvis kompileres og testes. Dersom noe går galt (avhengighet finnes ikke, en test feiler, osv.) vil hele pipelinen mislykkes. Det er også en egen fase for å generere JavaDoc og laste det opp til GitLab.

GitLab Pipelines benyttes altså for å sjekke at funksjon fortsatt fungerer etter hver commit og før hver merge.

## Testing



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

###### Backend
[![pipeline status](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/badges/main/pipeline.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/commits/main) 
[![coverage report](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/badges/main/coverage.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/backend/-/commits/main)

###### Frontend
[![pipeline status](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/badges/main/pipeline.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/-/commits/main)
[![coverage report](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/badges/main/coverage.svg)](https://gitlab.stud.idi.ntnu.no/idatt2106_2022_08/frontend/-/commits/main)