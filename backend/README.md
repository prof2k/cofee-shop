# Coffee Shop Backend

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

- [SQLAlchemy](https://www.sqlalchemy.org/) and [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) are libraries to handle the lightweight sqlite database. Since we want you to focus on auth, we handle the heavy lift for you in `./src/database/models.py`. We recommend skimming this code first so you know how to interface with the Drink model.

- [jose](https://python-jose.readthedocs.io/en/latest/) JavaScript Object Signing and Encryption for JWTs. Useful for encoding, decoding, and verifying JWTS.

## Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

Each time you open a new terminal session, run:

```bash
export FLASK_APP=api.py;
```

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

## Tasks

### Setup Auth0

1. Create a new Auth0 Account
2. Select a unique tenant domain
3. Create a new, single page web application
4. Create a new API
    - in API Settings:
        - Enable RBAC
        - Enable Add Permissions in the Access Token
5. Create new API permissions:
    - `get:drinks-detail`
    - `post:drinks`
    - `patch:drinks`
    - `delete:drinks`
6. Create new roles for:
    - Barista
        - can `get:drinks-detail`
    - Manager
        - can perform all actions
7. Test your endpoints with [Postman](https://getpostman.com). 
    - Register 2 users - assign the Barista role to one and Manager role to the other.
    - Sign into each account and make note of the JWT.
    - Import the postman collection `./starter_code/backend/udacity-fsnd-udaspicelatte.postman_collection.json`
    - Right-clicking the collection folder for barista and manager, navigate to the authorization tab, and including the JWT in the token field (you should have noted these JWTs). 
    - Run the collection and correct any errors.
    - Export the collection overwriting the one we've included so that we have your proper JWTs during review!

### Implement The Server

There are `@TODO` comments throughout the `./backend/src`. We recommend tackling the files in order and from top to bottom:

1. `./src/auth/auth.py`
2. `./src/api.py`

https://elijahdev.us.auth0.com/authorize?audience=drinks&response_type=token&client_id=4RZ9L193mADjKzXicZBMfIYnopC9KoQm&redirect_uri=http://127.0.0.1:8100/cofee-shop

barister@cofee-cafe.com - 
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlR6VjNiNG1jcFZXODJfWDhvbkhOWSJ9.eyJpc3MiOiJodHRwczovL2VsaWphaGRldi51cy5hdXRoMC5jb20vIiwic3ViIjoiYXV0aDB8NWYxNDc2NDU3ZmY2MGQwMDE5ZDY2ODBhIiwiYXVkIjoiZHJpbmtzIiwiaWF0IjoxNTk1MzMwMjM3LCJleHAiOjE1OTU0MTY2MzcsImF6cCI6IjRSWjlMMTkzbUFEakt6WGljWkJNZklZbm9wQzlLb1FtIiwic2NvcGUiOiIiLCJwZXJtaXNzaW9ucyI6WyJnZXQ6ZHJpbmtzLWRldGFpbCJdfQ.GXSk0Y7Fg-w3GlDA6pgcnh7VMxfyyFb78F4RNWO4pVrh4oZOAKXsTiatYECzgKhiSRVfh8s15AZ7PMR4VxSL8aa6pjVbNwPa59XSKiArRX8IGSSqBg7jJO_6MJC-H_A5StSXWE5o4OSP4y4TCqPPyGEfcrSOU8VgPbm5WGWWbpqcPEc3CdhHwFfBfMJxUl3G0K2MCZbkVG6sJWJFLj5g7IaF8cxS4BTGM7g0xfmffx_iSBo4IY3bqDSffj60ZSpM6mWp5U8MiFgn0B0ESFKvrhJNDCKFbsKtexmXlTGIwXMBj5yfki5dpcGjPyyBuL0mf1nG2f0U6u7nnAPkKFq8bg

manager@cofee-cafe.com
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlR6VjNiNG1jcFZXODJfWDhvbkhOWSJ9.eyJpc3MiOiJodHRwczovL2VsaWphaGRldi51cy5hdXRoMC5jb20vIiwic3ViIjoiYXV0aDB8NWYxNDc5MWUyYWQzMmMwMDEzNGZmOTA2IiwiYXVkIjoiZHJpbmtzIiwiaWF0IjoxNTk1MzMwMDYzLCJleHAiOjE1OTU0MTY0NjMsImF6cCI6IjRSWjlMMTkzbUFEakt6WGljWkJNZklZbm9wQzlLb1FtIiwic2NvcGUiOiIiLCJwZXJtaXNzaW9ucyI6WyJkZWxldGU6ZHJpbmtzIiwiZ2V0OmRyaW5rcy1kZXRhaWwiLCJwYXRjaDpkcmlua3MiLCJwb3N0OmRyaW5rcyJdfQ.bKWqRhVaZcRL4AEAX-kM99bttxYrXiZ7DvKN84Ov8m5kamHhOA_k9-PHMPWeHXAMqWsq9kcIVz1KJaw1Rl4ADqDsR0U4AHaOQcAjsjQReZx8-taKcjuAvkelXZbsA28mE2dh5h3m8VTqY0cBAQzQfHtTY1lzDgIcsAUXKMGSHKqmbLoSURw8bp5tEauzyKviMDmvBf4sb7trWbxpMs9YtUmY6luJ6Mpn_I1w19UHODaHSeVV8jyVBZDbDO_11bP4RKRmgrKm7_obuEqMcdihQ8y4U50DNPrOagnKLPCzS4xmGBNblRYccEzdOb8tGBgTSerWwFOIEb-N6n5kHMYdQg
