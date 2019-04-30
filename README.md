# Automad Docker

Docker container for the Automad flat-file CMS.

## Download

```bash
git clone https://github.com/LCBRU/automad_docker.git
```
## Run

1. Copy the 3 example directories

```bash
cp -r example_config config
cp -r example_pages pages
cp -r example_shared shared
```

2. Copy `example.env` to `.env` and populate it with appropriate values.  For
example, if using the example directories from above:

```
# Server Setup

PORT=2000
THEME=brc_automad_theme

# Volumes

CONFIG=./config
PAGES=./pages
SHARED=./shared

```

3. Build and bring up the container:

```
docker-compose build
docker-compose up
```

4. Got to the url, for example http://localhost:2000/.
5. To edit the pages got to http://localhost:2000/dashboard and log in
using the username `admin` and the password `admin`.

## Security

To create a more secure admin account, follow this process.

1. remove the `accounts.php` file from `config` directory.
2. Go to http://localhost:2000/dashboard, where it will ask you to enter a username and password.
3. When you submit the form, you will download a new `accounts.php` file.
4. Place this file in the `config` directory.
