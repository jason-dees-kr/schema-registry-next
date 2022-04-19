# Path Forward to Enable this

1. Update Schema Registry (SR) to support arbitrary amounts of directories deep for schema definitions.
	* Right now it expects `schemas/[library name]/[some directory name]/[schema name]/[schema name].json`
	* It needs to support `schemas/**/[schema name]/*.json`
1. Migrate a single scenario to this pattern in a SR branch. Schema library does not matter.
	 * We need to decide how references work with importing schema for field groups and data types. Do we let them reference `shared` directly from their scenarios or do we make them 'import' the reference to their schema library?
1. Use the SR branch to make sure SR works properly for versioning
1. Use the SR branch to update Scenario Poet (SP) to support importing schema from the `shared` schema library
1. Use the SR branch to update Schema Service (SS) to support importing schema refernces from the `shared` schema library
1. Create a method for disabling auto updates on schema libraries using shared schemas.
1. Update SP to support versions of schema other than latest, ie arbitrary, valid versions of schema references