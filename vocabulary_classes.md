# Vocabulary Classes {#vocabulary-classes}

Most of the classes used for describing xAPI vocabularies come from the Simple Knowledge Organization System (SKOS). Read the [Companion Specification for xAPI Vocabularies](https://docs.google.com/document/d/1SmyEu5qxTdun-BVNoznhbInKXZ5xLKYp_49qyXa0Lqc/edit?pref=2&pli=1#heading=h.l32x5uyzhn84) for more details on the intentional alignment with SKOS. This section will briefly describe all of the classes used for xAPI vocabularies.

**skos:ConceptScheme** is the class for collections, lists, and other similar types of a controlled vocabulary. In the xAPI sense, it will generally be used for various collections of verbs or activity types, particularly represented as vocabularies.

**xapi:ActivityType** is the class used for xAPI Activity Types. It is a ‘subclass’ of **skos:Concept**.

**xapi:Verb** is the class for xAPI Verbs. It is a ‘subclass’ of **skos:Concept**.

**prov:Activity** is a class used in connection with vocabulary provenance properties.