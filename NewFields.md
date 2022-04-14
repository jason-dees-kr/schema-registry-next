# New Fields

For when our data producers can modify schema in our hypothetical web-based schema editor, we should not allow users to add fields to schema that have not been approved by BDA in some way. This is for naming consistency, data type consistency, and catching misuse of scenarios.

It can be assumed that fields from classes and field groups will have been pre-approved. Adobe has a way to restrict what field groups go with what classes. We may want to introduce something like this so we don't get product information on `start-navigate` and they use `view-product` instead.

If a user decides that no field groups match their needs, they can submit a change to add a new field to a schema. BDA will then be able to approve, change, or deny the request. We can also recommend a list of pre-approved fields that other data producers currently use that are not in our schema. This almost precludes that we have some way to track when a field is custom via JSON Schema.