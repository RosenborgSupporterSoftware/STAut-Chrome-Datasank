# STAut-Chrome-Datasank

Et forsøk på en Chrome extension som kan installeres for å samle inn setedata til STAut

## Bakgrunn

TicketMaster (hei hei til dere!) ønsker tilsynelatende ikke at vi skal laste ned og dekode deres data og bruke dem til våre formål, ettersom de har iverksatt tiltak for å sørge for at tradisjonelle STAut-metoder ikke får tilgang til data.

Dette er selvfølgelig ikke akseptabelt, og vi kan ikke legge oss ned for å dø.

## Løsning

Dette repo'et er ÉN mulig løsning på problematikken, og ikke nødvendigvis hverken den eneste eller beste. Dette er å regne som et teoretisk prosjekt inntil det plutselig ikke er det lenger.

TicketMaster selv er avhengige av disse datafilene for å presentere setekart til brukere som vil kjøpe billetter til kamper på Lerkendal. Derfor er de tilgjengelige for vanlige webbrowsere. Det er ikke noe problem å få tak i dem så lenge man har en full browser til å gjøre jobben for seg. Dette prosjektet forsøker å automatisere sankingen av disse datafilene ved hjelp av en Chrome Extension.

Følgende scenario er grunntanken:

- Bruker laster ned vår Chrome extension. Dette vil typisk være RBKweb-brukere, eller de som følger STAut på Twitter eller Facebook.
- Så lenge brukeren er online vil extension laste kampoversikt og enkeltkamp-sider med jevne mellomrom. **Usikkerhetsmoment: Vil man måtte ha en tab åpen for å få til dette? Eller kan scriptet gjøre alt i en skjult tab? Mer forskning på extensions kreves.**
- Nye kamper (eventinfo.properties) og setedata (eventid.xml) lastes ned, ev. hentes ut via APIer som chrome.devtools.network.getHAR() og lagres midlertidig på brukers datamaskin.
- Data lastes opp til STAut-tjeneste som tar imot disse datafilene og dytter dem inn i den gode gamle STAut Ingest-prosessen.

## Mulige problematikker

- Hvor mye av dette kan en extension gjøre helt i bakgrunnen, uten å forstyrre brukeren ved å kreve åpen tab eller spise all RAM osv.?
- Bør vi bekymre oss for brønnpissere som vil mate dårlige data inn i ny webtjeneste som tar imot datafiler? Må vi ev. sikre oss med brukernavn/passord e.l. og sjalte ut utro tjenere?
- Bør vi sentralisere avgjørelsen om hvor ofte/når på døgnet hver browser henter data? Burde de spørre webtjenesten, som ser "akkurat nå har jeg 8 stk. online, så vi spacer dem ut så de henter hvert 7:30". Kontinuerlig oppdatert når en klient kommer og går på ett eller annet vis. Bedre måte?

## Oppsider med denne metoden

- Forhåpentligvis gjør en browserbasert datasanking at TicketMaster ser veldig liten return on investment i å komplisere dette ytterligere. Så lenge de selv bruker disse dataene, er sjansen god for at vi får tak i dem. Er det verdt det å skrive om dette her totalt for å holde oss unna? Kanskje. Jeg håper ikke.
- Denne metoden gjør at vi plutselig kommer fra mange forskjellige IP-adresser, isteden for én server som i dag. Vanskeligere å se vår trafikk som unormal.

# Videre diskusjon

Kom veldig gjerne med innspill, momenter, alt mulig som issues i dette repo'et. Jeg vil bruke litt fritid fremover på å lese meg opp på Chrome Extensions (og hvor lett de kan brukes i andre browsere ev.). Jeg tenker at vi bruker RFC-modellen. Hvert moment, innspill, mulige problem osv. blir et issue, en RFC, som diskuteres i egen tråd.
