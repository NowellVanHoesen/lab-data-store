# The Basics of a Data Store

This document defines the basic attributes and functionality of the data store

## External Functionality

This is the interface of how to interact with the data store:

- Put an item (by store key) into the store: `set`, `put`, `store`, or `add`
    - returns `true` if item stored, else returns `false`
    - avoids overwriting or replacing an existing item
    - check if key exists
        - if `false`, stored the item and returns `true`
        - if `true`, does not store the item and returns `false`
- Get a copy of the item (by store key) out of the store: `get`
    - Return a copy of the item
    - but the item remains in the store
- Check if item exists in the store: `exists` or `has`
    - Give it a key to check
    - returns `true` if exists; else `false`
- Remove a specific item from the store `remove`
    - get the item and return it
    - delete the item and its key from the store
- Replace a specific item (by store key) in the store: `replace`
    - if the item exists, replace and return `true`
    - if the item does not exist, add(insert) the item and return `true` 
- Merge the given array with the specified item array `merge`
    - check if specified item exists in the store, return `false` if not
    - restricted to arrays only
        - check if the given is_array and existing item is also array
        - if either is not array, return `false`
    - use native built-in PHP function to deeply merge the arrays together, return `true`
- empty all items currently stored in the store `empty`
    - Caution: deletes all items in the store
    - handy in the tests suite, i.e. clean up after each test
    - releases memory for performance and optimization

## Internal Functionality and Attributes

- Has a container - holds the items that have been stored.
- Retain the items in the container ( so the items can be accessed later ).
- Data agnostic, any kind of data can be stored.
- Identify each item in the container/store.
- Held in memory

### Item Identifier

Attributes:

- Unique
- Bound to one item
- Readable and understandable
- Items are discoverable


Naming convention for our identifiers:

[item_type].[subtype].[name_or_slug]

- item type: examples: config, object ( post, query ), user info
- subtype: examples: post_type, tax, shortcode, template, query
- name_or_slug: examples: name of the CPT, Tax, shortcode name, etc.

Examples:
- Theme Settings: `config.theme.settings`
- Lab CPT: `config.post_type.lab`
- Docx CPT: `config.post_type.docx`
- Glossary CPT: `config.post_type.glossary`
- Help CPT: `config.post_type.help`
- Catalog Tax: `config.tax.catalog`
- Skills Tax: `config.tax.skills`

### Container

The container will have the following attributes:
- It's a container - holds the items that have been stored.
- Data agnostic, any kind of data can be stored.
- Identify (key) each item in the container/store.
- Held in memory
- Retain the items in the container ( so the items can be accessed later ).

It will use the [PHP Array Data Type](https://knowthecode.io/docx/php/array).

The container could be:
- ~~JSON file~~
- ~~database~~
- ~~in-memory cache~~
- in-memory using a PHP array data type
 
 Ways to retain the items in the container:
 - Procedural: `static $container = [];`
 - Static Class: property: `static $container = [];` (visibility `private`)
 - OOP: property: `private $container = [];`
 