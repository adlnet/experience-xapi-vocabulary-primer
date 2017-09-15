# NOTE: THIS SPEC HAS BEEN SUPERSEDED BY THE [xAPI PROFILE SPECIFICATION](https://github.com/adlnet/xapi-profiles).

# VISIT: [https://github.com/adlnet/xapi-profiles](https://github.com/adlnet/xapi-profiles)

# THIS REPO IS AVAILABLE FOR ARCHIVAL PURPOSES ONLY.

#  {#how-to-read-this-document}

# How to Read this Document {#how-to-read-this-document}

This Primer is an introductory document designed to complement the [Companion Specification for xAPI Vocabularies](https://adl.gitbooks.io/companion-specification-for-xapi-vocabularies/content/) by providing the reader with additional knowledge and examples. It is more precise about how to use the terms than the Companion Specification. It also covers some introductory real-world examples of what can be immediately achieved by publishing xAPI vocabularies as Linked Data \(LD\). The reader is presented with a descriptive narrative of classes and properties that are most commonly used for representing [xAPI vocabularies as linked datasets](https://adl.gitbooks.io/companion-specification-for-xapi-vocabularies/content/xapi_vocabularies_as_linked_datasets.html).

## Formatting

Properties and classes are **bolded**.

Code examples are in  `red text or have a light gray background`.

Vocabularies and vocabulary term identifiers are all `red bold italicized`_** **_when described in this document’s text.

Internal hyperlinks are [blue text](#) and external links are [_**bold blue italicized**_](#).

Several examples will be also provided with code snippets contained inside of a gray box like the one below. Most of the examples in this document are initially written using the [_**Turtle syntax for RDF**_](https://www.w3.org/TR/turtle/). Turtle is used here for improved readability as it allows RDF to be completely written in a compact and simplified natural text form. Examples serialized as Turtle and JSON-LD will appear throughout this document as sample code contained inside the gray box such as the following:

```
#Turtle example
@prefix ex: <http://www.example.com/>.

ex:aResource ex:aProperty ex:anotherResource;
  ex:anotherProperty "An RDF Literal"@en.
```

Each resource is described as RDF triples as discussed in the [Companion Specification for xAPI Vocabularies](https://adl.gitbooks.io/companion-specification-for-xapi-vocabularies/content/semantic_web_technology,_linked_data,_and_rdf/rdf_data_structure.html). A simplified example of using Turtle for the xAPI Verb ‘satisfied’ with a basic label and description would be written as:

```
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix xapi: <https://w3id.org/xapi/ontology#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://w3id.org/xapi/adl/verbs/satisfied> a xapi:Verb ;
    skos:prefLabel "satisfied"@en ;
    skos:definition "Indicates that the Authority or application determined the Actor has fulfilled the criteria of the Activity."@en .
```

Some examples in this primer will also be provided as JSON-LD. The above Turtle serialization is equivalent to the following example, in JSON-LD syntax:

```
{
  "@context": {
    "rdf": "http://www.w3.org/1999/02/22-rdf-syntax-ns#",
    "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
    "skos": "http://www.w3.org/2004/02/skos/core#",
    "xapi": "https://w3id.org/xapi/ontology#",
    "xsd": "http://www.w3.org/2001/XMLSchema#"
  },
  "@id": "https://w3id.org/xapi/adl/verbs/satisfied",
  "@type": "xapi:Verb",
  "skos:prefLabel": {
    "@language": "en",
    "@value": "satisfied"
  },
  "skos:definition": {
    "@language": "en",
    "@value": "Indicates that the Authority or application determined the Actor has fulfilled the criteria of the Activity."
  }
}
```



