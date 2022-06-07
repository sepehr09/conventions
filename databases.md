## General Guidance

- Keep names as short as possible.

- Names should be full English words.

- Avoid abbreviating names - tables, fields, views, procedures, and other database objects - unless it's a known name
  in the domain. e.g. **do not** use `cap_id` instead of `customer_address_phone_id`

- Use underscore for delimiting words.

## Database

- Database names must only consist of the letters `a` to `z`, and the underscore `_` symbol. It's not allowed to use
  non-ASCII database names.

- Database names should start with letters.

- Database names should be unique across databases. In case of any conflict make a pragmatic choice.

- Database should have use meaningful name. If there is a business term exists, then that name should be used.

- Use a charset and a collation that meet the requirement of the project.

## Tables/Views/Relational

- Use `InnoDB` engine unless you are sure the table is not the case of ACID transactions.

- Avoid using descriptive prefixes such as `tb_` or `vw_`.

- Avoid adding `application name` prefixes to your database objects. e.g. `app_name_user`.

- Where possible use a meaningful word for a relational table. e.g. use `services` instead of `car_mechanic`.
  If not possible, concatenate table names together in alphabetical order.
  e.g. `customer_employee`, `post_user`, `author_post`.

## Columns / Fields

- All tables must have a primary key field named `id` - even if you use `UUID` field, unless a database doesn't let to
  change the index name.

- Choose short names (better no-longer than two words separated by `_`), and up to 30 characters.

- A field should have a name that corresponds to the way that plain language refers to the property such as
  `first_name`, `amount` or `measure`.

- All fields should have descriptive comment explaining the exact purpose of that field in English.

- Avoid applying the collective name to the property. e.g. `employee_name` field in an `employee` table.

- Avoid using field names that are just the name of data types such as text or timestamp. e.g. `timestamp`, `text`

- Avoid adding data type abbreviation as suffix to field names. e.g. `description_tx`, `created_at_dt`.

- Avoid using column with same name as table name and vice versa.

- Avoid using reserved words as field names. Check for [reserved words](https://mariadb.com/kb/en/reserved-words/).

- Avoid quoted identifiers. If you must use them then stick to SQL-92 double quotes for portability.

## Keys

- **Primary**: Single column primary key fields should be named `id`.

- **Foreign**: Foreign key fields should be a combination of the name of the referenced table and the name of the
  referenced fields. e.g. `person_id`. + In case of having more than one foreign key, you should use a meaningful name, followed by the name of reference
  table and end in `_id`. e.g. `creator_person_id`, `publisher_user_id`.

## Indexes:

All type of constraints and indexes should be explicitly named. Never allow the database to put in the constraint
names automatically.

- **Primary Key index:** table name concatenated with `_pk`. e.g. `person_pk`, `user_pk`

- **Foreign key index:** start with table name, plus foreign key fields, and end in `_fk`. e.g. `person_address_id_fk`.

- **Unique indexes:** start with table name and all the indexed fields, and end in `_uk` for a unique index.
  e.g. `person_ssn_uk`.

- **Normal indexes:** start with table name and all the indexed fields, and end in `_ik` for regular one.
  e.g. `person_first_name_ik`.

## Aliases

The algorithm to alias a table name:

- If the name does not contain an underscore, take the _four first letters_, e.g `customer` becomes `cust`.

- If the name contains one underscore, take the _first two letters of each word_, e.g. `post_user` becomes `pous`

- If the name contains two underscores, take the _first two letters of the first word_, and the _first letter of the other
  words_, e.g. `comment_post_user` becomes `copu`.

- If the name contains three or more underscores, take the _first letter of each word_, e.g `comment_like_post_user`
  becomes `clpu`.

- If a new alias causes a conflict with the existing ones, make a pragmatic choice.

## Stored procedures / Triggers

Stored procedures, are not logically tied to any table or column. Typically though, stored procedures perform one or
more common database activities (Read, Insert, Update, and/or Delete) on a table, or another action of some kind.

- Avoid prefixing with `sp_` or any other such a descriptive prefix or Hungarian notation.

- The name must contain a verb. e.g. `find_nearest_store`

- The name must be explanatory of what stored procedure is doing. e.g. `find_stores_near_zip_code`

## Data Types

- Only use `REAL` or `FLOAT` types where it is strictly necessary for floating-point mathematics otherwise
  prefer `NUMERIC` and `DECIMAL` at all times. Floating point rounding errors are a nuisance.

- Use `tinyint(1)` for all boolean fields.

- Use `varchar(191)` for all textual fields that need to have an index on it.

## Field Naming

- All `id` fields should be `unsigned integer`. The size will depend on the numeracy of the table.

- All `foreign key` fields should have the exact data type they have in their own table.

- All `timestamp` fields, better to be a one word name and should end with `_at`. e.g. `created_at`, `published_at`.

- All `boolean` fields, better to be a one word name and start with `is_`, `has_`, `can_`, or `should_` based on
  its meaning. e.g. `is_published`, `has_discount`, `can_register`, `should_change_password`.

- Any foreign key fields should follow the foreign key indexing naming mentioned above.

- All tables must have these three timestamp fields: `created_at`, `updated_at`, `deleted_at`. These fields should be
  updated automatically on record's `creation`, `updating`, and `deletion`.

- If you are going to use `json` data type make sure, that you are not routinely query that field as extracting data
  from `json` columns can greatly degrade a query’s performance.

- Avoid making up terms when it's possible use these instead, to provide a common terminology set. e.g. `start`, `stop`.
  Always use these instead of `begin/end`, `start/finish`, or any other similar words or combinations.

- If you are naming fields with time meaning use `start` and `end` for that. e.g. `start_at`, `end_at`.

## Variables

- [MySQL](https://dev.mysql.com/doc/refman/8.0/en/user-variables.html)
- [MariaDB](https://mariadb.com/kb/en/user-defined-variables/)
- [PostgresSQL](https://www.postgresql.org/docs/current/plpgsql-declarations.html)

## Sources

- [SQL Style Guide](https://www.sqlstyle.guide/)
- [The Power of a Good SQL Naming Convention](https://www.xaprb.com/blog/2008/10/26/the-power-of-a-good-sql-naming-convention/)
- [Six Tips For Avoiding Bad Table and Column Names](https://www.bobpusateri.com/archive/2010/07/six-tips-for-picking-bad-table-and-column-names/)
- [10 Database Naming Conventions Best Practices](https://brandongaille.com/10-database-naming-conventions-best-practices/)
- [10 Rules for a Better SQL Schema](https://www.sisense.com/blog/better-sql-schema/)
- [MYSQL Naming Conventions](https://medium.com/@centizennationwide/mysql-naming-conventions-e3a6f6219efe)
- [Laravel](https://laravel.com/docs/7.x/eloquent-relationships)
- [SQL Server Standards](https://www.isbe.net/Documents/SQL_server_standards.pdf)
- [Oracle Naming Conventions](https://oracle-base.com/articles/misc/naming-conventions)
- [Database Schema Naming Convention - DSNC](https://github.com/ghowland/Dasonic)
- [Tips on naming boolean variables - Cleaner Code](https://dev.to/michi/tips-on-naming-boolean-variables-cleaner-code-35ig)
- [SQL Server Table and Column Naming Conventions](https://www.codeproject.com/Articles/1065295/SQL-Server-Table-and-Column-Naming-Conventions)
- [Leszynski Naming Convention](https://en.wikipedia.org/wiki/Leszynski_naming_convention)
