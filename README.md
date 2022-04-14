# Options for Schema Structure

This has been based on [Adobe's XDM schema organization](https://github.com/adobe/xdm/tree/master/components). I would like to work on how we want to organize and name our classes/scenario level objects and add a concept of field groups to our schema.

We all agree on having the concept of `shared` schemas, in this example stored at `schema/shared`. Inside that directory we have abstract schema definitions, meaning these definitions cannot be used directly. Data producers would create a new scenario based on one of these classes, in this example `add-to-cart`.

## [Organization](/Organization.md)

## [Inheritance](/Inheritance.md)