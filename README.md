# The Yatube API project
Yatube is a social network for writers. It gives users the ability to create an account, post publications, follow their favorite authors, and tag posts they like.

## Resources API YaMDb
**POSTS**: Published posts.

**GROUPS**: Groups uniting publications on the subject.

**FOLLOW**: User subscriptions.

**COMMENTS**: Comments on posts.

## The technology stack is available in requirements.txt

## How to run the project:

Clone the repository and change into it on the command line:
```
git clone https://github.com/t0pdog/api_final_yatube.git
cd api_final_yatube
```

Create and activate virtual environment:
```
python -m venv venv
. venv/Scripts/activate
```

Install dependencies from requirements.txt file:
```
pip install -r requirements.txt
```

Run migrations:
```
python manage.py migrate
```

Run project:
```
python manage.py runserver
```

Redoc documentation is available at:
```
http://127.0.0.1:8000/redoc/
```

## Here are some examples of endpoint requests and their responses:

### Get a list of all publications. When specifying parameters limit and offset output should work with pagination. (GET request):

```
http://127.0.0.1:8000/api/v1/posts/
```

Server response:
```
{
  "count": 123,
  "next": "http://api.example.org/accounts/?offset=400&limit=100",
  "previous": "http://api.example.org/accounts/?offset=200&limit=100",
  "results": [
    {
      "id": 0,
      "author": "string",
      "text": "string",
      "pub_date": "2021-10-14T20:41:29.648Z",
      "image": "string",
      "group": 0
    }
  ]
}
```

### Adding a new publication to the collection of publications. Anonymous requests are prohibited. (POST request):

```
http://127.0.0.1:8000/api/v1/posts/
```
In the request body, we pass parameters to create a publication:
```
{
  "text": "string",
  "image": "string",
  "group": 0
}
```

Possible server responses:

* 1. 201 Successful execution of the request:
```
{
  "id": 0,
  "author": "string",
  "text": "string",
  "pub_date": "2019-08-24T14:15:22Z",
  "image": "string",
  "group": 0
}
```

* 2. 400 Missing required field in request body:
```

{
  "text": [
    "required field."
  ]
}
```

* 3. 401 Request on behalf of an anonymous user:
```

{
  "detail": "Credentials were not provided."
}