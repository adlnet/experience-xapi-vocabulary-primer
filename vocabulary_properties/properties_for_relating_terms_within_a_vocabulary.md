## Properties for relating terms within a vocabulary {#properties-for-relating-terms-within-a-vocabulary}

**skos:broader** goes from the more specific term to the more general. B skos:broader C means that C’s definition encompasses B’s definition. It is for use inside / within a vocabulary. For example, the IEEE ADB  Vocabulary (***```https://w3id.org/xapi/adb```***) has a verb (highlighted) that is more specific than another verb in the vocabulary (annotated). The **skos:broader** property would be here to here show this relationship. For example:

_< ***```https://w3id.org/xapi/adb/verbs/highlighted```***> skos:broader < ***```https://w3id.org/xapi/adb/verbs/annotated```***>_.

**skos:narrower** is the inverse of **skos:broader**. This property is also intended for use inside vocabularies.For example:

_< ***```https://w3id.org/xapi/adb/verbs/annotated```***> skos:narrower < ***```https://w3id.org/xapi/adb/verbs/highlighted```***>_.

**skos:related** leaves very ambiguous the nature of the relationship, but does assert there’s some conceptual connection between the two terms it connects. Since it is only for use inside vocabularies, it probably should not be used very often (if a vocabulary is well structured, it usually won’t include terms that only have ambiguous relationships to each other). This, narrower, and broader should only be used by the vocabulary author.