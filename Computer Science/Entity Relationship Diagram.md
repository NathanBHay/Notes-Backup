An entity relationship diagram, or ERD is a diagram used to visualise the content of a [[Databases|relational database]]. There are multiple notations for a ERD diagram, these being:
- **Chen** notations was the original form which uses diamonds with a label to represent relations.
- **Crow's Foot** notation which uses double dashed lines to represent one, and crows feet to represent many.
- **[[Object Orientated Programming#UML Class Diagrams|UML]]** notation uses the same notation as classes.

# Crows Foot
Crows foot is a notation which uses entities in the form of a grid with a key, and its entities. As well as lines to represent relationships. These lines have a symbol at either end to represent whether it is zero or many, one or many, one or one, and zero or one. The many being represented by crows feet, the one being represented by a dashed line, and zero being a circle. Put together these three symbols make the previous cases. Furthermore a label is usually required as to designate how it functions.

There are a few key rules that need to be followed, these are:
- Entities must not be pluralised
- Key attributes must be indicated by the word key in the first column of the entity shape, while attributes should be on the second column.
- Attributes are bolded if not optional
- Attribute must no include spaces or hyphens.
- Attributes need a common prefix.
- Relationship lines must include a label.
- Minimum and maximum cardinality must be shown at the end of each relationship.
- All relationship lines must correctly indicate if the relationship is identifying (a solid line) or non-identifying (dashed line).
- Relationship lines can't be crossed
