# Organization

```
/shared
	/classes
		add-to-cart.class.json
	/datatypes
		product.datatype.json
/banner
	/classes
		complete-flow.class.json
	/datatypes
		product.datatype.json
	add-to-cart.json
	complete-flow-cashback.json
	complete-flow-fuel.json
```

In the above structure, all data producer schema libraries will have access to the `shared` directory. The `shared` directory contains only abstract schema. Any schema that inherits from anything in the shared directory (will always use latest | have the option to use any existing version of the schema). This depends on if we want to force update or let people update as they wish.

## Classes

The schema in `/shared/classes` will be our base scenario definitions, essentially abstract classes that cannot be instantiated or built on their own. In order for a data producer to use them, they will have to create an implementation of that class, seen in `/banner/add-to-cart.json`. Scenarios will be made up of one class, and 0 or more field groups.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.class.json` suffix to each of these files.


## Data Types

The schema in `/shared/datatypes` are similar to the ones in `/shared/classes` but they are not valid schema on their own. For example, you cannot have a scenario definition based on the `product` data type. You can have an `add-to-cart` definition that uses the a data type derived from the shared `product` data type.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.fieldgroup.json` suffix to each of these files.

Data types are more flexible in how we handle them, but they should still be treated as abstract definitions, unable to instantiated without first inheriting from them. Using this pattern we set up data producers with the ability to modify their data type implementation from the start.

## Field Groups

Field groups are fields that can be applied consistently across multiple schema, such as data classification, or delivery service information.

## Custom Classes, Data Types, and Field Groups

We also have the possibility of allowing data producers to create their own custom, reusable classes, data types, and field groups that are not accessible to other schema libraries. These would still inherit from the shared definitions, but allow data producers to consistently customize them across their library. These are stored in the `/banner/classes/`, `/banner/datatypes/`, and `/banner/fieldgroups/` directories.

The custom classes, data types, and field groups have a similar naming scheme to the shared ones. They still cannot be scenarios by themselves, but can be added as fields or objects to scenarios.

## Limiting Field Groups