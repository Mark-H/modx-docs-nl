# Zoekmachine vriendelijke URLs gebruiken

Het activeren en configureren van zoekmachine vriendelijke URLs gaat in 2 stappen. Het aanzetten van de functie in MODX, en het instellen van de server. 

## 1. FURLs aanzetten in MODX
Ga naar Systeem en dan Systeem Instellingen bunnen de MODX Manager. Kies in de Gebied dropdown voor vriendelijke urls. Je ziet nu alle settings die daarmee te maken hebben. 
Zet aan:
- use_friendly_urls
- automatic alias
- use_alias_path

MODX zal nu urls bouwen op basis van de resource aliases en die van de bovenliggende pagina’s. 

## 2. Instellen van de Server.

- apache, of nginx met apache reverse proxy/IIS met volledige htaccess functionaliteiten (mod rewrite): hernoem ht.access in de root van de site naar .htaccess. Indien de MODX installatie niet in de root is geplaatst, pas dan ook de RewriteBase aan.
- IIS zonder mod rewrite
- nginx zonder mod rewrite
- ....