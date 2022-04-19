# Organization

## Versionless directory structure

```
/shared
	/classes
		/add-to-cart
			add-to-cart.class.json
		/complete-flow
			complete-flow.class.json
	/datatypes
		/product
			product.datatype.json
		/search 
			search.datatype.json
	/fieldgroups
		/data-classification
			data-classification.fieldgroup.json
/banner
	/classes
		/complete-flow
			complete-flow.class.json
	/datatypes
		/product
			product.datatype.json
		/search
			search.datatype.json
	/fieldgroups
		/fuel-information
			fuel-information.fieldgroup.json
	/scenarios
		/add-to-cart
			add-to-cart.json
		/complete-flow-cashback
			complete-flow-cashback.json
		/complete-flow-fuel
			complete-flow-fuel.json
```

In the above versionless structure, all data producer schema libraries will have access to the `shared` directory. The `shared` directory contains only abstract schema. Any schema that inherits from anything in the shared directory (will always use latest | have the option to use any existing version of the schema). This depends on if we want to force update or let people update as they wish.

## Classes

The schema in `/shared/classes` will be our base scenario definitions, essentially abstract classes that cannot be instantiated or built on their own. In order for a data producer to use them, they will have to create an implementation of that class, seen in `/banner/add-to-cart.json`. Scenarios will be made up of one class, and 0 or more field groups.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.class.json` suffix to each of these files.

Classes can also exist inside schema libraries and they will still be abstract.

## Data Types

The schema in `/shared/datatypes` are similar to the ones in `/shared/classes` but they are not valid schema on their own. For example, you cannot have a scenario definition based on the `product` data type. You can have an `add-to-cart` definition that uses the a data type derived from the shared `product` data type.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.fieldgroup.json` suffix to each of these files.

Data types are more flexible in how we handle them. Using this pattern we set up data producers with the ability to modify their data type implementation from the start.

## Field Groups

Field groups are fields that can be applied consistently across multiple schema, such as data classification, or delivery service information. These are also abstract schema and should be treated as such, even field groups inside a schema library. 

Adobe also limits field groups to schema that implement specific classes.

## Custom Classes, Data Types, and Field Groups

We also have the possibility of allowing data producers to create their own custom, reusable classes, data types, and field groups that are not accessible to other schema libraries. These would still inherit from the shared definitions, but allow data producers to consistently customize them across their library. These are stored in the `/banner/classes/`, `/banner/datatypes/`, and `/banner/fieldgroups/` directories.

The custom classes, data types, and field groups have a similar naming scheme to the shared ones. The classes and field groups are still abstract; data types can be use inside scenarios, field groups, or other data types.


## Versioned

```
/dist
	/shared
		/classes
			/add-to-cart
				/1.0.0
					add-to-cart.class.json
				/latest
					add-to-cart.class.json
				CHANGELOG.md
			/complete-flow
				/1.0.0
					complete-flow.class.json
				/latest
					complete-flow.class.json
				CHANGELOG.md
		/datatypes
			/product
				/1.0.0
					product.datatype.json
				/latest
					product.datatype.json
				CHANGELOG.md
			/search 
				/1.0.0
					search.datatype.json
				/latest
					search.datatype.json
				CHANGELOG.md
		/fieldgroups
			/data-classification
				/1.0.0
					data-classification.fieldgroup.json
				/latest
					data-classification.fieldgroup.json
				CHANGELOG.md
	/banner
		/classes
			/complete-flow
				/1.0.0
					complete-flow.class.json
				/latest
					complete-flow.class.json
				CHANGELOG.md
		/datatypes
			/product
				/1.0.0
					product.datatype.json
				/latest
					product.datatype.json
				CHANGELOG.md
			/search
				/1.0.0
					search.datatype.json
				/latest
					search.datatype.json
				CHANGELOG.md
		/fieldgroups
			/fuel-information
				/1.0.0
					fuel-information.fieldgroup.json
				/latest
					fuel-information.fieldgroup.json
				CHANGELOG.md
		/scenarios
			/add-to-cart
				/1.0.0
					add-to-cart.json
				/latest
					add-to-cart.json
				CHANGELOG.md
			/complete-flow-cashback
				/1.0.0
					complete-flow-cashback.json
				/latest
					complete-flow-cashback.json
				CHANGELOG.md
			/complete-flow-fuel
				/1.0.0
					complete-flow-fuel.json
				/latest
					complete-flow-fuel.json
				CHANGELOG.md
```

We might be able to come up with a better versioning scheme and take advantage of git tags and releases? It would be easier to have a `dist` directory like this for Scenario Poet so we can easily grab all previous versions. 

* How can we construct a versioning system like this for Scenario Poet without having a dist folder? From github releases somehow?
* To reduce complexity does it make sense to have 1 github schema registry repo per schema library? ie one repo for Banner, one repo for Demeter, one repo for VitaCost? How do we do the shared schemas at that point? One shared repo that can be referenced by the others?