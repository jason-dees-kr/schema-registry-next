# Glossary

## Abstract

In our instance, it is an adjective attached to various types of schema, making that schema a partial schema with the intent of reusing that schema across the various schema libraries for consistency. An abstract schema will not result in a valid object, and needs to be implemented by a schema library in a scenario or a data type.

## Class

The base, abstract schema definition for a scenario. A scenario implements 1 class. A class has the smallest number of fields to have a valid scenario. Classes cannot be instantiated on their own since they are partial schema; this makes them abstract.

Adapted from Adobe's idea of [composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en).

## Data Producer

The people, teams, or organizations that use scenarios to produce data for reporting purposes.

## Data Type

A reusable component of fields that represent an object, like product and search information. Data types will be used as field in a scenario, field group, or other data type. Scenarios cannot implement a data type, but they can use a data type as a field. Scenarios cannot inherit or implement a data type.

Adapted from Adobe's idea of [composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en).

## Field

The most basic building block of a schema. It is a property on a schema that data producers fill in with data from their application for reporting purposes.

Adapted from Adobe's idea of [composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en).

## Field Group

An abstract, reusable component of one or more fields that are grouped based on use and context, such as fuel information and data classification. Scenarios, data types, and other field groups will implement a field group. Scenarios, custom classes, data types, and other field groups can implement a field group.

Adapted from Adobe's idea of [composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en).

## Implement

An idea stolen from Object Oriented Programming that is used in constructing schema, very similar to inheritance, but used only in the context of classes. A scenario represents an actual instance of a class, an implementation of a class. These can be viewed as interfaces/protocols, meaning the child schema has at least the fields defined in the parent.

A parent schema can only be a shared schema (class, field group, or data type), or a custom abstract class from a data producer's schema library. A child schema can both implement and inherit from an abstract schema. A child schema cannot implement an existing valid object schema; that valid object already has a valid implementation: itself.

## Inherit

An idea stolen from Object Oriented Programming that is used in constructing schema. To inherit a schema (the parent) means that the resulting schema (the child) contains the data structure as the parent. The child schema can add more fields and requirements, potentially overwriting poritions of the parent's schema, such as accepted values for fields that the parent has. 

A parent schema can be a valid scenario, or an abstract class, field group, or data type. A schema can inherit from one or more schema. Due to our rules, we can set certain limitations on this, like scenarios can only inherit from one other scenario or class.

## Scenario

The generic name for a full analytics object. This is the base object for measuring analytics. A scenario is implements 1 class, implements 0 or more field groups, with 0 or more data types as fields. A scenario can inherit another scenario as well.

## Schema

A model used to represent a class, a scenario, a field group, or a data type. Schema in our use case always means JSON schema, which is a standardized way of representing objects in the JSON format.

## Valid Object

An object that can be instantiated inside a data producer's application. This is only scenarios and data types from a data producer's schema library.