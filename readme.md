O  # Apartment Database

- Create a database called `apartments`
- Using this database, create two tables, one for owners and one for properties
- Keep this relationship in mind when designing your schema:
  + **One owner can have many properties**

###Part 1: Create Tables

- The owners table should consist of:
  + `id` (this should be the primary key as well as a unique number that increments automatically)
  + `name` - name of owner
  + `age` - age of owner
- The properties table should consist of:
  + `id` (this should be the primary key as well as a unique number that increments automatically)
  + `name` - name of property
  + `units` - number of units
  + `owner_id` - reference to owner table
    + Remember to create a foreign key constraint that references the owners table

###Part 2: Insert Data

* Insert the following owners
    * Donald - age 29
    * John - age 33
    * Jane - age 43
    * Add 3 more people (you choose name / age)

* Insert the following properties (you can pick and choose the property owners)
    * Archstone - 20 units
    * Willowspring - 30 units
    * Add 3 more properties (you choose name / units)

###Part 3: Use Your Database

Write down the following sql statements that are required to solve the following tasks.

1. Show all the data in the owners table.
SELECT * FROM owners;

* Show the names of all owners.
SELECT * FROM owners ORDER BY name;

* Show the ages of all of the owners in ascending order.
SELECT * FROM owners ORDER BY age;

* Show the name of an owner whose name is Donald.
SELECT * FROM owners WHERE name = 'Donald'

* Show the age of all owners who are older than 30.
SELECT * FROM owners WHERE age > 30;

* Show the name of all owners whose name starts with an E.
SELECT * FROM owners WHERE name LIKE 'E%';

* Change Jane's age to 30.
UPDATE owners SET age=30 WHERE name = 'Jane';

* Change Jane's name to Janet.
UPDATE owners SET name = 'Janet' WHERE id = 3;
* Delete the owner named Janet.

* Show the names of the first three owners in your owners table.

SELECT * FROM owners ORDER BY id limit 3

apartments
id |   name   | age
----+----------+-----
 1 | Donald   |  29
 2 | John     |  33
 4 | Brittany |  31


###Bonuses

These might require you to look up documentation online, or look at the next section in the notes.

1. In the properties table change the name of the column "name" to "property_name".
ALTER TABLE properties RENAME name TO property_name;

* Count the total number of properties where the owner_id is between 1 and 3.

SELECT COUNT(owner_id) FROM properties WHERE owner_id > 1 AND owner_id < 3;

* Show all of the properties in alphabetical order that are not named Archstone and do not have an id of 3 or 5.

SELECT property_name FROM properties WHERE property_name <> 'Archstone' AND id <> 3 AND id <> 5 ORDER BY property_name;

* Show the highest age of all owners.
SELECT * FROM owners ORDER BY age DESC limit 1;

* Show the name of all owners whose name starts with an E.

REPEAT FROM ABOVE

* List all properties sorted by the owners names

SELECT * FROM properties INNER JOIN owners ON properties.owner_id = owners.id ORDER BY owners.name;

---

## Licensing
1. All content is licensed under a CC-BY-NC-SA 4.0 license.
2. All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
