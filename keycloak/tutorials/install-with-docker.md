# Install with docker

## Minimal configuration (easiest)

```bash
docker run --name keycloak -d -p 8080:8080 -e KEYCLOAK_ADMIN=admin -e
KEYCLOAK_ADMIN_PASSWORD=admin quay.io/keycloak/keycloak:latest start-dev
```

(to run it you need to delete spaces)

## Minimal configuration (production)

```bash
docker run -v G:/keycloak:/opt/keycloak/conf -p 8443:8443 -net keycloak-network
-e KEYCLOAK_ADMIN=admin -e KEYCLOAK_ADMIN_PASSWORD=admin -e
KC_DB=mysql -e KC_DB_URL=jdbc:mysql://mysql:3306/keycloak?useSSL=false -e
KC_DB_USERNAME=keycloak -e KC_DB_PASSWORD=password -e
KC_HOSTNAME=localhost quay.io/keycloak/keycloak:latest start-auto-build
-db=mysq
```

(to run it you need to delete spaces)

### Legend:

* `docker run`: Run a Docker container.
* `--name keycloak`: Assign the name "keycloak" to the container.
* `-d`: Detaches and runs it in the background.
* `-p 8080:8080`: Maps port 8080 on the host machine to port 8080 in the container.&#x20;
* `-e KEYCLOAK_ADMIN=admin`: Sets the environment variable `KEYCLOAK_ADMIN` . This sets the admin username for the Keycloak instance.
* `-e KEYCLOAK_ADMIN_PASSWORD=admin`: Sets the environment variable `KEYCLOAK_ADMIN_PASSWORD`. This specifies the admin password for the Keycloak instance.
* `quay.io/keycloak/keycloak:latest`: The Docker image to use for the container. In this case, it's the latest version of the Keycloak image from Quay.io. ([https://quay.io/repository/keycloak/keycloak](https://quay.io/repository/keycloak/keycloak))
* `start-dev`: start Keycloak in development mode.
* `-v G:/keycloak:/opt/keycloak/conf`: The directory `G:/keycloak` on the host machine is mounted to `/opt/keycloak/conf` inside the container. This is done to provide configuration files to the container.
* `-net keycloak-network`: This specifies the network the container should be connected to.(`keycloak-network`)
* `-e KC_DB=mysql -e KC_DB_URL=jdbc:mysql://mysql:3306/keycloak?useSSL=false -e KC_DB_USERNAME=keycloak -e KC_DB_PASSWORD=password`: These environment variables are related to the database configuration for Keycloak. It specifies that MySQL will be used as the database, and provides the database URL, username, and password.
* `-e KC_HOSTNAME=localhost`: This sets the hostname for Keycloak to "localhost".
* `start-auto-build -db=mysq`: These are arguments passed to the Keycloak startup command. `start-auto-build` is a custom command to start Keycloak with custom database setup, and `-db=mysq` specifies that MySQL is the database backend.
