## pip install from git

```shell
# from commit
pip install git+git://github.com/aladagemre/django-notification.git@2927346f4c513a217ac8ad076e494dd1adbf70e1

# from branch
pip install git+git://github.com/aladagemre/django-notification.git@cool-feature-branch

# from branch source bundle
pip install https://github.com/aladagemre/django-notification/archive/cool-feature-branch.tar.gz

# from tag
pip install git+git://github.com/aladagemre/django-notification.git@v2.1.0

# from tag source bundle
pip install https://github.com/aladagemre/django-notification/archive/v2.1.0.tar.gz

```

## Update all python packages

```shell
pip3 list --format=freeze | cut -d'=' -f 1 | xargs -n1 pip3 install --upgrade
```

## Create virtual env

```shell
python3 -m venv .venv
```
