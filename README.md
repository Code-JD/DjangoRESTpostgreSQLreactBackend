# DjangoRESTpostgreSQLreactBackend

- Building a Todo App with a focus on Backend developemnt

- Following DigitalOcean's [Documentation](https://www.digitalocean.com/community/tutorials/build-a-to-do-application-using-django-and-react) to build out the basic Frontend in [React](https://reactjs.org/docs/getting-started.html) and a Backend with [Django](https://docs.djangoproject.com/en/3.1/)

- This was developed using [WSL2](https://docs.microsoft.com/en-us/windows/wsl/install-win10) on a Windows machine, so all command line script will be written accordingly

---

## Things that were different than in the "Movies"

   I mean in the Documentation, the tutorial... never mind, bad dad joke

![alt text](https://i.imgur.com/48jjojJ.gif)

- 3rd command down won't work if you are using Pip3, so use this command:

  Install Pip3:

```python
  pip3 install pipenv
```

- When you add the `CORS_ORIGIN_WHITELIST` port for the frontend make sure and use a `,` after `'http://localhost:3000'`

```python
CORS_ORIGIN_WHITELIST = (
    'http://localhost:3000',
)
```

- In `frontend/src/App.js` there is a missing `/` at the end of the Axio Delete call

```python
handleDelete = item => {
axios
  .delete(`http://localhost:8000/api/todos/${item.id}/`)
  .then(res => this.refreshList());
};
```

- Then install [psycop2](https://pypi.org/project/psycopg2/) for the PostgreSQL database

```python
pip3 install pyscop2
```

- Set up a PostgreSQL database  with [paAdmin](https://www.pgadmin.org/) locally on your machine or on some Linux server somewhere [ElephantSQL](https://www.elephantsql.com/) [AWS](https://aws.amazon.com/rds/postgresql/)

![alt text](https://i.imgur.com/iiafQsm.png)

- Then in the setting.py file in the 'backend' folder change the info under 'DATABASES' to this

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432'
    }
}
```
