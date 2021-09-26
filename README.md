# flask-pytest-ci-cd

## Installation

1. First Create a new project on GitLab.
2. Cone the project using the the `git clone` following with git project URL.
3. Create a new python3 virtual environment using `python3 -m venv myven`
4. Next active our environment `source myven/bin/activate`
5. Then install flask and pytest `pip3 install flask pytest` and upgrade pip3 using `python3 -m pip install --upgrade pip`
6. Change to the `cd myven` directory.
7. Use `pip3 freeze > requirements.txt` to export all the requirements in a file.
8. You can use `cat requirements.txt` command to check all the requirements.
9. Create a new directory called `src` and change directory `cd src`
10. Use `touch app.py` to create a new python file.
11. Use `vi app.py` command and import flask and add an app object and function by adding the bellow lines.

```
from flask import Flask
app = Flask(__name__)

@app.route("/")
def index():
	return "Hello World!"

if __name__ == "__main__":
	app.run()
```

12. Create a test folder `mkdir tests` and change directory `cd tests`
13. Create a python test file using `touch test_app.py`
14. `vi test_app.py` to edit the file and add below lines to create a simple unit test.

```
from app import index

def test_index():
    assert index() == "Hello World!"
```
15. Return to the root of the project folder `cd ..`
16. Run `python3 -m pytest`
17. If you receive and error (No module named app) run `export PYTHONPATH=src` and `echo $PYTHONPATH`
 to confirm. Because test package does not know what is app.
18. Run again `python3 -m pytest` and the test should pass.
19. `touch .gitignore` to create ignore file for virtual environment we have created and `vi .gitignore` or from editor.

```
myven/
__pycacheg__/
```

20. `git status`to check the changes
21. `git add .` to add the all files
22. `git commit -m "Initial Commit"`
## Requirements

- [Python](https://www.python.org/downloads/)
- [MySQL Server](https://dev.mysql.com/downloads/mysql/)
- [MongoDB Server](https://www.mongodb.com/try/download/community)



```
# Import MongoClient from pymongo library 
from pymongo import MongoClient 

# MySQL DB connection parameters 
SQL_URL = <Host address for MySQL DB server> 
USERNAME = <MySQL DB username> 
PASSWORD = <MySQL DB password> 
DB_NAME = <MySQL DB schema name> 

# Configure GitLab connection 
GITLAB_URL = <GitLab URL to mine the source code data> 

# The 'PROJECTS' is a key-value pair with key as the project id and value as the GitLab 
# example - { 1234: "abcdefghij1234567890", 5678: "zyxwvutsrq0987654321" } 
PROJECTS = <{'Project ID 1': 'GitLab access token 1', 'Project ID 2': 'GitLab access token 2'}> 

USER_ID = <99999 - Assign a unique User ID for contributors in GitLab with no IDs> 

# Configure Mongo DB connection # 
passwordMongo = <Mongo DB password> 
MONGODB_URL = <Mongo DB connection URL> 
client = MongoClient(MONGODB_URL, ssl = True) 

# Create objects of Mongo DB database collections 
mdb = client.<Mongo DB username>.<Mongo DB collection name for Developer profiles> 
mdb_projects = client.<Mongo DB username>.<Mongo DB collection name for Project profiles> 
```

## API Routes
This application features many API routes to access different information. These API routes are documented here. 

```
/api/developers/
```