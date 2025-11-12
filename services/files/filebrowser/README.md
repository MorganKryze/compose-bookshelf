# Filebrowser

## Special steps

After cloning the repository, and navigating to the `services/files/filebrowser` directory, make sure to perform the following steps before deploying the service:

Copy the example environment file to create your own `.env` file:

```bash
cp .env.example .env
```

Then, open the `.env` file in your preferred text editor and customize the settings as needed:

```bash
nano .env
```

> - `FILEBROWSER_CONFIG`: Path to the FileBrowser configuration file, you should not need to change this unless you have a specific reason.
> - `BASE_FOLDER`: The base directory that FileBrowser will manage. Set this to the path where you want to store and manage your files. You may add other volumes if needed as explained in [their documentation](https://filebrowserquantum.com/en/docs/advanced/source-configuration/sources/).

Then, you should have a volume mapping `- ${DOCKER_VOLUMES_PATH}/filebrowser/data:/home/filebrowser/data` in the `docker-compose.yml` file. This is where FileBrowser will store its data, including user accounts and settings. Once created on your host machine, move the provided `config.yml` file into that directory to set up the initial configuration.

```bash
# This is an example, adjust the path according to your docker volumes setup
mkdir -p ${DOCKER_VOLUMES_PATH}/filebrowser/data
mv data/config.yml ${DOCKER_VOLUMES_PATH}/filebrowser/data/
```

You **NEED** to update it, at least:

- Change the default admin user's password `adminPassword` to a secure password generated using a tool like `openssl` or `pwgen` or a password manager.
- Change the default totp secret `totpSecret` to a unique value for better security.
- You may also change, functional and cosmetic settings but is not mandatory.

Finally, start the service using Docker Compose:

```bash
docker-compose up -d
```

You may also follow its logs to ensure everything is running smoothly:

```bash
docker-compose logs -f
```
