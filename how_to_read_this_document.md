# How to Read this Document {#how-to-read-this-document}

This Primer is an introductory document designed to complement the [Companion Specification for xAPI Vocabularies](https://docs.google.com/document/d/1SmyEu5qxTdun-BVNoznhbInKXZ5xLKYp_49qyXa0Lqc/edit?pref=2&pli=1#) by providing the reader with additional knowledge and examples. It is more precise about how to use the terms than the Companion Specification. It also covers some introductory real-world examples of what can be immediately achieved by publishing xAPI vocabularies as Linked Data (LD).

The reader is presented with a descriptive narrative of classes and properties that are most commonly used for representing [xAPI vocabularies as linked datasets](https://docs.google.com/document/d/1SmyEu5qxTdun-BVNoznhbInKXZ5xLKYp_49qyXa0Lqc/edit?pref=2&pli=1#heading=h.xwvqwzalhk0t). Vocabulary and vocabulary term IRIs are all **_bold italicized_ **when described in paragraph text of this document. Classes and properties are **bolded**. Several examples will be also provided with code snippets contained inside of a gray box like the one below. Most of the examples in this document are initially written using the [Turtle syntax for RDF](https://www.w3.org/TR/turtle/). Turtle is used here for improved readability as it allows RDF to be completely written in a compact and simplified natural text form. Examples serialized as Turtle and JSON-LD will appear throughout this document as sample code contained inside the gray box such as the following:

| #Turtle example |
| --- |

Each resource is described as RDF triples as discussed in the [Companion Specification for xAPI Vocabularies](https://docs.google.com/document/d/1SmyEu5qxTdun-BVNoznhbInKXZ5xLKYp_49qyXa0Lqc/edit?pref=2&pli=1#heading=h.altocwinmbth). A simplified example of using Turtle for the xAPI Verb ‘satisfied’ with a basic label and description would be written as:

| @prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> . |
| --- |

Some examples in this primer will also be provided as JSON-LD. The above Turtle serialization is equivalent to the following example, in JSON-LD syntax:

| { |
| --- |