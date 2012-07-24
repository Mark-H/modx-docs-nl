# Docs - Tag Syntax

Binnen een MODX Template gaat het om jouw html en door middel van tags een vleugje MODX. Dit artikel bied de nieuweling maar ook gevorderden een handige referentie en uitleg van de mogelijkheden.

## Referentietabel

(van engelse docs)

## De verschillende Tags uitgelegd

De tabel hierboven ziet er misschien eng en groot uit, maar eigenlijk valt het best mee. En zodra je die kent en begrijpt, weet je bijna alles wat je moet weten om een site te bouwen!

### Resource Velden: [[*pagetitle]]
Een Resource Veld kan twee dingen vertegenwoordigen. Allereerst een standaard resource veld als de paginatitel, de introductietekst of de inhoud. Alle standaardvelden die bij een resource horen vind je hier. (LINK)

Maar dezelfde tagstructuur wordt ook gebruikt voor zogenaamde Template Variabelen. Deze TVs zijn de MODX implementatie van custom velden en hebben een waarde per resource. Als je een TV met naam "sidebar" hebt gemaakt, kan je de waarde hiervan dus met [[*sidebar]] opvragen. 

Samenvattend betreft deze tag (met het sterretje) dus altijd data over de huidige resource.

### Snippets: [[naam]]
Door middel van een snippet kun je in je template dynamische functionaliteiten toevoegen. Je plakt simpelweg de snippet tag met eventuele opties (zie properties beneden), en de snippet wordt vervolgens daar uitgevoerd om een dynamisch menu, galerij of wat dan ook weer te geven.

Via Pakket Management kan je honderden Extras installeren, welke je vaak als Snippet gebruikt. In je template.

Een snippet is een stukje PHP en werkt eigenlijk als php functie binnen je template. Lees meer over het ontwikkelen van Snippets.

### Chunks [[$chunknaam]]
Chunks zijn brokken HTML (al kan je er in kwijt wat je wilt: css, csv, xml, plaintext, eigenlijk alles behalve php). Deze worden over het algemeen op 2 manieren gebruikt. 

Allereerst gebruik je chunks om stukken html die je herhaalt in op te slaan. Stel je hebt 5 templates, elk met dezelfde footer. Door de footer in een chunk te zetten, en vervolgens deze chunk in elke template aan te roepen, zorg je ervoor dat de site goed te onderhouden valt. Als je iets moet aanpassen in je footer, pas je simpelweg de chunk aan en dan is het overal aangepast.

Daarnaast worden chunks gebruikt voor het scheiden van logica (php) en markup (html) in snippets. De snippet wordt vaak zo geprogrammeerd dat deze een chunk aanroept die je gekozen hebt, waar vervolgens placeholders worden gebruikt om waardes in te plaatsen. Abstract verhaal misschien, maar gezien de flexibiliteit die dit oplevert is er geen één simpele uitleg die alles omvat. We gaan elders dieper op deze methodes in.


### Placeholders: [[+pagetitle]]
Een placeholder is ook weer een geval apart. Placeholders worden niet door de core ingesteld, maar snippets, plugins of tags bepalen de waarde hiervan. 

Je komt ze het vaakst tegen wanneer je met een snippet werkt die je door middel van chunks de mogelijkheid bied de output aan te passen. In deze tpl chunk gebruik je placeholders om waardes in de html te plaatsen. Kijk voor een voorbeeld naar de Wayfinder documentatie.

### Interne link tag: [[~15]]
Een core functie van MODX zijn zogenaamde vriendelijke urls (“FURLs”), wat inhoud dat een bepaalde pagina op een url beschikbaar is welke op basis van de resource hiërarchie en aliassen wordt samengesteld.

Om te voorkomen dat links naar pagina’s breken zodra deze hiërarchie of aliassen veranderen, kun je met de interne link tag de link automatisch laten genereren. Plaats simpelweg het resource ID na het golfje en er komt een link naar de pagina uitrollen.