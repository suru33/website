# Postgres Installation

=== ":octicons-file-binary-16: From binaries"

    :fontawesome-solid-download: and install binaries from [here](https://www.enterprisedb.com/download-postgresql-binaries)

=== ":simple-apple: MacOS homebrew"

    ```shell
    brew install postgresql
    ```

=== ":material-text-box-outline: From source"

    === ":fontawesome-solid-file-zipper: Download zip"
        :fontawesome-solid-download: the source zip from [here](https://www.postgresql.org/ftp/source/)
        ```shell
        # Extract the source
        tar -xvzf postgresql-<VERSION>.tar.gz
        cd postgresql-<VERSION>
        ```

    === ":simple-git: Checkout from git repo"
        Check the tags from [here](https://git.postgresql.org/gitweb/?p=postgresql.git;a=tags)
        ```shell   
        # Clone the repo (assume you are in ~/dev)
        git clone --depth 1 -b <TAG> https://git.postgresql.org/git/postgresql.git
        cd postgresql
        ```

    Make and Install
    ```shell
    # Check openssl
    which openssl
    
    SSL_DIR="<ssl libs dir>" 
    # for home brew you can get it using `brew --prefix openssl@1.1` 

    # Configure the build
    ./configure --with-openssl \
      --with-includes=${SSL_DIR}/include \
      --with-libraries=${SSL_DIR}/lib \
      --prefix $HOME/dev/postgres/pgsql
    
    # Make
    make world
    
    # Install
    make install 
    ```

## Configuration

Create `~/dev/postgres` and `~/dev/postgres/pgdata`

### env variables and aliases

```shell title="Postgres config"
export PG_HOME="$HOME/dev/postgres"
export PG_LOG_FILE="$PG_HOME/postgres.log"
export PG_DATA="$PG_HOME/pgdata"

export PATH="$PG_HOME/pgsql/bin:$PATH" # (1)

alias start_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} start"
alias stop_postgres="pg_ctl -D ${PG_DATA} -l ${PG_LOG_FILE} stop"
```

1. :man_gesturing_no: not required for homebrew installation

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
