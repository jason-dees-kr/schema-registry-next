
## Profile entities	

Profile entities represent attributes relating to an individual person, typically a customer. Entities that fall under this category should be represented by schemas based on the XDM Individual Profile class.

## Lookup entities	

Lookup entities represent concepts that can relate to an individual person, but cannot be directly used to identify the individual. Entities that fall under this category should be represented by schemas based on custom classes.

Kroger wants to limit the amount of custom classes in use.


## Event entities	

Event entities represent concepts related to actions a customer can take, system events, or any other concept where you may want to track changes over time. Entities that fall under this category should be represented by schemas based on the XDM ExperienceEvent class.

https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/best-practices.html?lang=en#sort-entities-into-profile%2C-lookup%2C-and-event-categories