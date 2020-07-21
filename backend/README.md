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
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlR6VjNiNG1jcFZXODJfWDhvbkhOWSJ9.eyJpc3MiOiJodHRwczovL2VsaWphaGRldi51cy5hdXRoMC5jb20vIiwic3ViIjoiYXV0aDB8NWYxNDc2NDU3ZmY2MGQwMDE5ZDY2ODBhIiwiYXVkIjoiZHJpbmtzIiwiaWF0IjoxNTk1MTc5MTQzLCJleHAiOjE1OTUyNjU1NDMsImF6cCI6IjRSWjlMMTkzbUFEakt6WGljWkJNZklZbm9wQzlLb1FtIiwic2NvcGUiOiIiLCJwZXJtaXNzaW9ucyI6WyJnZXQ6ZHJpbmtzLWRldGFpbCJdfQ.tMO1TxxuaZr2ZNz5G1fr5UULCjsIEvvSgvh2zY-Gnlf5HuzImfqNxVRNaVTCKU_2rBE_HERw1MuZYGTOKtuOY0rQZgjoXjlgcu5rqoFDlrV6WCxCRNDn5SfyFgsgIMyTu97xQyD-194L8wc-Guzi0r-ofE9HUDCnoAyRT9_HfjRatsOP8RO-04Gh0JY-sdYGAe1iYREtPXHAw-myDeaE08DZLL49QzaWcnvIumFjXPVPCNT5Ikc1RsbKyQLMCEqaZCK0tsp-YEI8g4_noKCwwUqqL4tv9mIcE959KBxoRzuvfSrHRVrqJco_ka6hW7Qn9xIbKQYYBCuBCNA0RvRysw

manager@cofee-cafe.com
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6IlR6VjNiNG1jcFZXODJfWDhvbkhOWSJ9.eyJpc3MiOiJodHRwczovL2VsaWphaGRldi51cy5hdXRoMC5jb20vIiwic3ViIjoiYXV0aDB8NWYxNDc5MWUyYWQzMmMwMDEzNGZmOTA2IiwiYXVkIjoiZHJpbmtzIiwiaWF0IjoxNTk1MTc4OTE4LCJleHAiOjE1OTUyNjUzMTgsImF6cCI6IjRSWjlMMTkzbUFEakt6WGljWkJNZklZbm9wQzlLb1FtIiwic2NvcGUiOiIiLCJwZXJtaXNzaW9ucyI6WyJkZWxldGU6ZHJpbmtzIiwiZ2V0OmRyaW5rcy1kZXRhaWwiLCJwYXRjaDpkcmlua3MiLCJwb3N0OmRyaW5rcyJdfQ.SqkMhkFXyOQD-6rYWAafnFgEBtdyg_oNPQ10SdpMAB1S6OA1qzsnk-7lcBeQuWM7cHlSw4BzWS0QivVpw8o_GsZycmK8Y5jR3vmT_wch7PLQZHdr8VYRa7Nk8hsU-bBpEDajuNPXXve6R95wISU5VMhegCzps9lRe52OqCFz-GXcUtcFNGmrLOvKpP8cLbJwDkyTvCnFaLs9OdHN0O59Gki-HFytZLQmtaw-JP9v92j50jWsw6zEN9lWlzOb_0zkQ3k0aSngsS881CDa39cp28i_DEdemYI3-9rtFCpK0FQcwVVPgb5DBz5QTuCbbYPfvcV7Kc_ZUKMXTke8p-FixA
