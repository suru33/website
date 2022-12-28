# Postgres Installation

=== "From binaries"

    Download and install binaries from [here](https://www.enterprisedb.com/download-postgresql-binaries)

=== "MacOS homebrew"

    ```shell
    brew install postgresql
    ```

=== "From source"

    === "Download zip"
        Download the source zip from [here](https://www.postgresql.org/ftp/source/)
        ```shell
        # Extract the source
        tar -xvzf postgresql-<VERSION>.tar.gz
        cd postgresql-<VERSION>
        ```

    === "Checkout from git repo"
        Check the tags from  [here](https://git.postgresql.org/gitweb/?p=postgresql.git;a=tags)
        ```shell   
        # Clone the repo (assume you are in ~/dev)
        git clone --depth 1 -b <TAG> https://git.postgresql.org/git/postgresql.git
        cd postgresql
        ```

    Make and Install
    ```shell
    # Check openssl
    which openssl
    
    # Configure the build
    ./configure --with-openssl \
      --with-includes=/usr/local/opt/openssl/include \
      --with-libraries=/usr/local/opt/openssl/lib 
      --prefix $HOME/dev/postgres/pgsql
    
    # Make
    make world
    
    # Install
    make install-world 
    ```

## Configuration

Create `~/dev/postgres` and `~/dev/postgres/pgdata`

### env variables and aliases

```shell
# Postgres config
export PG_HOME="$HOME/dev/postgres"
export PG_LOG_FILE="$PG_HOME/postgres.log"
export PG_DATA="$PG_HOME/pgdata"

# not required for homebrew installation
export PATH="$PG_HOME/pgsql/bin:$PATH"

alias start_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} start"
alias stop_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} stop"
```

### InitDB (create database folder structure)

```shell
initdb ${PG_DATA}
```

### Create user/role

```shell
createuser --interactive --pwprompt
```

### Create database

```shell
createdb -O <user_name> <db_name>
```

### Login to database

```shell
psql -U <user_name> -d <database> [-h <host>] [-p <port>] -a
```
