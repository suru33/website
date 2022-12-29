# SSH Key

```shell title="in ~/.ssh directory"
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# or the new algorithm
ssh-keygen -t ed25519 -C "your_email@example.com"

eval "$(ssh-agent -s)"
```

## Create SSH config file

``` title="~/.ssh/config"
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

## Add key

=== "MacOS"

    ```shell
    ssh-add -K ~/.ssh/id_rsa # (1)
    # or
    ssh-add --apple-use-keychain ~/.ssh/id_rsa
    ```

    1. -K is deprecated in new versions of MacOS    

=== "Windows/Linux"

    ```shell
    ssh-add ~/.ssh/id_rsa
    ```
