# Plugin

Een Plugin in MODX is een functie die uitgevoerd wordt op een bepaald moment door middel van een verwijzing naar een Systeem Event. Er zijn zo'n 150 systeem events op het moment, varierend van OnPageNotFound voor wanneer er geen resource gevonden kan worden voor een bepaalde url, tot OnInitCulture wat vroeg in een request wordt uitgevoerd.

Door middel van plugins is het mogelijk om veel van de core zich anders te laten gedragen. Het is bijvoorbeeld mogelijk om een login poging langs een extern login systeem te laten gaan, of om op basis van een domeinnaam een andere [context](/Principes/Context) in te laden. 