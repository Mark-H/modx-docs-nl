# Plugins Ontwikkelen

Een Plugin is binnen MODX een stukje php welke uitgevoerd wordt op een bepaald moment. Plugins worden uitgevoerd wanneer ze aan een system event (in andere systemen een “hook”) gekoppeld zijm, en die system event wordt in de core of een uitbreiding aangeroepen.

Een plugin die gekoppeld is aan de “OnWebLogin” event wordt bijvoorbeeld uitgevoerd als een gebruiker in de frontend inlogt, en “OnPageNotFound” als de opgevraagde URL niet bestaat. Er zijn een heleboel events waar een plugin aan gekoppeld kan zijn, en elke heeft weer eigen beschikbare gegevens en verwachte resultaten.