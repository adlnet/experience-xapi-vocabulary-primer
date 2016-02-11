## Properties for vocabulary provenance metadata {#properties-for-vocabulary-provenance-metadata}

**prov:specializationOf** comes into play to relate revisions of the same vocabulary. The specific revision of the vocabulary is **prov:specializationOf** for the overarching vocabulary.

**prov:wasGeneratedBy** connects specific revisions to the ‘provenance activity’ (a **prov:Activity**, unrelated to an xAPI Activity) that generated them. That provenance activity will often be a working group or community of practice, and in those cases it should have at least a **foaf:name**.

**prov:wasRevisionOf** connects new revisions of the vocabulary to the old revision they’re based on.