---
tags:
  - database
  - indexes
---
# What is it?
is an on-disk structure associated with a table or view, contains keys built from one or more columns and those keys are stored in a B-tree structure(?) that enables to find associated rows quickly and efficiently

improve query performance

# What type they can be?

## Clustered 
is based on table keys data, can be only one per table

## Nonclustered
have structure separate from data rows, and each index has a pointer to data row (called __row locator__).

both can be unique (no two rows can have same value for index key)
