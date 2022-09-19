https://github.com/Gollum959/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg

[**Description of the project**](#description-of-the-project)

[**Filling the env file**](#filling-the-env-file)

[**Commands to run an application in containers**](#commands-to-run-an-application-in-containers)

[**Command to fill in the database**](#command-to-fill-in-the-database)

[**Authors**](#authors)

[**Technologies**](#technologies)


## Description of the project

The YaMDb project collects users reviews about works, divides them into categories(for example, books, films, music). A work can be assigned one or more genres. 
A user can make one text review for the work available in the YaMDb database and rate it on a scale from one to ten. Only admin can add new works. 
You can leave comments on review
### Some examples of valid API requests

**Registration and authorization of a new user**
> POST |  [http://127.0.0.1:8000/api/v1/auth/signup/](http://127.0.0.1:8000/api/v1/auth/signup/)
```
{
"email": "pochta@mylo.ru",
"username": "test_user"
}
```
> 200 OK

>  POST |  [http://127.0.0.1:8000/api/v1/auth/token/](http://127.0.0.1:8000/api/v1/auth/token/)
```
{
"username": "test_user",
"confirmation_code": "61p-c0443f686f2ea7e2444f"
}
```
> 200 OK

**Getting a list of all categories**
> GET |  [http://127.0.0.1:8000/api/v1/categories/](http://127.0.0.1:8000/api/v1/categories/)
> 200 OK

**Search by genre**
> GET |  [http://127.0.0.1:8000/api/v1/genres/?search=rock-n-roll](http://127.0.0.1:8000/api/v1/genres/?search=rock-n-roll)
> 200 OK

## Filling the env file

**DB_ENGINE**=django.db.backends.postgresql  # indicate that we are working with postgresql
**DB_NAME**=postgres  # database name
**POSTGRES_USER**=postgres  # database login
**POSTGRES_PASSWORD**=postgres  # database password
**DB_HOST**=db  # name of the service (container) 
**DB_PORT**=5432  # port for connecting to the database
**SECRET_KEY**=' ' # django Secret Key
**DEBUG**= # True or False
**ALLOWED_HOSTS**=[] # for example ['localhost', '127.0.0.1', 'web']

## Commands to run an application in containers
```
docker-compose up -d
docker-compose exec web python manage.py migrate 
docker-compose exec web python manage.py createsuperuser 
docker-compose exec web python manage.py collectstatic --no-input
```
## Command to fill in the database
```
docker-compose exec web python manage.py loaddata fixtures.json
```
## Authors
[Aleksandr Alekseev](https://github.com/Gollum959/)

## Technologies

Project is created with:
* Python 3.7
* PostgreSQL
* Django 2.2.16
* Django REST framework 3.12.4
