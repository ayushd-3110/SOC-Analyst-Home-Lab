# Impact Detection

## Process-Based Search

```spl
index=main EventCode=4688
| where like(lower(Process_Command_Line),"%file%i.txt%")
    OR like(lower(Process_Command_Line),"%ransomware%")
    OR like(lower(Process_Command_Line),"%locked%")
| table _time host Account_Name New_Process_Name Creator_Process_Name Process_Command_Line
| sort _time
```

## Investigation Note

The exact fields available depend on the Windows logging configuration. If a query returns no data, inspect the raw Event 4688 record and adjust the field names or search terms.

## Interpretation

The `.locked` files in this project are harmless simulation artifacts. Their presence does not mean that real ransomware encryption occurred.
