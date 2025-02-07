All companies store data
- Sometimes this requires a database

What is a database?
- A collection of data
	- Of many different types

May require a DBMS
- "Database management system"
- One or more pieces of software that allow us to
	- Read, write, and manage data

Two types of DBMS that are popular right now
- Examples
	- PostgreS(QL)
	- MongoDB
- Relational database
- NoSQL database

Relational databases
- Two or more tables 
- With columns and rows
	- A column
		- Stores a specific type of data
	- A row 
		- A collection of columns
- For example
	- Users (table)
		- full_name
		- username
		- test
		- created_at
	- Tweets (table)
		- id
		- text
		- created_at
		- username
	- Following
		- from_user
		- to_user
- Use SQL for "communication"
	- Create
	- Read
	- Update
	- Delete

NoSQL data store (non-relational database)
- For example
	- MongoDB
	- Cassandra
	- CouchDB
- Do not require defining a schema before use
- Offer greater flexibility than relational database
- MongoDB
	- Stores "documents"
	- Consider a relational database with
		- Users
		- Tweets
		- Profile
		- Following
	- MongoDB has "documents"
		- user1.txt
		- user2.txt
		- user3.txt
		- Each document may have 
			- Tweets
			- Profile
			- Following
			- **Embedded** in the document

At a high-level
- Relational databases
	- Blog post
	- Blog tags
	- Blog comments
	- All related (via "relations")
- MongoDB
	- Has a single document
		- For example, "Blog post"
	- Each document has
		- Comments
		- Tags
		- Categories
		- Other related data

What does MongoDB use to communicate?
- The MongoDB query language
	- Communicates with data to perform
		- CRUD operations
