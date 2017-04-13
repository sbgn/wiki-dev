Several proposals were presented by Mirit Aladjem, Stuart Moodie and Michael Blinov. The proposals were divided into "subdivision", where an entity glyph is made-up of several adjacent domains, and "enclosure", where an entity glyph contains the domains.

The subdivision approach implies the existence of a particular domain, representing the whole protein. After discussing examples, it was recognized that a correct interpretation of such an entity would require pre-existing knowledge, and relied on arbitrary requirements difficult to implement (specific location of the generic domain, different fonts etc.).

The subdivision approach also precludes nesting of domains.

While a consensus emerged on the use of enclosure, there was discussion on the respective positions of domains and their relationships.

### Agreements

#### Representation of domains

Domains of an Entity are represented by Entities located within the parent Entity. Several levels of enclosures can be represented, with domains, subdomains etc.

#### Auxiliary units

The state variables and units of information located on an enclosing Entity are relevant to the whole entity, either because the information affects all domains, or because one does not know which domain is affected.

The assignment of on an enclosing entity affects all the enclosed entities:

-   The assignment of a location on an enclosing entity modifies the location of all the enclosed entities. Example: Transport of a protein from the cytosol to the nucleus.

<!-- -->

-   The assignment of an existence on an enclosing entity modifies the existence of all the enclosed entities. Example: Degradation of a protein.

An assignment on an enclosed entity overrides an assignment on the enclosing entity:

-   The assignment of a location on an enclosed entity modifies the location of this entity, and only this one, leaving the sibling entities unaffected. Example: insertion of a transmembrane segment.

<!-- -->

-   The assignment of an existence on an enclosed entity modifies the existence of this entity, and only this one, leaving the sibling entities unaffected. Example: cleavage of a domain.

### To be clarified

Topology of domains within and enclosing entity: No topology? Alignment? Adjacency?

Location of state-variable values affecting a domain: Within the enclosing entity or outside, with assignment crossing the entity boundary?