# Inheritance

## Reducing Model Complexity

In banner models in particular, we have a lot of optional fields that apply at specific times and places. With an inhertance model we can create multiple scenario definitions that are essentially the same scenario, but with certain fields always mandatory, with all the scenarios inheriting from the same base definition.

For example, in banner, `add-to-cart` has two id fields, `bagId` and `basketId`, that are both optional. We can change this by creating an [`add-to-bag`](/schema/banner/add-to-bag.json) scenario that inherits from the shared `add-to-cart` class that has the `bagId` field required and lacks the `basketId` field completely. 

This enables our models to be more strict in what we allow without the complicated rules around conditionally optional fields.

If we allow data producers to create custom classes, we can enable this property sharing among all their scenarios that would inherit from their own custom class.

## Issues With Child References

Ideally an `add-to-cart` class would contain `product` information already. If we include the `product` field group reference directly in the `add-to-cart` class, data producers would not able to modify the `product` field group at all. The `schema/shared/classes/add-to-cart.class.json` file has the `product` field group included and `schema/vitacost/add-to-cart.json` inherits from that class definition. Vitacost can no longer edit the `product` field group to meet their product-specific needs.

To fix this, we can create an `add-to-cart` class definition without the `product` field group included, and specify somehow in the schema that when a data producer adds `add-to-cart` to their library it adds a `product` reference. There are a few ways this can be done as well.

### The Standard, Classic Way

```json    
"product": {
	"$ref": "/shared/fieldgroups/product/$VERSION"
},
````

This declares a product property that uses `$ref` like how we currently do it. There is one major downside to this in that it would be more difficult to extend this object by adding fields. 

### A New Way I Just Thought Of

```json    
"product": {
	"$id": "/banner/add-to-cart/product",
	"description": "Captures product data related to an add to cart event",
	"properties": {
	},
	"allOf": [
		{
			"$ref": "/shared/fieldgroups/product/$VERSION"
		}
	]
},
````

This uses our more standard extension pattern we use for normal schema definitions. We can also create custom objects this way and this allows us to add properties. These new internal definitions are not (will not?) shared across scenarios.

### Just Create a Custom Field Group

We can also automatically create a custom field group based the referenced field group and add it automatically to the new definition based on the class. This would allow the data producers to add fields ot the product definition and treat it as a shareable field group.

#### Reference in the scenario

```json    
"product": {
	"$ref": "/banner/fieldgroups/product/$VERSION"
},
````

#### Shareable Field Group Definition

```json
{
	"$id": "/banner/fieldgroups/product/$VERSION",
	"description": "Captures product data related to an add to cart event",
	"properties": {
	},
	"allOf": [
		{
			"$ref": "/shared/fieldgroups/product/$VERSION"
		}
	]
}
```

This gets us the advantage of sharing the definition across multiple scenarios. But if the data producers need a differnt version of a product, they will have to create a new field group with a different name. Conceptually this makes sense to developers, but we should not cater to developers.