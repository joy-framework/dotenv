# dotenv

dotenv is a [one-dependency](https://github.com/joy-framework/tester) module that loads environment variables from a .env file or from the actual `os/env`

## Install

```sh
# with jpm
jpm install https://github.com/joy-framework/dotenv
```

## Usage

```clojure
(import dotenv :as env)
```

Create a `.env` file in the root directory of your project. Add environment-specific variables on new lines in the form of NAME=VALUE. For example:

```bash
MY_ENV=development
DB_NAME=my_app.sqlite3
```

Here's a pretty thorough example of how to use it

```clojure
(import dotenv :as env)

(= (env :db-name) "my_app.sqlite3")
(= (env :my-env) "development")

(= nil (os/env "DB_NAME"))
(= nil (os/env "MY_ENV"))

(os/setenv "PORT" "1337")

(= (env :port) "1337")
(= (env :PORT) "1337")
(= (os/env "PORT") "1337")
```

Enjoy!
