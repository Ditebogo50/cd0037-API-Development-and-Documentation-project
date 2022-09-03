# TRIVIA APP

This project is a trivia game and compleeting it helped me gain more knowledge on implementing and testing an API. And also gain more knowledge on HTTP best practices.

# Getting Started

Currently the application is run on http://127.0.0.1:5000/ by default and is a proxy in the frontend configuration.

Authentication: This version of the application does not require authentication or API keys.

## Error Handling
Errors are returned as JSON objects in the following format:

```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```

The API will return four error types when requests fail:

- 404:Resource not found
- 422:Not Processable
- 405:Method not allowed
- 500:Internal server error

## Endpoints

### GET '/categories'
 - Fetches a dictionary of categories in which the keys are the ids and the value is the corresponding string of the category
 - Returns: An object with a single key, categories, that contains an object of id: category_string key:value pairs.

```
{
    {
    'categories': { '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports" }
}
}
```

### GET '/questions?page=${integer}'
 - Fetches a paginated set of questions, a total number of questions, all categories and current category string.
 - Request Arguments: page - integer
 - Returns: An object with 10 paginated questions, total questions, object including all categories, and current category string


```
{
    'questions': [
        {
            'id': 1,
            'question': 'This is a question',
            'answer': 'This is an answer',
            'difficulty': 5,
            'category': 2
        },
    ],
    'totalQuestions': 100,
    'categories': { '1' : "Science",
    '2' : "Art",
    '3' : "Geography",
    '4' : "History",
    '5' : "Entertainment",
    '6' : "Sports" },
    'currentCategory': 'History'
}
```

### GET '/categories/${id}/questions'
 - Fetches questions for a cateogry specified by id request argument
 - Request Arguments: id - integer
 - Returns: An object with questions for the specified category, total questions, and current category string
```
{
    'questions': [
        {
            'id': 1,
            'question': 'This is a question',
            'answer': 'This is an answer',
            'difficulty': 5,
            'category': 4
        },
    ],
    'totalQuestions': 100,
    'currentCategory': 'History'
}
```

### DELETE '/questions/${id}'

 - Deletes a specified question using the id of the question
 - Request Arguments: id - integer
 - Returns: Does not need to return anything besides the appropriate HTTP status code. Optionally can return the id of the question. If you are able to modify the frontend, you can have it remove the question using the id instead of refetching the questions.

### POST '/quizzes'
 - Sends a post request in order to get the next question
 - Request body:

```
{
    'previous_questions': [1, 4, 20, 15]
    quiz_category': 'current category'
 }
```

- Returns: a single new question object

```
{
    'question': {
        'id': 1,
        'question': 'This is a question',
        'answer': 'This is an answer',
        'difficulty': 5,
        'category': 4
    }
}
```

### POST '/questions'
 - Sends a post request in order to add a new question
 - Request Body:

```
{
    'question':  'Heres a new question string',
    'answer':  'Heres a new answer string',
    'difficulty': 1,
    'category': 3,
}
```
- Returns: Does not return any new data

### POST '/questions'
 - Sends a post request in order to search for a specific question by search term
 - Request body:

```
{
    'searchTerm': 'this is the term the user is looking for'
}

```
- Returns: any array of questions, a number of totalQuestions that met the search term and the current category string

```
{
    'questions': [
        {
            'id': 1,
            'question': 'This is a question',
            'answer': 'This is an answer',
            'difficulty': 5,
            'category': 5
        },
    ],
    'totalQuestions': 100,
    'currentCategory': 'Entertainment'
}
```













```python
```

hi this `is code` 