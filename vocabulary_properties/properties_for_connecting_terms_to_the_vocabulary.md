## Properties for connecting terms to the vocabulary: {#properties-for-connecting-terms-to-the-vocabulary}

**skos:inScheme** connects an **xapi:Verb** or other xAPI term maintained as part of a vocabulary (**xapi:ActivityType**) to the **skos:ConceptScheme** that is the xAPI vocabulary it is part of. Make each Verb **skos:inScheme** of at least one concept scheme (the overarching vocabulary), plus any new versions of the vocabulary with new revisions.

**xapi:referencedBy** connects an **xapi:Verb** or other xAPI term not directly maintained by the vocabulary author to the **skos:ConceptScheme** that is the xAPI vocabulary referencing the term. Generally speaking, no properties should be provided for referenced Verbs or Activity Types other than **xapi:thirdPartyLabel**, **xapi:referencedBy**, or **skos:scopeNote**. This property (**xapi:referencedBy**) is a sub property of **skos:inScheme**.