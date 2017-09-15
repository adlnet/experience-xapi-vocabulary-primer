# NOTE: THIS SPEC HAS BEEN SUPERSEDED BY THE [xAPI PROFILE SPECIFICATION](https://github.com/adlnet/xapi-profiles).

# VISIT: [https://github.com/adlnet/xapi-profiles](https://github.com/adlnet/xapi-profiles)

# THIS REPO IS AVAILABLE FOR ARCHIVAL PURPOSES ONLY.

#  {#introduction-and-motivations}

# Introduction and Motivations {#introduction-and-motivations}

In the core [_**Experience API \(xAPI\) Specification**_](https://github.com/adlnet/xAPI-Spec), there are a lot of things identified by using an [_**Internationalized Resource Identifier**_](https://en.wikipedia.org/wiki/Internationalized_resource_identifier) \(IRI\). When the core xAPI specification was written it was envisioned that the IRIs used for identifiers in xAPI statements could eventually map directly to vocabulary IRIs for more semantic meaning. Most IRIs will be URLs, just like you commonly see in web browsers. Using IRIs for identifiers gives many advantages, such as clear rules that prevent people from trampling on each other’s identifiers, having a place to go to find out more built in, and interoperability with other standards that use IRIs.

One of those standards is called the [_**Resource Description Framework**_](https://en.wikipedia.org/wiki/Resource_Description_Framework) \(RDF\), and it’s part of the Semantic Web. A basic introduction to RDF is provided in the [Companion Specification for xAPI Vocabularies](https://adl.gitbooks.io/companion-specification-for-xapi-vocabularies/content). The Semantic Web is a loose collection of standards and practices, including for querying stores of data, for exchanging data in a multitude of formats, for creating ontologies — descriptions of how patterns relate to other patterns, so that you can infer new meanings. All of these capabilities are built on top of or meant to work heavily with RDF.

This means it is very useful to have ways to talk about parts of xAPI that are identified by IRIs in RDF. By doing so, many powerful tools for working with RDF, such as specialized databases, automatic inference engines, and code libraries in virtually every programming language that have built up over many years can be brought to bear. What’s more, many of the things we might want to say in the xAPI community, such as that one verb is a more specific form of another, can be expressed using existing schemas and ontologies based on RDF.

For example, some of the types of questions that will be not just possible, but rather easy for us to answer:

1. Has anyone published a translation of any existing xAPI verbs in Simplified Chinese \(or any other language\)?
2. How many published xAPI vocabularies are reusing a particular Verb or Activity Type?
3. What verbs are more specialized forms of a verb, in any vocabulary?

The main downside of RDF has historically been that working with it in programs requires importing quite a bit of complexity. Luckily, another standard provides a highly effective bridge between the higher complexity world of RDF and the simplicity of JSON \(the same format xAPI Statements are written in\): JSON-Linked Data \(JSON-LD\). People wanting to generate descriptions of xAPI verbs, activity types, and so forth can initially work with simple HTML/RDFa representations, and anyone wanting to deliver additional value can transform HTML/RDFa representations into JSON-LD.

