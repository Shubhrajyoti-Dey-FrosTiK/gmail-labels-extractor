# Mails Label Extractor

This is a simple Google Cloud Function which extracts the labels of your email addresses and sends it back as an API Call response.

# Prerequisites

1. Golang installed on system
2. Make a GCP Account
3. Create OAuth2 Credentials from [here](https://console.cloud.google.com/apis/credentials/oauthclient)
4. Now you need a refresh token.
   The easiest way to get te refresh token is from [here](https://developers.google.com/oauthplayground/).
   Select `GMail API V1`.
   Select `https://mail.google.com/`
   Select `https://www.googleapis.com/auth/gmail.readonly`
   These will give you readonly rights
   Now select `Authorize` and choose your account.
   Then exchange the Authorization Code with a refresh token.
5. Install `Make` in the system. (Optional and only required for the last step in setup)

# Setup

1. Clone the repo

```
git clone https://github.com/Shubhrajyoti-Dey-FrosTiK/gmail-labels-extractor.git
```

2. Go inside the directory

```
cd gmail-labels-extractor
```

3. Create a `.env` file

```
touch .env
```

4. Put the credentials in the `.env` file like this

```
OATH_CLIENT_ID = ...
OATH_PROJECT_ID = ...
OATH_CLIENT_SECRET = ...
OATH_REDIRECT_URI = http://localhost
REFRESH_TOKEN = ...
```

5. Start the server by running this commande

```
make
```

# Walkthrough

`cmd/main.go` is the starting point of the application where the function server will be initialized.

`makefile` will set an env variable named `TARGET_FUNCTION` to the name of the path which we are calling the function. Suppose the URL is `http://..../api` then the function will be `api` here. After setting this we are starting the server by running the main.go file

In `cmd/main.go` we also see a blank import.This will import `functions.go` and will look for the init function.

In `functions.go` we define all the functions and we call the `labels` functions.

After you have started the server with the `make` command you can hit `http://localhost8080/labels` and check the output.
