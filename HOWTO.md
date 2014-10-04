---
title: How to add a new IP to ipindx
---


IP records in ipindx are recorded in CSON format (CoffeeScript Object Notation).

# Description of files

## reasons.cson

This contains a key of reasons/categories to avoid having to write out varying reasons which cannot be machine readable.

Each key is on the top level of the CSON document, and then under that key is the info string, which elaborates the top level key.


"parts" is an array containing sub-categories/reasons. Each part contains the same format as described above, an info string, and can also contain other sub-sub-parts.



```
{
  dos: # top level key
    info: "Denial of service" # info string
    parts: [ # array of sub-categories/reasons
      http: "Denial of service via HTTP" # read: "http" is a subpart of the reason "dos" (Denial of Service can take place via HTTP)
    ]
}
```


## index/xxx-xxx-xxx-xxx.cson (dash delimited IP address)


1. First key is `ip`, this indicates the IP address explained within the document.
1. Second key is `recorded` this is the date where the IP was first seen in the format `YYYY/MM/DD`, same with `last_seen` but instead is the date where the IP was last seen to be violating.
1. Third key is `categories`, which states the reason (found in `reasons.cson` as explained above), where (sub)categories are referenced via the notation of `CATEGORY.SUBCATEGORY.SUBSUBCATEGORY.[...]`, since this is an array, multiple categories can be specified.
