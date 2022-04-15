
Allow creation of an ERD of some sort?
Can we steal the idea of 'classes', 'field groups', and 'data types'?

# [Composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en)

## Class

Composing a schema begins by assigning a class. Classes define the behavioral aspects of the data the schema will contain (record or time-series). In addition to this, classes describe the smallest number of common properties that all schemas based on that class would need to include and provide a way for multiple compatible datasets to be merged.

## Field group

A field group is a reusable component that defines one or more fields that implement certain functions such as personal details, hotel preferences, or address. Field groups are intended to be included as part of a schema that implements a compatible class.

Field groups define which class(es) they are compatible with based on the behavior of the data they represent (record or time series). This means that not all field groups are available for use with all classes.

Remember that schemas are composed of “zero or more” field groups, so this means that you could compose a valid schema without using any field groups at all.

## Data type

Data types are used as reference field types in classes or schemas in the same way as basic literal fields. The key difference is that data types can define multiple sub-fields. Similar to a field group, a data type allows for the consistent use of a multi-field structure, but has more flexibility than a field group because a data type can be included anywhere in a schema by adding it as the “data type” of a field.

Experience Platform provides a number of common data types as part of the Schema Registry to support the use of standard patterns for describing common data structures. This is explained in more detail in the Schema Registry tutorials, where it will become clearer as you walk through the steps to define data types.

The following screenshot demonstrates how data types are represented in the Platform UI. One of the fields provided by the Demographic Details field group uses the “Person name” data type, as indicated by the text following the pipe character (|) next to the field’s name. This particular data type provides several subfields that relate to the name of an individual person, a construct that can be reused for other fields where a person’s name needs to be captured.

[Probably disallow the creation of custom objects, ie force teams to add new fields on the top level of the predefined class/field group.](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en#objects-v-freeform)

[Adobe differentiates between Events and Profiles and Lookup entities](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/best-practices.html?lang=en)


[Stealing the UI for some concepts](https://experienceleague.adobe.com/docs/experience-platform/xdm/tutorials/create-schema-ui.html?lang=en)

[We should start thinking about identity and an identity service of some sort](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=en)

[How do we track performance degradation when reporting on data? What causes that?](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

[Data Behaviors](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html?lang=en#data-behaviors)
It seems we really focus on events, with events having the associated profile information in them. I think adobe terms this as 'time-series'. We tend to have 'record' and 'ad-hoc' data with the 'time-series' data. I'm not sure this is important or relevant to us.

[Field groups are also limited to certain classes.](https://github.com/adobe/xdm/tree/master/components/fieldgroups)

# [Data modeling best practices](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/best-practices.html?lang=en#sort-entities-into-profile%2C-lookup%2C-and-event-categories)

## Profile entities	

Profile entities represent attributes relating to an individual person, typically a customer. Entities that fall under this category should be represented by schemas based on the XDM Individual Profile class.

## Lookup entities	

Lookup entities represent concepts that can relate to an individual person, but cannot be directly used to identify the individual. Entities that fall under this category should be represented by schemas based on custom classes.

Kroger wants to limit the amount of custom classes in use.

## Event entities	

Event entities represent concepts related to actions a customer can take, system events, or any other concept where you may want to track changes over time. Entities that fall under this category should be represented by schemas based on the XDM ExperienceEvent class.

Should we split out profile information into separate schema? What advantages or disadvantages does that have over what we do now?

# [ERD](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/best-practices.html?lang=en#create-a-high-level-erd)

Would making an ERD be valuable?

Can we leverage an ERD as a requirements form in some way?

Ask for things like what they want to measure, data they want to capture, how it relates to their existing entities/models/objects?