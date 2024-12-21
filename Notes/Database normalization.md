---
tags:
  - database
  - normalization
---
---
summary from - [source](https://learn.microsoft.com/en-us/office/troubleshoot/access/database-normalization-description)

---
#### 
What it is?
is a **process of organizing data**, includes creating tables and establishing relationships between tables. 

*inconsistent dependencies* - path to find data may be missed or broken. there are few rules for database normalization, each is called a **normal form**, third form is considered the highest level necessary for most applications (is observed it will called third normal form database).

#### First normal form
- no repeating groups in individual tables (data is not duplicating)
- create a separate table for each set of related data
- identify each set of related data with a primary key
#### Second normal form
- create separate tables for sets of values that apply to multiple records
- relate these tables with a foreign key
#### Third normal form
- eliminate fields that don't depend on the key
For example, `in an Employee Recruitment table, a candidate's university name and address may be included. But you need a complete list of universities for group mailings. If university information is stored in the Candidates table, there is no way to list universities with no current candidates. Create a separate Universities table and link it to the Candidates table with a university code key.`
#### Other normalization forms
- fourth normal form (Boyce-Codd Normal Form (BCNF))
- fifth normal form
they do exists but rarely considered in practical design