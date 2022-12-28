## Check list of authors

```shell
git log --pretty=full | grep  -E '(Author|Commit): (.*)$' | sed 's/Author: //g' | sed 's/Commit: //g' | sort -u
```

## Change history

```shell
git filter-branch --env-filter '
    if [ "$GIT_COMMITTER_EMAIL" = "<OLD AUTHOR EMAIL - 1>" ]; then
        export GIT_COMMITTER_NAME="<NEW AUTHOR NAME>"
        export GIT_COMMITTER_EMAIL="<NEW AUTHOR EMAIL>"
    fi
    if [ "$GIT_COMMITTER_EMAIL" = "<OLD AUTHOR EMAIL - 2 ... >" ]; then
        export GIT_COMMITTER_NAME="<NEW AUTHOR NAME>"
        export GIT_COMMITTER_EMAIL="<NEW AUTHOR EMAIL>"
    fi
' --tag-name-filter cat -f -- --all
```

## Push the code

```shell
git push --force --tags origin 'refs/heads/*'
```