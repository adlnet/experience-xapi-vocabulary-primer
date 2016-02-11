## Example xAPI Vocabulary Dataset (Shown in Turtle RDF) {#example-xapi-vocabulary-dataset-shown-in-turtle-rdf}

```
@prefix : <http://myvocab.example.com/xapi/> .
@prefix myvocab10: <http://myvocab.example.com/xapi/1.0/> .
@prefix myvocab20: <http://myvocab.example.com/xapi/2.0/> .
@prefix xapi: <https://w3id.org/xapi/ontology#> .
@prefix adlnet: <https://w3id.org/xapi/adl> .
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

# the above are just bookkeeping for all the prefixes and the current base namespace


# the overall vocabulary, which is the namespace verbs and so forth will be in.
# using just the colon indicates this is just the bare base URI
:
    a skos:ConceptScheme ;
    prov:wasGeneratedBy [
    a prov:Activity ;
        foaf:name "Sports and Competition xAPI Vocabulary Working Group"@en
    ] .


# the current version of the vocabulary, which is connected to the overall vocabulary
# as a specialization, and to the previous version by wasRevisionOf
myvocab20:
    a skos:ConceptScheme ;
    prov:specializationOf : ;
    prov:wasRevisionOf myvocab10: .


# okay, now we're starting to define our verbs. As recommended by SKOS, our concepts
# go in the overall vocabulary namespace, not the version namespaces.
:qualifiedfor
    a xapi:Verb ;
    skos:inScheme : ; # the overall vocabulary again
    skos:inScheme myvocab20: ;
    skos:prefLabel "qualified for"@en ;
    skos:definition "To be accepted as a participant for the Activity object by meeting some set of criteria"@en .

:placed
    a xapi:Verb ;
    skos:inScheme : ;
    skos:inScheme myvocab20: ;
    skos:prefLabel "placed"@en ;
    skos:altLabel "ranked"@en ;
    skos:definition "To achieve a ranked outcome in the Activity object, which is a competitive event"@en ;
    skos:broadMatch adlnet:completed ;
    xapi:closelyRelatedNaturalLanguageTerm <http://wordnet-rdf.princeton.edu/wn31/200661447-v> .

# when we're talking about 'completed' for a race, 'finished' might be a good display
adlnet:completed xapi:thirdPartyLabel "finished"@en .

:medaled
    a xapi:Verb ;
    skos:inScheme : ;
    skos:inScheme myvocab20: ;
    skos:prefLabel "medaled"@en ;
    skos:definition "To receive a medal for achievement in a competitive event"@en ;
    skos:broader :placed .
```