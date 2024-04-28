# event-archetypes
The different types of events and literature references



## Data streams vs Event streams
* Wanneer gegevens over gebeurtenissen geen metadata bevatten spreken we over (`data`) en (`data streams`) (bijv. bij sensoren die alleen een pakket ruwe data leveren). Als er wel contextgegevens aanwezig spreken we over (`events`) en (`event streams`) (bijv. bij gebeurtenisgegevens die op basis van metakenmerken moeten worden geïnterpreteerd om verwerkt te kunnen worden) [Project Notificaties Architectuur p57](https://github.com/VNG-Realisatie/notificatieservices/blob/main/docs/achtergronddocumentatie/notificatieservices_architectuur.pdf)




### JWT (JSON Web Token)

- [ ] Use a random complicated key (`JWT Secret`) to make brute forcing the token very hard.
- [ ] Don't extract the algorithm from the header. Force the algorithm in the backend (`HS256` or `RS256`).
- [ ] Make token expiration (`TTL`, `RTTL`) as short as possible.
- [ ] Don't store sensitive data in the JWT payload, it can be decoded [easily](https://jwt.io/#debugger-io).
- [ ] Avoid storing too much data. JWT is usually shared in headers and they have a size limit.


# Haal Centraal BRP update API
![lint oas](https://github.com/BRP-API/Haal-Centraal-BRP-Update-API/workflows/lint-oas/badge.svg)
![ci](https://github.com/BRP-API/Haal-Centraal-BRP-Update-API/workflows/ci/badge.svg)

API waarmee je je kunt abonneren op notificaties over wijzigingen van personen. Bedoeld voor gebruik in combinatie met de [BRP bevragen API](https://vng-realisatie.github.io/Haal-Centraal-BRP-bevragen), bijvoorbeeld om (tijdelijk) lokale kopiegegevens actueel te houden.
De API wordt niet door RvIG aangeboden. Om de transitie naar API's en de besparing op het gegevensmagazijn te versnellen, kunnen gemeenten deze API lokaal aanbieden.  

