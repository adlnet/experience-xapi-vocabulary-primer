## SPARQL Queries Made Possible {#sparql-queries-made-possible}

Back to why we’re doing all of this: for what it makes possible. There isn’t just one thing, but a key component is the ability to answer those first example questions provided in the introduction of this document. Here are some ways SPARQL could be used to do that. While not exactly self explanatory, these should be clear enough to see how the use of the terms above make such retrievals easy (and easy to hide behind a web application with good user experience). Federated semantic queries will also be an option in the future, but at the time of this publication only the ADL vocabulary server is currently supporting RDF in xAPI implementations.

The following example SPARQL queries assumes the reader has some knowledge of SQL-like queries and access to a public SPARQL endpoint. For these examples, the xAPI vocabulary server has provided a public SPARQL endpoint, **_http://xapi.vocab.pub/sparql_**.

1.**Has anyone published a translation of any existing xAPI verbs from other vocabulary authors in Simplified Chinese (or any other language)?**

```
PREFIX xapi: <https://w3id.org/xapi/ontology#>

select distinct ?verb ?thirdPartyLabel

where {
   ?verb a xapi:Verb .
  ?verb xapi:thirdPartyLabel ?thirdPartyLabel .
  FILTER(langMatches(lang(?thirdPartyLabel), "zh-tw"))
}```

Using the above SPARQL query at the endpoint provided (**_http://xapi.vocab.pub/sparql_**) will return the following [results](http://xapi.vocab.pub:8890/sparql?default-graph-uri=&query=PREFIX+xapi%3A+%3Chttps%3A%2F%2Fw3id.org%2Fxapi%2Fontology%23%3E%0D%0A%0D%0Aselect+distinct+%3Fverb+%3FthirdPartyLabel%0D%0A%0D%0Awhere+%7B%0D%0A++%3Fverb+xapi%3AthirdPartyLabel+%3FthirdPartyLabel+.%0D%0A++FILTER%28langMatches%28lang%28%3FthirdPartyLabel%29%2C+%22zh-tw%22%29%29%0D%0A%7D%0D%0AORDER+BY+%3Fverb&should-sponge=&format=text%2Fhtml&timeout=0&debug=on):

| **verb** | **thirdPartyLabel** |
| --- | --- |
| [```http://adlnet.gov/expapi/verbs/answered```](http://adlnet.gov/expapi/verbs/answered) | "回答"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/asked```](http://adlnet.gov/expapi/verbs/asked) | "提問"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/attempted```](http://adlnet.gov/expapi/verbs/attempted) | "開始嘗試"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/commented```](http://adlnet.gov/expapi/verbs/commented) | "回應"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/completed```](http://adlnet.gov/expapi/verbs/completed) | "完成"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/interacted```](http://adlnet.gov/expapi/verbs/interacted) | "互動"@zh-tw |
| [```http://adlnet.gov/expapi/verbs/shared```](http://adlnet.gov/expapi/verbs/shared) | "分享"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/bookmarked```](https://w3id.org/xapi/adb/verbs/bookmarked) | "加書籤"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/highlighted```](https://w3id.org/xapi/adb/verbs/highlighted) | "畫重點"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/noted```](https://w3id.org/xapi/adb/verbs/noted) | "做筆記"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/read```](https://w3id.org/xapi/adb/verbs/read) | "閱讀"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/referenced```](https://w3id.org/xapi/adb/verbs/referenced) | "查詢參考"@zh-tw |
| [```https://w3id.org/xapi/adb/verbs/requested```](https://w3id.org/xapi/adb/verbs/requested) | "求助"@zh-tw |
| [```https://w3id.org/xapi/adl/verbs/logged-in```](https://w3id.org/xapi/adl/verbs/logged-in) | "登入"@zh-tw |

Chinese (Simplified (zh-cn) and Traditional (zh-tw)) and English (en) translations have been provided at the time of this publication. It is expected that more will follow with the adoption of these vocabulary practices. In the future, you could easily substitute the “zh-tw” country-locale code for any other to match your inquiry. **Note:** The xAPI Chinese Community of Practice published translations of pre-existing xAPI verbs that they used as part of their vocabulary dataset at the IRI, **_```https://w3id.org/xapi/acrossx```_**. They used the **xapi:thirdPartyLabel** property for translating xAPI verbs from other authors and they used **skos:prefLabel** for translating any original vocabulary terms.

For example, to see only the original verbs that were translated in Simplified Chinese we would simply use the following query:

```
PREFIX xapi: <https://w3id.org/xapi/ontology#>

select distinct ?verb ?label

where {
  ?verb a xapi:Verb .
  ?verb skos:prefLabel ?label .
  FILTER(langMatches(lang(?label), "zh-cn"))
}
```

2.**How many other published xAPI vocabularies are reusing/referencing an existing Verb?**

```
# return all of the verbs that are referenced by other vocabularies, and show the label, description, scope note, and third party labels

PREFIX xapi: <https://w3id.org/xapi/ontology#>

select distinct ?verb ?label ?description ?vocab ?note ?thirdPartyLabel

where {
{ ?verb a xapi:Verb .
  ?verb skos:prefLabel ?label .
  ?verb skos:definition ?description . }

{ GRAPH
 ?graph { ?verb xapi:referencedBy ?vocab .
       OPTIONAL { ?verb skos:scopeNote ?note }
       OPTIONAL { ?verb xapi:thirdPartyLabel ?thirdPartyLabel }
       }
   }
}
ORDER BY ?verb```

Below is a SPARQL Query to locate which Activity Types are reused/referenced by other vocabularies. The below query will show the English label and description, the vocabulary referencing the Activity Type, scope note, and thirdPartyLabel. Paste the following query into the [***http://xapi.vocab.pub/sparql***](http://xapi.vocab.pub/sparql) endpoint or [***click here***](http://xapi.vocab.pub:8890/sparql?default-graph-uri=&query=PREFIX+xapi%3A+%3Chttps%3A%2F%2Fw3id.org%2Fxapi%2Fontology%23%3E%0D%0A%0D%0Aselect+distinct+%3Factivity+%3Flabel+%3Fdescription+%3Fvocab+%3Fnote+%3FthirdPartyLabel%0D%0A%0D%0Awhere+%7B%0D%0A%7B+%3Factivity+a+xapi%3AActivityType+.%0D%0A++%3Factivity+skos%3AprefLabel+%3Flabel+.%0D%0A++%3Factivity+skos%3Adefinition+%3Fdescription+.%7D%0D%0A%0D%0A%7B+GRAPH%0D%0A+%3Fgraph+%7B+%3Factivity+xapi%3AreferencedBy+%3Fvocab+.%0D%0A+++++++OPTIONAL+%7B+%3Factivity+skos%3AscopeNote+%3Fnote+%7D%0D%0A+++++++OPTIONAL+%7B+%3Factivity+xapi%3AthirdPartyLabel+%3FthirdPartyLabel+%7D%0D%0A+++++++%7D%0D%0A+++%7D%0D%0A%7D%0D%0AORDER+BY+%3Factivity&should-sponge=&format=text%2Fhtml&timeout=0&debug=on) for the results.

```
PREFIX xapi: <https://w3id.org/xapi/ontology#>

select distinct ?activity ?label ?description ?vocab ?note ?thirdPartyLabel

where {
{ ?activity a xapi:ActivityType .
  ?activity skos:prefLabel ?label .
  ?activity skos:definition ?description .}

{ GRAPH
 ?graph { ?activity xapi:referencedBy ?vocab .
       OPTIONAL { ?activity skos:scopeNote ?note }
       OPTIONAL { ?activity xapi:thirdPartyLabel ?thirdPartyLabel }
       }
   }
}
ORDER BY ?activity```

The previous two examples show all of the results of terms that are referenced by other vocabularies. If you wanted to be more specific and narrow down the results to a specific verb (e.g., ADL’s “completed” verb), you could perform the query below. Use the **_http://xapi.vocab.pub/sparql_ **endpoint or [***click here***](http://xapi.vocab.pub:8890/sparql?default-graph-uri=&query=PREFIX+adl%3A+%3Chttp%3A%2F%2Fadlnet.gov%2Fexpapi%2Fverbs%2F%3E%0D%0APREFIX+xapi%3A+%3Chttps%3A%2F%2Fw3id.org%2Fxapi%2Fontology%23%3E%0D%0A%0D%0Aselect+distinct+%3Flabel+%3Fdescription+%3Fsynset+%3Fvocab+%3Fnote+%3FthirdPartyLabel%0D%0A%0D%0Awhere+%7B%0D%0A++%7B%0D%0A++++adl%3Acompleted+skos%3AprefLabel+%3Flabel+.%0D%0A++++adl%3Acompleted+skos%3Adefinition+%3Fdescription+.%0D%0A++++adl%3Acompleted+xapi%3AcloselyRelatedNaturalLanguageTerm+%3Fsynset+.%0D%0A++%7D%0D%0A%7B%0D%0AGRAPH+%3Fgraph+%7B%0D%0A++++adl%3Acompleted+xapi%3AreferencedBy+%3Fvocab+.%0D%0A++++OPTIONAL+%7B+adl%3Acompleted+skos%3AscopeNote+%3Fnote+%7D%0D%0A++++OPTIONAL+%7B+adl%3Acompleted+xapi%3AthirdPartyLabel+%3FthirdPartyLabel+%7D%0D%0A++++%7D%0D%0A++%7D%0D%0A%7D&should-sponge=&format=text%2Fhtml&timeout=0&debug=on) for the results. This example query also displays other properties such as **xapi:closelyRelatedNaturalLanuageTerm**.

```
PREFIX adl: <http://adlnet.gov/expapi/verbs/>
PREFIX xapi: <https://w3id.org/xapi/ontology#>

select distinct ?label ?description ?synset ?vocab ?note ?thirdPartyLabel

where {
  {
    adl:completed skos:prefLabel ?label .
    adl:completed skos:definition ?description .
    adl:completed xapi:closelyRelatedNaturalLanguageTerm ?synset .
  }
{
GRAPH ?graph {
    adl:completed xapi:referencedBy ?vocab .
    OPTIONAL { adl:completed skos:scopeNote ?note }
    OPTIONAL { adl:completed xapi:thirdPartyLabel ?thirdPartyLabel }
    }
  }
}```

3.**What verbs are more specialized forms of other verbs?**

```
PREFIX xapi: <https://w3id.org/xapi/ontology#>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>

SELECT distinct ?verb ?verbLabel ?verbDescription ?broaderVerb ?broaderLabel ?broaderDescription

 WHERE { {
    ?verb a xapi:Verb .
    ?verb skos:prefLabel ?verbLabel .
    ?verb skos:definition ?verbDescription .
    ?verb skos:broader ?broaderVerb }
{
GRAPH ?graph {
  OPTIONAL { ?broaderVerb skos:prefLabel ?broaderLabel }
  OPTIONAL { ?broaderVerb skos:definition ?broaderDescription }
  }
 }
}```

**Note:** There might be limited results in the above example as at the time of this writing only the IEEE ADB Verb vocabulary had applied any form of semantic relationship mapping between terms both inside and outside of the ADB vocabulary. It is expected that vocabulary tools and refined publishing processes will help make this practice more practical and widespread in the near future.