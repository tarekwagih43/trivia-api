# Full Stack Trivia API Backend

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Enviornment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organaized. Instructions for setting up a virual enviornment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/)  is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) is the Python SQL toolkit and ORM we'll use handle the lightweight sqlite database. You'll primarily work in app.py and can reference models.py. 

- [Flask-CORS](https://flask-cors.readthedocs.io/en/latest/#) is the extension we'll use to handle cross origin requests from our frontend server. 

## Database Setup
With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:
```bash
psql trivia < trivia.psql
```

## Running the server

From within the `backend` directory first ensure you are working using your created virtual environment.

To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

Setting the `FLASK_ENV` variable to `development` will detect file changes and restart the server automatically.

Setting the `FLASK_APP` variable to `flaskr` directs flask to use the `flaskr` directory and the `__init__.py` file to find the application. 


REVIEW_COMMENT
```
This README is missing documentation of your endpoints. Below is an example for your endpoint to get all categories. Please use it as a reference for creating your documentation and resubmit your code. 

Endpoints
GET '/categories'
GET ...
POST ...
DELETE ...
```
## Documentation

### GET '/categories'
- Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
- Request Arguments: None
- Returns: An object with a single key, categories, that contains a object of id: category_string key:value pairs. 
```
{
    '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports"
}
```

### GET '/questions'
- Feches a dictionary of questions and total questions 
- returens only 10 results each time, you can request next results with request argument.
- request argument: "page"
- returns data of that structure

```
{
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  }, 
  "questions": [
    {
      "answer": "Muhammad Ali", 
      "category": 6, 
      "difficulty": 2, 
      "id": 31, 
      "question": "What boxer's original name is Cassius Clay?"
    }
    ], 
  "success": true, 
  "total_questions": 1
}

```

### DELETE '/questions/1'
- Deletes a question with spacific id which in that case "id=1"
- if the id of the question is in the database, the response is 
```
{
    "success": True
}
```
- if the id is not in the database it will abort with 404

### POST '/questions'
- creates a new question 
- adding new question requires you to send (the quistion, the answer, the category, the difficulty)
- that will send you, if success:
```
{
    "success": True
}
```
 if not:
    will abort with 400 error, because some way yor request is unprocessable.

### POST '/search'
- with that endpoint you can search the questions with any word in the question it self.
- end point expects to recive parameter "searchTerm".
- the response of that will be:
```
{ 
    "categories": {
        "1": "Science", 
        "2": "Art", 
        "3": "Geography", 
        "4": "History", 
        "5": "Entertainment", 
        "6": "Sports"
  }, 
    "questions": [
        {
        "answer": "Muhammad Ali", 
        "category": 6, 
        "difficulty": 2, 
        "id": 31, 
        "question": "What boxer's original name is Cassius Clay?"
        }
    ], 
    "success": true, 
    "total_questions": 1
}
```

### GET '/categories/1/questions'
- endpoint to filter the questions with category
- parametars : "category id as (1) in that case"
- the response will be:
```
{ 
    "categories": {
        "1": "Science", 
        "2": "Art", 
        "3": "Geography", 
        "4": "History", 
        "5": "Entertainment", 
        "6": "Sports"
  }, 
    "questions": [
        {
        "answer": "Muhammad Ali", 
        "category": 6, 
        "difficulty": 2, 
        "id": 31, 
        "question": "What boxer's original name is Cassius Clay?"
        }
    ], 
    "current_category": {
        "6": "Sports"
    }, 
    "success": true, 
    "total_questions": 1
}
```

## POST '/quizzes'
- endpoint geves back random question from a choseen category or from all.
- the end point expects the resive the previce question in not the first question time.
- expect the response will by:
```
{  
    "questions": [
        {
        "answer": "Muhammad Ali", 
        "category": 6, 
        "difficulty": 2, 
        "id": 31, 
        "question": "What boxer's original name is Cassius Clay?"
        }
    ], 
    "success": true, 
}
```

## Testing
To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```
