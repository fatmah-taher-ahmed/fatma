# Udacity Catalog

Udacity FSND project

This full stack app allows users to login into the system and add different types of items to the database.
Each user is the owner of the items they have added and no other user can modify those items.
Also, no unauthenticated user has the right to make changes to the database.


## Screenshots

#### Main page with login

![Main page with login](https://i.imgur.com/7YyNFxR.png)

#### Category page without login

![Category page without login](https://i.imgur.com/DIRASWq.png)


## Running instructions

Tested on **Python 3**.

* Set Google OAuth credentials. See the [next section](#oauth) for this.

* Install requirements.

```sh
pip install -r requirements.txt
```

* Setup database.

```sh
# python manage.py db init     # init migrations folder at project start
# python manage.py db migrate  # generate migration files in case of model change
# ^^ the above two commands required in development. Not required when running this project for the first time.
python manage.py db upgrade  # upgrade/create database
```

* Create initial categories.

```sh
python create_category.py
```

* Start server.

```sh
python manage.py runserver
```

* Access on `http://localhost:5000`.


<a name="oauth"></a>
## Generating Google OAuth credentials

* Create a project on [developers.google.com](https://console.developers.google.com/).
* Go to Credentials. Then select "Add Credentials" -> "OAuth (v2) token". Choose `Web` as the type.
* In the next page, make sure you have `http://localhost:5000` in authorized JavaScript origins and `http://localhost:5000/gCallback` in Redirect URIs.
* Get your client ID and client secret.
* Put it in [config.py](config.py).


## Extra features

Spaces in item name are converted to dashes in the url to make things look pretty. Example `http://localhost:5000/catalog/Slice-of-Life/Shigatsu-wa-kimi-no-uso`

This project uses flask-migrate and Alembic for database migrations. So no data loss or manual upgrade of database when database models are changed.


## Notes

The JSON format of the catalog can be accessed from `/catalog.json`.


## Thanks

* Google OAuth - http://bitwiser.in/2015/09/09/add-google-login-in-flask.html
