# The Basics of the API

This document defines tje basic functionality of the data store API

The API serves as a public, globally accessibility interface with the data store. Using the API, the developer does not need to know the data store implementation or how to interact with it directly.

## Public-Facing Functionality

This is the interface of how to interact with the data store API. It provides functions for each of the data store public methods, These include:

- Add item
- Get item
- Has item - does an item exist
- Replace item
- Remove item
- Merge item
- Empty store

### Naming Convention

[verb]_item(s)_[preposition]_data_store()

- `add_item_to_data_store()`
- `get_item_from_data_store()`
- `item_exists_in_data_store()`
- `remove_item_from_data_store()`
- `replace_item_in_data_store()`
- `merge_with_item_in_data_store()`
- `empty_data_store()`

## Attributes

- globally accessible - plugins or themes can interact with the data store
- control how to interact with the items and/or the store itself
- the data store and its implementation are handled within the API, but abstracted from the developer
