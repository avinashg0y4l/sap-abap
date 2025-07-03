cast 
string_operation

## Aggregate Functions

| Function                  | Description                        |
|---------------------------|------------------------------------|
| `MIN(operand)`            | Returns the minimum value          |
| `MAX(operand)`            | Returns the maximum value          |
| `SUM(operand)`            | Returns the sum of values          |
| `AVG(operand)`            | Returns the average value          |
| `COUNT(*)`                | Counts all rows                    |
| `COUNT(DISTINCT operand)` | Counts distinct values of operand  |




## Annotation System Fields Mapping

| Value for Annotation `systemField` | Related ABAP System Field |
|------------------------------------|--------------------------|
| `#client`                         | `sy-mandt`               |
| `#SYSTEM_DATE`                    | `sy-datum`               |
| `#SYSTEM_TIME`                    | `sy-uzeit`               |
| `#SYSTEM_LANGUAGE`                | `sy-langu`               |
| `#USER`                           | `sy-uname`               |
| `#USER_DATE`                      | `sy-datlo`               |
| `#USER_TIMEZONE`                  | `sy-zonlo`               |
s

## Session Variable Mapping

| Session Variable                | Related ABAP System Field |
|---------------------------------|--------------------------|
| `$sesuib.clint`                 | `sy-mandt`               |
| `$sesuib.system_date`           | `sy-datum`               |
| `$sesuib.system_language`       | `sy-langu`               |
| `$sesuib.user`                  | `sy-uname`               |
| `$sesuib.user_date`             | `sy-datlo`               |
| `$sesuib.user_timezone`         | `sy-zonlo`               |




inner join
left innner join
right inner join
Outer join
left outer join
Right outer join

Association in CDS View
    it is special kindf of join

    Program On :    join conditition using association
