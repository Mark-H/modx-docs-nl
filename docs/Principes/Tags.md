# Docs - Tag Syntax

Binnen een MODX Template gaat het om jouw html en door middel van tags een vleugje MODX. Dit artikel bied de nieuweling maar ook gevorderden een handige referentie en uitleg van de mogelijkheden.

## Referentietabel


| Tag / Element | Revolution (2.x) | Evolution (1.x) |
|---|---|---|
| Resource Veld | [[*pagetitle]] | [\*pagetitle*]|
| Template Variabele | [[*pagetitle]] | [\*pagetitle*]
| Chunk | [[$chunkNaam]] | {{chunkNaam}}
| Snippet (cached) | [[snippetNaam]] | [[snippetNaam]]
| Snippet (uncached) | [[!snippetNaam]] | [!snippetNaam!]
| Placeholders | [[+placeholderNaam]] | [+placeholderNaam+]
| Interne Link | [[~5]] | [~5~]
| Systeem Installingen | [[+systeem_instelling]] | [(systeem_instelling)]
| Lexicon | [[%lexicon]] | *bestaat niet in Evo*
| Comment/Notitie | [[- commentaar ]] | *bestaat niet in Evo*


Deze tabel ziet er misschien eng en groot uit, maar eigenlijk valt het best mee. Het mooie is dat je met de informatie uit die tabel eigenlijk alles al weet om je site in MODX te bouwen. Leer hem uit je hoofd of print hem uit, en de rest komt dan vanzelf. 

Hieronder gaan we even kort in op de verschillende soorten tags, met links naar meer specifieke informatie mocht het onduidelijk zijn.

### Resource Veld & Template Variabele: `[[*pagetitle]]`

De tag syntax met een sterretje (*) kan twee waardes vertegenwoordigen: of een [Resource](/Principes/Resource) Veld, of de waarde van een [Template Variabele](/Principes/Template-Variabele). De overeenkomst tussen beide is dat ze allebei een waarde specifiek aan de huidige Resource hebben. 

Een resource veld bevat bijvoorbeeld de waarde van de paginatitel (`[[*pagetitle]]`), de introductietekst (`[[*introtext]]`) of de inhoud (`[[*content]]`). Deze velden zijn ingebouwd in de core van MODX en zijn dus altijd beschikbaar (of ze een waarde hebben is een ander verhaal, natuurlijk). Alle standaardvelden die bij een resource horen en meer informatie over wat Resources zijn vind je op de [Principes/Resource](/Principes/Resource) pagina. 

Dezelfde tagstructuur met het sterretje wordt ook gebruikt voor zogenaamde [Template Variabelen](/Principes/Template-Variabele). Deze "TVs" zijn de MODX implementatie van custom velden en hebben een waarde per resource. Als je een TV met naam "sidebar" hebt gemaakt, kan je de waarde hiervan dus met `[[*sidebar]]` opvragen. 

Samenvattend betreft deze tag (met het sterretje) dus altijd data **over de huidige resource**.

### Snippets: `[[naam]]`

Door middel van een [snippet](/Principes/Snippet) kun je in je template dynamische functionaliteiten toevoegen. Je plakt simpelweg de snippet tag met eventuele opties (zie *Properties* later in dit document), en de snippet wordt vervolgens uitgevoerd om een dynamisch menu, galerij of wat dan ook weer te geven. Deze waarde geeft hij dan terug en zie je terug op je pagina.

Via [Pakket Management](/Tools/Pakket-Management) kan je honderden Extras installeren, welke heel vaak gebruik maken van snippets om een bepaalde functionaliteit waar te maken.

Een snippet is een stukje PHP en werkt eigenlijk als php functie binnen je template. Lees meer over het ontwikkelen van Snippets. 

### Chunks `[[$chunknaam]]`
Chunks zijn brokken HTML (al kan je er in kwijt wat je wilt: css, csv, xml, plaintext, eigenlijk alles behalve php). Deze worden over het algemeen op 2 manieren gebruikt. 

Allereerst gebruik je chunks om stukken html die je herhaalt in op te slaan. Stel je hebt 5 templates, elk met dezelfde footer. Door de footer in een chunk te zetten, en vervolgens deze chunk in elke template aan te roepen, zorg je ervoor dat de site goed te onderhouden valt. Als je iets moet aanpassen in je footer, pas je simpelweg de chunk aan en dan is het overal aangepast.

Daarnaast worden chunks gebruikt voor het scheiden van logica (php) en markup (html) in snippets. De snippet wordt vaak zo geprogrammeerd dat deze een chunk aanroept die je gekozen hebt, waar vervolgens placeholders worden gebruikt om waardes in te plaatsen. Abstract verhaal misschien, maar gezien de flexibiliteit die dit oplevert is er geen één simpele uitleg die alles omvat. We gaan elders dieper op deze methodes in.


### Placeholders: `[[+pagetitle]]`
Een placeholder is ook weer een geval apart. Placeholders worden niet door de core ingesteld, maar snippets, plugins of tags bepalen de waarde hiervan. 

Je komt ze het vaakst tegen wanneer je met een snippet werkt die je door middel van chunks de mogelijkheid bied de output aan te passen. In deze tpl chunk gebruik je placeholders om waardes in de html te plaatsen. Kijk voor een voorbeeld naar de Wayfinder documentatie.

### Interne link tag: `[[~15]]`
Een core functie van MODX zijn zogenaamde vriendelijke urls (“FURLs”), wat inhoud dat een bepaalde pagina op een url beschikbaar is welke op basis van de resource hiërarchie en aliassen wordt samengesteld.

Om te voorkomen dat links naar pagina’s breken zodra deze hiërarchie of aliassen veranderen, kun je met de interne link tag de link automatisch laten genereren. Plaats simpelweg het resource ID na het golfje en er komt een link naar de pagina uitrollen.