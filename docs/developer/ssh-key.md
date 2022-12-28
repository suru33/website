# SSH Key

```shell
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
# or the new algorithm
ssh-keygen -t ed25519 -C "your_email@example.com"

eval "$(ssh-agent -s)"
```

### SSH config file

```shell
cat ~/.ssh/config

# file content
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```

=== "MacOS"

    ```shell
    ssh-add -K ~/.ssh/id_rsa # -K is deprecated in new versions of MacOS
    
    ssh-add --apple-use-keychain ~/.ssh/id_rsa
    ```

=== "Windows/Linux"

    ```shell
    ssh-add ~/.ssh/id_rsa
    ```
