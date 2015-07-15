# SQL Data Types

PostgreSQL supports a wide array of data types, some specific to Postgres and some conforming to the SQL standard. The number of data types “out of the box” numbers over 50, but it is also possible to define custom data types.

#### Numeric Types

Note that the serial types are Postgres-specific implementations of a common, but non-standardized type.

| Name                      | Size     | Description                 | Range                       |
|---------------------------|----------|-----------------------------|-----------------------------|
| smallint                  | 2 bytes  | small integer               | -32768 to + 32767           |
| integer                   | 4 bytes  | typical integer             | ~ +/-2147483648             |
| bigint                    | 8 bytes  | large integer               | ~ +/-9223372036854775808    |
| decimal / numeric / float | variable | custom precision,exact      | custom                      |
| real                      | 4 bytes  | variable precision, inexact | 6 decimal places precision  |
| double precision          | 8 bytes  | variable precision, inexact | 15 decimal places precision |
| serial                    | 4 bytes  | auto-incrementing integer   | 1 to 2147483647             |
| bigserial                 | 8 bytes  | auto-incrementing integer   | 1 to 9223372036854775807    |

#### Monetary Types

Currency type is determined by the database's lc_monetary setting. Note this is not a SQL standard type.

| Name    | Size     | Description     | Range                                          |
|---------|----------|-----------------|------------------------------------------------|
| money   | 8 bytes  | currency amount | -92233720368547758.08 to +92233720368547758.07 |

#### Character Types

Note that char and varchar are SQL standard types and text is not.

| Name        | Size                       | Description                | Range                    |
|-------------|----------------------------|----------------------------|--------------------------|
| varchar(n)  | varying up to n characters | variable length with limit | -32768 to + 32767        |
| char(n)     | varying up to n characters | fixed length               | ~ +/-2147483648          |
| text        | varying, unlimited         | large integer              | ~ +/-9223372036854775808 |

#### Binary Types

This is Postgres' equivalent to the SQL standard BLOB or Binary Large Object.

| Name   | Size                                    | Description                   |
|--------|-----------------------------------------|-------------------------------|
| bytea  | 1-4 bytes plus the actual binary string | variable length binary string |

#### Date/Time Types

All types are SQL standards.

| Name                    | Size     | Description    | Low            | High          |
|-------------------------|----------|----------------|----------------|---------------|
| timestamp w/ time zone  | 8 bytes  | date and time  | 4713 BC        | 294276 AD     |
| timestamp w/o time zone | 8 bytes  | date and time  | 4713 BC        | 294276 AD     |
| date                    | 4 bytes  | date (no time) | 4713 BC        | 5874897 AD    |
| time w/o time zone      | 8 bytes  | time (no date) | 00:00:00       | 24:00:00      |
| time w/ time zone       | 12 bytes | time (no date) | 00:00:00+1459  | 24:00:00-1459 |
| interval                | 16 bytes | time interval  | -178000000 yrs | 178000000 yrs |

#### Boolean Types

The SQL standard.

| Name     | Size   | Description   |
|----------|--------|---------------|
| boolean  | 1 byte | true or false |

#### Enumerated Type

The ENUM type needs to be created using the CREATE TYPE command, and is used to store a static, ordered set of values. It is not a SQL standard, but is a common type among RDBMS's.

#### Geometric Types

Not SQL standard types, but most are common among RDBMS's supporting spatial types.

| Name   | Size         | Description  | Representation                        |
|--------|--------------|--------------|---------------------------------------|
| point  | 16 bytes     | x,y          | Point on a plane                      |
| line   | 32 bytes     | (x,y),(x,y)  | Infinite line (not fully implemented) |
| lseg   | 32 bytes     | (x,y),(x,y)  | Finite line segment                   |
| box    | 32 bytes     | (x,y),(x,y)  | Rectangular box                       |
| path   | 16+16n bytes | (x,y)...     | Closed path (like polygon)            |
| path   | 16+16n bytes | (x,y)...     | Open path                             |
| polygon| 49+16n bytes | (x,y)...     | Polygon (similar to closed path)      |
| circle | 24 bytes     | (x,y),radius | Circle                                |

#### Network Address Types

Non-standard types for storing IPv4, UPv6, and MAC addresses.

| Name    | Size          | Description                      |
|---------|---------------|----------------------------------|
| cidr    | 7 or 19 bytes | IPv4 and IPv6 networks           |
| inet    | 7 or 19 bytes | IPv4 and IPv6 networks and hosts |
| macaddr | 6 bytes       | MAC addresses                    |

#### Bit String Types

Non-standard types for storing string of 1's and 0's for bit masks.

#### Text Search Types

Non-standard types for full text search.

#### UUID Type

The uuid type is a non-standard type for storing Universally Unique Identifiers.

#### XML Type

The xml data type is a non-standard type for storing XML data. Unlike the text type, it has built-in abilities for testing the well-formedness and type-safing of the XML.

#### JSON Type

The json data type is a non-standard type for storing JSON data. Unlike the text type, it has built-in abilities for checking if the content is valid JSON.

#### Array Type

Arrays can be made from table columns, custom types, ENUMs, or composite types. They are of variable length. Syntax compliant with the SQL standard can be used.

#### Composite Type

The composite type is a custom type representing the structure of a record with its associated internal data types. A non-standard type.

#### Range Types

Discrete or continuous ranges associated with a sub-type. These are not SQL standard types.

| Name      | Description                           |
|-----------|---------------------------------------|
| int4range | Range of integers                     |
| int8range | Range of bigints                      |
| numrange  | Range of numerics                     |
| tsrange   | Range of timestamps without time zone |
| tstzrange | Range of timestamps with time zone    |
| daterange | Range of date                         |

#### Object Identifier Type

The oid type is a non-standard type for storing Object Identifiers.

#### Pseudo Types

A set of non-standard types that are not used for column data types, but can be used to declare a function's argument or result type.






