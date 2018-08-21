# gogs_install_application

## Description:

Installs a containerised Go Git Service on a Docker host.

## Behaviour:

**Feature:** Install GoGS
- **Given** the RHEL machine is configured as a Docker host
- **Given** a GoGS Docker image is available from a specified registry
- **Given** a MariaDb image is available from a specified registry
- **Given** MariaDb does not run on the host as a service
- **Given** Docker Compose is installed on the host
- **When** Docker Compose is requested to run the application containers
- **Then** the GoGS container is running
- **Then** the MariaDb container is running with a Named Volume
- **Then** GoGS container is linked to the MariaDb container

## Configuration:

| Variable  | Description  | Default  |
|---|---|---|
| **mysql_root_password**  | MariaDb root password.  | None |
| **mysql_user_password**  | MariaDb user password.  | None |
| **gogs_registry_login** |  Whether login is required for the GoGS Docker registry. |false |
| **gogs_registry** | The GoGS Docker registry hostname. Must end with a forward slash. | docker.io/ |
| **gogs_image_name** | The GoGS image name including tag if required. | gogs/gogs |
| **gogs_http_port** | GoGS http port mappings: HostPort:ContainerPort. | 10080:3000 |
| **mariadb_registry_login** | Whether login is required for the MariaDb Docker registry. | false |
| **mariadb_registry** | The MariaDb Docker registry hostname. Must end with a forward slash | docker.io/ |
| **mariadb_image_name** | The name of the MariaDb image including tags if required. | library/mariadb |
| **mariadb_data** | The path of the MariaDb named volume. | /var/lib/mysql |
| **mariadb_port** | MariaDb port mappings: HostPort:ContainerPort. | 3306:3306 |
