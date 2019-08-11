<!--
https://pypi.org/project/readme-generator/
https://pypi.org/project/python-readme-generator/
https://pypi.org/project/django-readme-generator/
-->

[![](https://img.shields.io/badge/OS-Unix-blue.svg?longCache=True)]()
[![](https://img.shields.io/pypi/v/django-static-s3.svg?maxAge=3600)](https://pypi.org/project/django-static-s3/)
[![](https://img.shields.io/npm/v/django-static-s3.svg?maxAge=3600)](https://www.npmjs.com/package/django-static-s3)
[![Travis](https://api.travis-ci.org/andrewp-as-is/django-static-s3.svg?branch=master)](https://travis-ci.org/andrewp-as-is/django-static-s3/)

#### Installation
```bash
$ [sudo] npm i -g django-static-s3
```
```bash
$ [sudo] pip install django-static-s3
```

#### How it works
`static/` hard-coded folder

scripts:
+   create full-access user and credentials
+   upload `static/`

hard-coded environment variables names:
+   `AWS_S3_STATIC_BUCKET`
+   `AWS_S3_STATIC_USER`
+   `AWS_S3_STATIC_ACCESS_KEY_ID`
+   `AWS_S3_STATIC_SECRET_ACCESS_KEY`

#### Scripts usage
command|`usage`
-|-
`static-s3` |`usage: static-s3 command [args]`
`static-s3-create-bucket` |`usage: static-s3-create-bucket bucket`
`static-s3-create-env` |`usage: static-s3-create-env bucket`
`static-s3-upload` |`usage: static-s3-upload`

#### Examples
`Makefile`, create env
```bash
STATIC_BUCKET:=BUCKET_NAME
all:
    test -s .env.s3.static || static-s3-create-env $(STATIC_BUCKET) > .env.s3.static
```

upload `static/` to S3 
```bash
set -o allexport
. .env.s3.static || exit

export DJANGO_SETTINGS_MODULE=settings.dev

thon manage.py collectstatic --no-input
static-s3-upload
```

<p align="center">
    <a href="https://pypi.org/project/django-readme-generator/">django-readme-generator</a>
</p>