# SSH Key

## Generate SSH key

```shell title="in ~/.ssh directory"
ssh-keygen -t ed25519 -C "your_email@example.com"
```

!!! note "If you are using a legacy system that doesn't support the Ed25519 algorithm, use:"

    ```shell
    ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
    ```

## Ensure the ssh-agent is running

```shell
eval "$(ssh-agent -s)"

## Agent pid 60501
```

## Create SSH config file

``` title="~/.ssh/config"
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

## Add key

=== ":simple-apple: MacOS"

    ```shell
    ssh-add --apple-use-keychain ~/.ssh/id_ed25519
    ```
    !!! info "For older versions of MacOS"
        ```shell
        ssh-add -K ~/.ssh/id_ed25519
        ```

=== ":simple-windows: Windows/:simple-linux: Linux"

    ```shell
    ssh-add ~/.ssh/id_ed25519
    ```
