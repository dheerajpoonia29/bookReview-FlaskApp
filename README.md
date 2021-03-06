# BOOK REVIEW 
<hr/>
<br/>

## PROJECT SCREENSHOT
| login page             |  sign-up page |
:-------------------------:|:-------------------------:
![login-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/loginpage.png?raw=true)  |  ![signup-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/signuppage.png?raw=true)

| sign-success-page             |  list of books page |
:-------------------------:|:-------------------------:
![sign-success-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/signupsuccesspage.png?raw=true)  |  ![list-books-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/listofbooks.png?raw=true)

| give review page             |  view review page |
:-------------------------:|:-------------------------:
![give-review-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/givereview.png?raw=true) |  ![view-review-page](https://github.com/dheerajpoonia29/bookReview-projectPythonFlask/blob/master/projectImage/viewreview.png?raw=true)


## CREATING FASK SERVER 
### Create server syntax 
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
return 'Hello, World!'
```
### Run server command 
*   on linux export appName.py
```
$ export FLASK_APP=main.py
$ export FLASK_ENV=development
$ flask run
```
*   on window we need to set environment variable ps is powershell make sure venv is activated 
```
(venv) PS > $env:FLASK_APP = "app.py"
(venv) PS > $env:FLASK_ENV= "development"    # optional
(venv) PS > flask run
```

## DATABASE 
### postgres vs mysql 
*   postgres
-   PostgreSQL is an object-relational database management system (ORDBMS) based on postgres
-   based on object data model
-   support sql structure-query-language
-   docs: [![what is postgres]](https://www.postgresql.org/docs/13/intro-whatis.html)
-   ORDBMS vs OODBMS
--   OODBMS - object oriented database management system 
--   OODBMS aimed at applications where an object-centric viewpoint is appropriate, mainly used in cpp or java
--   ORDBMS focus on large data collections 
*   mysql   
-   Mysql is an relational database management system (RDBMS) based on sql 
-   based on relational data model
-   docs: [![what is msql](https://dev.mysql.com/doc/refman/8.0/en/what-is-mysql.html)]
-   RDBMS vs ORDBMS
--  RDBMS stores only data.
--  ORDBMS Stores data as well as methods to use it.
--  ORDBMS Handles larger and complex data than RDBMS.

*   mongodb
-   MongoDB is a document oriented database management system
-   based on document data model
-   use MongoDb query language (mql) does not support sql
-   docs: [![what is mongodb](https://docs.mongodb.com/manual/introduction/)]
### postgres sql commong syntax 
*   heroku used for db based on postgres
-   email : dheerajbishnoi123
-   db : https://data.heroku.com/datastores/c848db28-1ef7-4d42-b21b-2d8d015bf5a2
-   why i use : it provide free db with 10000 entries on heroku cloud
-   Host     ec2-54-83-17-151.compute-1.amazonaws.com
-   Database     dce25fb79tcjcv
-   User     ntcwaduvpgeowm
-   Port    5432
### object relational mapping 
*   orm module provide by sqlalchemy python library
*   this orm module have 2 method scoped_session(start session), sessionmaker(create connection)
-   connect with db syntax
```
db = scoped_session(sessionmaker(bind=create_engine('postgres://user:secret@host:port/database', echo = True))
```
-   query syntax from backend to database 
```
bookselect = db.execute("SELECT * FROM book WHERE book_id = :book_id",{"book_id": book_id}).fetchone()
sid = db.execute("SELECT student_id FROM student WHERE username =:username", {"username": username}).fetchone();
booksdb = db.execute("SELECT * FROM book LIMIT 10 ").fetchall()
db.execute("SELECT * FROM review WHERE student = :student_id and book =:book_id", {"student_id": student_id, "book_id": book_id}).rowcount
db.execute("INSERT INTO review (scale, texts, student, book) VALUES (:scale, :texts, :student, :book)", {"scale": scale, "texts": texts, "student": student_id, "book": book_id})
db.commit()
```
