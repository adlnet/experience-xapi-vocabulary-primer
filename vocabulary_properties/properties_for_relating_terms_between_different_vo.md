## Properties for relating terms between different vocabularies {#properties-for-relating-terms-between-different-vocabularies}

**skos:broadMatch** is just like **skos:broader** (in fact, it is a sub property) but is intended for use between different vocabularies, and as such is appropriate for use by anyone, which applies to all the ‘Match’ properties.

**skos:closeMatch** relates a term in a vocabulary to a term in another vocabulary that means very nearly the same thing. While it will be worth considering using the other term directly, it is usually more reasonable to create a new term with the precise meaning desired, then relate it using **skos:closeMatch** to the other vocabulary’s term.

**skos:exactMatch** makes a bold claim: two concepts are so close that they might reasonably be considered identical. It should only be used after careful consideration. If creating a term for the first time and you discover another term in another vocabulary that would be an exact match, use the other term instead. Only if two vocabularies independently arrived at a term that was nigh identical should **skos:exactMatch** be used. Basically, try very hard not to use this.

**skos:narrowMatch** is the inverse of **skos:broadMatch**.

**skos:relatedMatch** is like **skos:related**, but for between different vocabularies. Since two separate vocabularies having ambiguously related terms is normal, it should see use a lot more often than skos:related.