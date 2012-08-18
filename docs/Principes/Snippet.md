# Snippet

Een snippet is PHP welke op een bepaalde plek in een [template](/Principes/Template) uitgevoerd wordt. Over het algemeen geeft een snippet direct een waarde terug op basis van de [properties](/Principes/Properties) die je mee geeft, maar ook kunnen snippets zogenaamde placeholders instellen welke je vervolgens elders in de template kunt gebruiken.

Een snippet volgt altijd de volgende tag structuur zonder token:

```
Cached:
[[naamVanSnippet? &naamVanProperty=`waardeVanProperty`]]
Uncached:
[[!naamVanSnippet? &naamVanProperty=`waardeVanProperty`]]
```

Aangezien snippets vaak data opvragen uit de database of externe bronnen, is het principe van caching heel erg belangrijk bij Snippets. Door onnodig snippets niet te cachen kun je al snel waardevolle performance van je website opgeven. Sommige snippets moeten wel uncached gebruikt worden omdat deze per paginaverzoek een ander resultaat kan geven, maar deze zullen dat  expliciet in de handleiding aangeven.

**[Lees meer over Caching in MODX](/Principes/Caching)**

## Snippets Ontwikkelen
Zie [Snippet Ontwikkeling](/Principes/SnippetOntwikkeling).

## Beschikbare Snippets

Zie [MODX Extras](http://modx.com/extras/).