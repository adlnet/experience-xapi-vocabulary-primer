## Example xAPI Vocabulary Dataset (JSON-LD Version) {#example-xapi-vocabulary-dataset-json-ld-version}

Some parts of the JSON-LD document, such as those properties using SKOS, are intended for use by semantic web aware processors, while other parts are for general consumption. Except for a few keys being prefixed by “@”, it should look like you might expect a JSON document to look to describe an xAPI vocabulary and associated verbs, even knowing nothing of JSON-LD.


```
{
  "@context": {
  "http://xapi.vocab.pub/vocabulary/context.jsonld",
  "@id": "http://myvocab.example.com/xapi/",
  "@type": "ConceptScheme",
  "versions": [
    {
      "@id": "http://myvocab.example.com/xapi/2.0/",
      "wasRevisionOf": "http://myvocab.example.com/xapi/1.0/"
    },
    {
      "@id": "http://myvocab.example.com/xapi/1.0/"
    }
  ],
  "wasGeneratedBy": {
    "name": {
      "en": "Sports and Competition xAPI Vocabulary Working Group"
    }
  },
  "verbs": [
    {
      "@id": "http://myvocab.example.com/xapi/qualifiedfor",
      "@type": "Verb",
      "skos:inScheme": {
        "@id": "http://myvocab.example.com/xapi/2.0/"
      },
      "prefLabel": {
        "en": "qualified for"
      },
      "definition": {
        "en": "To be accepted as a participant for the Activity object by meeting some set of criteria"
      }
    },
    {
      "@id": "http://myvocab.example.com/xapi/placed",
      "@type": "Verb",
      "skos:inScheme": {
        "@id": "http://myvocab.example.com/xapi/2.0/"
      },
      "prefLabel": {
        "en": "placed"
      },
      "altLabel": {
        "en": "ranked"
      },
      "definition": {
        "en": "To achieve a ranked outcome in the Activity object, which is a competitive event"
      },
      "broadMatch": [
        "http://www.adlnet.gov/expapi/verbs/completed"
      ],
      "closelyRelatedNaturalLanguageTerm": "http://wordnet-rdf.princeton.edu/wn31/200661447-v"
    },
    {
      "@id": "http://myvocab.example.com/xapi/medaled",
      "@type": "Verb",
      "skos:inScheme": {
        "@id": "http://myvocab.example.com/xapi/2.0/"
      },
      "prefLabel": {
        "en": "medaled"
      },
      "definition": {
        "en": "To receive a medal for achievement in a competitive event"
      },
      "broader": [
        "http://myvocab.example.com/xapi/placed"
      ]
    }
  ]
}```
