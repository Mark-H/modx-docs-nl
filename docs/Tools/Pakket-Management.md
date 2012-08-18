# Pakket Management

Pakket Management, beschikbaar in het Systeem menu binnen de MODX Manager, is een tool waarmee je zogenaamde Pakketten kunt downloaden en installeren in MODX. Een Pakket is een .zip bestand en praktisch hetzelfde als een Extra: een uitbreiding voor MODX.

Pakketten bestaan meestal uit [Snippets](/Principes/Snippet), [Plugins](/Principes/Plugin) of [Custom Manager Pagina's](/Principes/Custom-Manager-Pagina), maar ze zijn flexibel genoeg om hele websites inclusief [resources](/Principes/Resource), [gebruikers](/Principes/Gebruiker) en [systeem instellingen](/Principes/Systeem-Instellingen) te installeren.

## Providers
Pakket Management werkt door middel van een REST API met een server. Deze API wordt uigelezen op basis van een zoekopdracht, download instructie van MODX of bij een check of er updates beschikbaar zijn. 

In principe zal je bijna altijd de officiele provider van MODX gebruiken. Deze is standaard geinstalleerd in elke MODX Installatie en bevat alleen goedgekeurde Extras. Toch kan het zo nu en dan voorkomen dat iemand een andere provider aanbied met andere pakketten. Deze kun je eenvoudig toevoegen, maar hou er rekening mee dat **zodra je een pakket installeert, je deze volledige toegang tot je MODX installatie geeft**. Meestal is dit de bedoeling, maar zonder enkele controle over de inhoud van een pakket zou zoiets zelfs een database wachtwoord kunnen lezen, en een script kan deze vervolgens per email opsturen naar de ontwikkelaar. **Gebruik dus altijd je goede verstand**, en installeer niks van providers die je niet kent of niet vertrouwd. 

De officiele MODX provider is als volgt:

- Naam: modx.com
- Service URL: http://rest.modx.com/extras/ (voorheen http://rest.modxcms.com/extras/)
- Omschrijving: *The official MODX transport facility for 3rd party components.*

## Pakketten Installeren
Het installeren van een pakket door middel van Pakket Management is kinderlijk eenvoudig.

Allereerst moeten we een pakket downloaden naar de server. Dit kan op twee manieren: via de Provider, of handmatig. Na de download zullen we het pakket installeren - dit gaat hetzelfde ongeacht de download manier.

### Pakket Downloaden (via Provider)
Ga naar Pakket Management in het Systeem menu. Klik op de **Download Extras** knop, boven de grid (tabel) met geinstalleerde pakketten. 

In het venster wat je nu te zien krijgt, vind je een aantal dingen terug. Links zie je een boomstructuur met daarin de categorieen en subcategorien die beschikbaar zijn binnen de provider. In het midden en rechts in het scherm zie je de populairste en nieuwste pakketten.

Ervan uitgaande dat we weten welk pakket we willen installeren, gaan we de zoekfunctie gebruiken, deze vind je links boven de boomstructuur. Een pakket wat je waarschijnlijk wel wilt gebruiken is Wayfinder, hiermee bouw je menus op de website. Tik `Wayfinder` in het zoekveld, en druk op enter. We krijgen nu een aantal resultaten te zien, waaronder het pakket met de naam "Wayfinder". De overige resultaten gebruiken de tekst "wayfinder" in hun omschrijving, bijvoorbeeld om aan te geven dat deze Wayfinder gebruiken. 

Klik op Bekijk Details onder het pakket met de naam Wayfinder om de omschrijving te lezen. Je zult naast de omschrijving ook installatieinstructies en een changelog vinden. Als je het pakket wilt installeren klik je op Download aan de rechterkant van de pagina, of via de Download knop in de tabel.


### Pakket Downloaden (handmatig)
Mocht je een pakket niet via de provider kunnen downloaden, of je hebt van een ontwikkelaar een beta versie gekregen welke niet beschikbaar is via de provider, dan kun je het handmatig installeren.

Ook als je server geen cURL ondersteund kan je alsnog handmatig pakketten installaren - het is alleen wat meer werk.

Om een pakket handmatig te installeren hebben we een pakketnaam-versie.transport.zip bestand nodig. Deze kunnen we downloaden vanaf de [MODX Site](http://modx.com/extras/) voor elk pakket wat in de Provider beschikbaar is. Zoek daar via de zoekfunctie het pakket op wat je wilt installeren en download het bestand.

Upload dit bestand vervolgens naar de `core/packages/` map op de server. Dit kan via de "Files" tab in de MODX Manager, FTP of SSH - als het bestand maar in die map komt.

Als je het pakket daar hebt geupload, kun je deze binnen MODX registreren. Ga hiervoor naar Pakket Management in het Systeem menu. In plaats van op de Download Extras knop te klikken, klik je op het kleine pijltje aan de rechterkant van de knop. Op dat moment krijg je een submenu te zien met de opties Selecteer een Provider en **Lokaal Zoeken voor Pakketten**. Klik op de laatste. Je krijg dan een melding te zien over dat je het bestand moet uploaden. Dit heb je al gedaan, dus klik op ok. 

Nu zal het pakket in de tabel beschikbaar zijn. 

### Pakketten Installeren

Nu het pakket bekend is bij MODX, kunnen we deze installeren. 

Vind je pakket in de tabel, en klik op de groene Installeer knop. Je krijg nu een venster te zien met links 3 tabjes (Readme, Changelog en Licentie) welke informatie geven over het pakket. Niet alle pakketten zetten hier veel informatie in, maar lees door wat er staat en klik vervolgens op de knop rechtsonder op de pagina.

Indien een pakket opties heeft geconfigureerd, kan het hier naar vragen. Zo niet, krijg je meteen de Console te zien - een AJAX gestuurd overzicht van de installatie stappen en voortgang daarvan.

Soms kan het voorkomen dat je heel veel rode foutmeldingen te zien krijgt. Vaak hoeft dit niks te betekenen, bijvoorbeeld als het pakket probeert een tabel aan te passen die al klopt met het schema. Mocht je twijfelen over de fouten, maak dan een forum post aan met de informatie uit de console - vaak zullen mensen je snel kunnen helpen met het analyseren van de meldingen en of het een echt probleem is.

## Hoe vind ik het juiste pakket?

Vaak helpt het om op een goed keyword te zoeken binnen Pakket Management. "event", "calendar" of "twitter" bijvoorbeeld. Alle gerelateerde pakketten worden dan getoond, waarna je de omschrijving kunt bekijken om te zien wat het precies doet.

Ook kan je Google gebruiken. Door te zoeken op MODX en een passend keyword bij wat je zoekt, zal je vaak forum posts of externe artikelen vinden met tips, vergelijkingen of aankondigingen. 

Veel pakketten zijn erg flexibel, en je zult dus ook niet voor alle doelen een apart pakket nodig hebben. Zo kan je bijvoorbeeld vrijwel alles wat te maken heeft met Resources met 1 pakket doen: getResources. Daarnaast heb je gespecialiseerde pakketten als Wayfinder voor menus en getResourceField om een enkel veld van een andere resource in te laden.










