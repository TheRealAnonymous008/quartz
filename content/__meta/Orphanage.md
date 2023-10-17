
```dataview 
TABLE without id
out AS "Non-existent files" FLATTEN file.outlinks as out WHERE !(out.file) AND !contains(meta(out).path, "/") 
GROUP by out SORT out ASC
```
