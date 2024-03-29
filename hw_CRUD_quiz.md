# CRUD Quiz

Use the solution to this afternoon's Property Tracker lab to answer the following questions. Please write your answers under each question, push the file to GitHub, and submit in the usual way.

## MVP Questions

In our Property Tracker application:

Q1. Where are we instantiating instances of the `Property` class?

console.rb

Q2. Where are we defining the SQL that enables us to save the ruby `Property` object into the database?

sql =

Q3. In `console.rb`, which lines modify the database?

.delete_all
.save
.delete

Q4. Why do we not define the id of a `Property` object at the point we instantiate it (‘new it up’)?

Is it because it's auto-generated for us as soon as we make the row?
@id = db.exec_prepared("save", values)[0]["id"].to_i

Q5. Where and how do we assign the id (that is generated by the database) to the ruby `Property` object?

RETURNING id <- part of the SQL
@id = db.exec_prepared("save", values)[0]["id"].to_i

Q6. Why do we put a guard (an `if` clause) on the `@id` attribute in the constructor?

Don't know.

Q7. Why are some of the CRUD actions represented by instance methods, and others by class methods?

Class methods can be used without instances being present. This is useful for deleting all and selecting all.

Q8. What type of data structure is returned by calls to `db.exec_prepared()`? In the `save` method, how do we access the id from the returned data structure?

PGResult object. It is an array of hashes. Each hash is a potential row in the table.
@id = db.exec_prepared("save", values)[0]["id"].to_i

Q9. Why do we use prepared statements when performing database operations?

To limit the values that can be inputted in the query. This stops values we don't want being inputted.

## Extension Questions

Look at the `find_by_id` and `find_by_address` methods in the `Property` class.

Q10. What do they take in as their arguments?

A particular property's id.
address column.

Q11. What are their return values?

A instance of Property with the parameter.
The parameter is either:
Either an array of hashes.
Or just a hash.
