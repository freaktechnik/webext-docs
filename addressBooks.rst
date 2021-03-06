============
addressBooks
============

The address books API, also including the :doc:`contacts` and :doc:`mailingLists` namespaces, first appeared in Thunderbird 64.

.. note::

  The permission ``addressBooks`` is required to use ``addressBooks``.

Types
=====

.. _addressBooks.NodeType:

NodeType
--------

Indicates the type of a Node, which can be one of ``addressBook``, ``contact``, or ``mailingList``.

.. _addressBooks.AddressBookNode:

AddressBookNode
---------------

A node representing an address book.

- ``id`` (string) The unique identifier for the node. IDs are unique within the current profile, and they remain valid even after the program is restarted.
- ``name`` (string)
- ``type`` (:ref:`addressBooks.NodeType`) Always set to ``addressBook``.
- [``contacts``] (array) A list of contacts held by this node's address book or mailing list.
- [``mailingLists``] (array) A list of mailingLists in this node's address book.
- [``parentId``] (string) The ``id`` of the parent object.
- [``readOnly``] (boolean) Indicates if the object is read-only. Currently this returns false in all cases, as read-only address books are ignored by the API.

Functions
=========

openUI()
--------

Opens the address book user interface.

closeUI()
---------

Closes the address book user interface.

list([complete])
----------------

Gets a list of the user's address books, optionally including all contacts and mailing lists.

- [``complete``] (boolean) If set to true, results will include contacts and mailing lists for each address book.

get(id, [complete])
-------------------

Gets a single address book, optionally including all contacts and mailing lists.

- ``id`` (string)
- [``complete``] (boolean) If set to true, results will include contacts and mailing lists for this address book.

create(properties)
------------------

Creates a new, empty address book.

- ``properties`` (object)

  - ``name`` (string)

update(id, properties)
----------------------

Renames an address book.

- ``id`` (string)
- ``properties`` (object)

  - ``name`` (string)

delete(id)
----------

Removes an address book, and all associated contacts and mailing lists.

- ``id`` (string)

Events
======

onCreated(node)
---------------

Fired when an address book is created.

- ``node`` (:ref:`addressBooks.AddressBookNode`)

onUpdated(node)
---------------

Fired when an address book is renamed.

- ``node`` (:ref:`addressBooks.AddressBookNode`)

onDeleted(id)
-------------

Fired when an addressBook is deleted.

- ``id`` (string)
