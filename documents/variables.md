# Packer Variables

We are going to discuss differenct ways to make use of [variables](https://www.packer.io/docs/templates/user-variables.html) in packer configurations, this allows you to parameterize your templates.

1. parameters from console or using values part of the template.

`-var` for single parameter of `-var-file` for a file _(json type parameter file)_

__VAR__

```
$ packer build \
    -var 'aws_access_key=YOUR_ACCESS_KEY' \
    -var 'aws_secret_key=YOUR_SECRET_KEY' \
    template.json
```
_warning_ If you are calling Packer from cmd.exe, you should double-quote your variables rather than single-quoting them. For example:

`packer build -var "aws_secret_key=foo" template.json`


__VAR FILE__

```
On Linux :
$ packer build -var-file=variables.json template.json

On Windows :
packer build -var-file variables.json template.json

```


2. using `environment` variables. use `export` to set the values

