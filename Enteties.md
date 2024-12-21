---
tags:
  - pet-project
---
Medicine(Drug)
- Id (guid)
- Name (string 300)
- Description (string 1000)
- Ingredients (many-to-many with Substance)
- Form (MedicineForm enum)
- Dosage (string)
- Manufacturer (Company)
- Tags

Ingredients
- Id (guid)
- Medicine Id
- Substance Id
- Quantity (string)
- Is Active (bool)
- Manufacturer (Company)

Substance
- Id (guid)
- Name (string 1000)
- Description (string 10000)
- Formula (string 1000) 

Company
- Id (guid)
- Name (string 300)
- Country (string 100)
- Address (string 500)
- Contact Info (string 300)

Tag
- Name

---
public enum DosageForm { [Description("Tablets")] Tablet = 100, [Description("Capsules")] Capsule = 200, [Description("Syrups")] Syrup = 300, [Description("Injections")] Injection = 400, [Description("Creams")] Cream = 500, [Description("Ointments")] Ointment = 600, [Description("Powders")] Powder = 700, [Description("Suppositories")] Suppository = 800, [Description("Drops")] Drop = 900, [Description("Patches")] Patch = 1000 }