## Direct Requests on Vocabulary Dataset IRIs {#direct-requests-on-vocabulary-dataset-iris}

One of the most common ways people or applications can obtain more meaning is by directly targeting the vocabulary dataset IRI. This method is useful for applications that might require immediate need to access to a whole vocabulary dataset, meaning of a single term, or the relationships among terms in vocabulary. Let's assume that you are building an authoring tool/application and want to find out all of the published ADL vocabulary. You already know that you can directly view these in a browser at the vocabulary IRI**_._ **For example, the overall ADL Vocabulary is available here: **_https://w3id.org/xapi/adl_**. But if you wanted to retrieve a machine-readable representation of the vocabulary dataset for your application and update the displays of this information on a regular basis you could simply issue a HTTP request. The example below a sample request using the CURL command line tool. The request is for the ADL vocabulary in JSON.

```curl --header "Accept: application/json" -L https://w3id.org/xapi/adl```

Alternatively, you could use JavaScript to test that JSON is returned using an HTTP request in a browser developer console such as Firefox or Chrome:

```
<!doctype html>
<html>
  <head>
    <script src="http://code.jquery.com/jquery-1.4.2.min.js"></script>
    <script type="text/javascript">
      $(document).ready(function() {
        $.ajax({
          url: 'https://w3id.org/xapi/cmi5',
          type: 'GET',
          dataType: 'json',
          beforeSend: setHeader		  
        });
      });

      function setHeader(xhr) {
		xhr.addEventListener('load', function (ev) {console.log(ev);console.log(xhr.response);console.log(xhr.responseText);});
        xhr.setRequestHeader('Accept', 'application/json');
      }
    </script>
  </head>
  <body>
    <h1>Load this page with the browser developer console open and view the network / xhr requests.</h1>
  </body>
</html>
```

It is expected that more vocabularies will be made available as Communities of Practice publishe them. In the meantime, direct GET requests on vocabulary IRIs can be attempted on any of the following vocabularies:

*   ADL Vocabulary: **_```https://w3id.org/xapi/adl```_**
*   IEEE ADB Vocabulary: **_```https://w3id.org/xapi/adb```_**
*   Across X Vocabulary: **_```https://w3id.org/xapi/acrossx```_**
*   Serious Games Vocabulary: **_```https://w3id.org/xapi/seriousgames```_**
*   Video Vocabulary: **_```https://w3id.org/xapi/video```_**
*   SCORM Vocabulary: **_```https://w3id.org/xapi/scorm```_**
*   cmi5 Vocabulary: **_```https://w3id.org/xapi/cmi5```_**

In addition, valuable information and meaning can be further retrieved from each vocabulary term. The vocabulary datasets use SKOS to express relationships between terms and the vocabulary they belong to (the concept scheme). However, the vocabulary datasets also provide text labels in other languages, descriptions, and links to other sources such as Wordnet for word sense disambiguation. In fact, if you take advantage of “following your nose” to look up other linked data sources, then you will find that each verb should have a link to a wordnet synset. In the previous examples a vocabulary dataset IRI was requested and JSON-LD was returned. The IRI **_```http://wordnet-rdf.princeton.edu/wn31/200485097-v```_** is provided as the **_xapi:closelyRelatedNaturalLanguageTerm_ **for ADL’s “completed” Verb. A subsequent HTTP request on this IRI returns even more useful data, including multiple language translations and other synset members such as the equivalent word “finished,” **_```http://wordnet-rdf.princeton.edu/wn31/finish-v```_**.

```curl --header "Accept: application/ld+json" -L http://wordnet-rdf.princeton.edu/wn31/200485097-v```