# Options for Kroger Data Model (KDM) 

This has been based on [Adobe's XDM schema organization](https://github.com/adobe/xdm/tree/master/components). I would like to work on how we want to organize and name our classes/scenario level objects and add a concept of field groups to our schema.

Adobe also has the concept of 'data types' that might better represent our non-scenario models, like products.

We all agree on having the concept of `shared` schemas, in this example stored at `schema/shared`. Inside that directory we have abstract schema definitions, meaning these definitions cannot be used directly. Data producers would create a new scenario based on one of these classes, in this example `add-to-cart`.

Another goal is to organize, and categorize, schema in such a way as to help users understand what a certain analytics definition is supposed to be used for. We can use this as an educational tool as much as a capability tool.

## [Glossary (WIP)](/Glossary.md)

## [Inheritance](/Inheritance.md)

## [New Fields](/NewFields.md)

## [Organization](/Organization.md)