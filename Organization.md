# Organization

```
/shared
	/classes
		add-to-cart.class.json
	/fieldgroups
		product.fieldgroup.json
/banner
	/classes
		complete-flow.class.json
	/fieldgroups
		product.fieldgroup.json
	add-to-cart.json
```

In the above structure, all data producer schema libraries will have access to the `shared` directory. Any schema that inherits from anything in the shared directory (will always use latest | have the option to use any existing version of the schema). This depends on if we want to force update or let people update as they wish.

## Classes

The schema in `/shared/classes` will be our base scenario definitions, essentially abstract classes that cannot be instantiated or built on their own. In order for a data producer to use them, they will have to create an implementation of that class, seen in `/banner/add-to-cart.json`. Scenarios will be made up of one class, and 0 or more field groups.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.class.json` suffix to each of these files.

## Field Groups

The schema in `/shared/fieldgroups` are similar to the ones in `/shared/classes` but they do not mean anything on their own. For example, you cannot have a scenario definition based on the `product` field group. You can have an `add-to-cart` definition that uses the a field group derived from the shared `product` field group.

To make it more obvious you are editing a class instead of a scenario, I have added the `*.fieldgroup.json` suffix to each of these files.

Field groups are more flexible in how we handle them, but they should still be treated as abstract definitions, unable to instantiated without first inheriting from them. Using this pattern we set up data producers with the ability to modify their field group implementation from the start.

## Custom Classes and Field Groups

We also have the possibility of allowing data producers to create their own custom, reusable classes and field groups that are not accessible to other schema libraries. These would still inherit from the shared definitions, but allow data producers to consistently customize them across their library. These are stored in the `/banner/fieldgroups/` and `/banner/classes/` directories.

The custom classes and field groups have a similar naming scheme to the shared ones, but custom field groups can be instantiated as objects. They still cannot be scenarios by themselves, but can be added as fields or objects to scenarios.
