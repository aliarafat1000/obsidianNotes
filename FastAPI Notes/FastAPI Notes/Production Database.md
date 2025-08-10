Installing database for our application
We will be going over MySQL and PostgreSQL, with either DBMS we cannot go wrong

**Production DBMS vs SQLITE**

- Local data storage for individual applications and devices
- Economy, efficiency and simplicity, same server as your application
- Small to medium scale application
- Easy and quick, but we can expand to production database. *simplicity is the key*

Production:
- Scalability, control, concurrency
- Better stability then SQLite, when dealing with many many users.
- If small amount users use SQLite, then you can move to production database

Run:
- SQLite3 run in memory or local database, easy development as it's a part of the application
- Production database run on their own server and port, make sure database is running and have authentication linking to the database. 
- SQLite3 deploy database, we deploy along with our application
- Prod DBMS is deployed separately, more work in the long run.

**We will cover in the section: **
- We will setup -> install, setup tables and data withing production DBMS, connect the production DBMS to our application -> Push data from our application to our production DBMS. 

*Next: [[PostgreSQL]]
*


