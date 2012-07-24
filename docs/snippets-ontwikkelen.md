# Snippets Ontwikkelen

Zoals op de Tag Syntax pagina uitgelegd, is een snippet het makkelijkste te vergelijken met een PHP functie: je roept hem aan waarbij je properties (parameters) meegeeft, en de snippet geeft dan het resultaat daarvan terug.

Een snippet moet dus aan de volgende eisen voldoen:
- het is geschreven in PHP
- indien van toepassing worden properties gebruikt om het resultaat of de logica aan te passen
- er wordt een waarde teruggegeven, bij voorkeur door een “return” statement aan het einde van de code.

Een voorbeeld van een “helloWorld” snippet:

<?php
$name = $modx->getOption('name', $scriptProperties, 'Anonymous Coward');
return "Hi there, {$name}!";

Wat je als volgt in je template zou aanroepen:

[[helloWorld? &name=’John Doe’]]

wat het volgende tot resultaat zou hebben:

Hi there, John Doe!

Dit is een simpel voorbeeld, maar laat wel zien hoe je met gebruikersinput kunt werken.

Hieronder gaan we dieper in op bepaalde aspecten van het ontwikkelen van snippets en aspecten van de MODX API je daarbij kunnen helpen. Ook kun je een codestijl advies hier vinden.

## Snippet Properties gebruiken en definiëren
Properties werken voor alle elementen waaronder plugins en chunks, maar worden toch het meest gebruikt met snippets. Properties geven de eindgebruiker de mogelijkheid de logica in de snippet of het resultaat te configureren, wat snippets heel flexibel kunnen maken. Kijk alleen maar naar getResources en de oneindige mogelijkheden die je daarmee krijgt. 

Snippet properties zijn in veel gevallen erg nuttig en met weinig moeite te implementeren. Wenselijke properties zijn bijvoorbeeld: 
- tpl (“template”) properties, waarmee je een chunk inlaad zodat de resulterende html kan worden aangepast.
- separator property welke gebruikt wordt om individuele resultaten van elkaar te scheiden. 
- where, parents en andere properties om resultaten in of uit te sluiten. 
- js, css en dergelijke properties waarmee standaard in te laden assets worden weggelaten.
En ga zo maar door. Eigenlijk zou je met deze properties moeten proberen te voorkomen dat er ook maar iets niet veranderd kan worden in het resultaat van de snippet.

### Hoe gebruik je een snippet property?
Het afvangen van een snippet property kan op vele manieren, maar het is aan te raden om modX.getOption te gebruiken. Deze methode accepteert 4 parameters (meestal worden er maar 3 gebruikt): de naam van de property, de bron, en een standaardwaarde als de property niet is gedefinieerd. De 4e parameter geeft aan of de standaardwaarde gebruikt moet worden als de property leeg is. De 2e parameter, de bron, geeft aan waarin gezocht moet worden, dit is bij een element $scriptProperties - een array met alle gedefinieerde properties. Met getOption kan je ook systeem instellingen opvragen: specificeer dan “null” als bron.

Je kan ook gewoon $scriptProperties['property'] gebruiken, maar als de property dan niet is gedefinieerd veroorzaak je een E_NOTICE error - iets wat je dan weer zou moeten voorkomen door isset te gebruikem. getOption doet dit al voor je, dus maakt het allemaal weer wat makkelijker.

## Het gebruik van tpl Chunks
In het allereerste voorbeeld op deze pagina kunnen we iets niet aanpassen, namelijk de tekst “Hi there” en het daarop volgende uitroepteken. Dit is voor zo’n simpele snippet misschien nog wel acceptabel, maar zodra snippets groter worden of door meer mensen gebruikt wordt, zullen mensen sneller zoiets anders nodig hebben.

Wat we dan kunnen doen is een chunk gebruiken als tpl (“template”) en om daar onze waardes (in dit geval de naam) in te plakken.

Naast onze snippet gebruiken we dan dus ook een chunk. Neem als voorbeeld het volgende (naam: helloWorldTpl):

Hi there, [[+name]]!

In onze snippet roepen we die dan als volgt aan:

<?php
$name = $modx->getOption('name', $scriptProperties, 'Anonymous Coward');
return $modx->getChunk('helloWorldTpl', array ('name' => $name));

Nu kan de gebruiker van de snippet dus gewoon de chunk helloWorldTpl aanpassen als deze een andere tekst of extra html wil hebben. Nu is het enige probleem nog dat wanneer we deze snippet als Extra aan gaan bieden, mensen mogelijk een keer gaan updaten waarbij de chunk ookweer veranderd wordt. Dus gaan we nog een stapje verder, en gebruiken we ook een property voor de naam van de chunk.

<?php
$name = $modx->getOption('name', $scriptProperties, 'Anonymous Coward');
$tpl = $modx->getOption('tpl', $scriptProperties, 'helloWorldTpl');
return $modx->getChunk($tpl, array ('name' => $name));

Nu kan de eindgebruiker de chunk simpelweg dupliceren, en de nieuwe naam meegeven aan de snippet in de tpl property.

## Hoe noem je de properties die je gebruikt?
Hoewel er geen verplichte standaard is, helpt het om het volgende te gebruiken als leidraad:

- Gebruik camelCase voor properties.
- Begin een tpl chunk altijd met “tpl” gevolgd door een eventuele aanvulling. Bijvoorbeeld “tpl”, “tplFirst”, “tplLast” en “tplOdd”. Indien een specifieke tpl als “tplFirst” niet is ingevuld dient deze standaard de waarde van “tpl” over te nemen.
- wees consistent in de benaming: “showHidden”, “showUnpublished” en “showDeleted” in plaats van “excludeHidden”, “publishedOnly” en “noDeleted”. 
- gebruik goede, algemene standaardwaarden en standaard output. 
- Indien de snippet vrijgegeven wordt als Extra, hou rekening met backward compatibility en gebruik semantic versioning voor je versienummers.
- bied een “debug” property aan welke de gekozen properties en enkele stappen van de logica naar het error log stuurt, zodat gebruikers problemen kunnen vaststellen bij complexere snippets. 