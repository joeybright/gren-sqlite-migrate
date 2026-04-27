# gren-sqlite-migrate

Apply SQL migrations to a SQLite database in Gren.

## How it works

This package takes a series of SQL statements (migrations) that are to be applied to a database in a specific order and ensures they are applied as safely as possible.

The internals of this package accomplish this by using a hash chain which represent the history of applied migrations to the database. For more information on hash chains, check out [this Wikipedia article](https://en.wikipedia.org/wiki/Hash_chain).

Hash chains give us a few beneficial properties:

- Each migration will only ever be applied once to the database.
- Migrations will always be applied in the same order.
- Any SQL in a given migration set cannot be changed after applied to the database.

The main tradeoff for all of these benefits is strictness. Once migrations are applied, altering the database with this package is difficult. You cannot easily undo or change applied migrations given that corrupts the entire hash chain. This can make certain scenarios difficult compared to other migration frameworks / packages in other languages.

## When to use it

This package is best suited for greenfield projects maintained by a single developer.

It is not yet a good fit for collaborating on migrations with other people, or for environments where multiple migrations might be applied at once. Those scenarios can produce conflicts this package hasn't been designed to handle yet.
