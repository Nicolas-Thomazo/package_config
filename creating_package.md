# 🚀 Package creation with pip
> How to create a python package 

![Package](img/package.jpeg)

**Table of Contents**

- [Setup config](#setup-config)
- [License](#license)
    + [Why](#why)
    + [How](#how)
- [Package Creation](#package-creation)
  * [Generation](#generation)
  * [Installation](#installation)
  * [(optional) Development mode](#-optional--development-mode)


## Setup config

**pyproject.toml** is now the standard way to create a package in python.
Create this file at the root of your project 

This section declares what are your build system dependencies, and which library will be used to actually do the packaging.
```python 
[build-system]
requires = ["setuptools"]
build-backend = "setuptools.build_meta"
```

Then you can add informations some package information. **Name** and **versions** are mandatory, the rest of it is optional.

The [dynamic](https://setuptools.pypa.io/en/latest/userguide/pyproject_config.html#dynamic-metadata) argument allows specific options. Here we use the **dependecies** option to specify a requirements.txt file for the necessary package for the project. 

```python 
[project]
name = "package_name"
version = "0.1.0"
authors = [
    {name = "Nicolas Thomazo", email = "nicolas.thomazo@outlook.com"},
]
description = "My package description"
readme = "README.rst"
requires-python = ">=3.7"
license = {text = "BSD-3-Clause"}
dynamic = ["dependencies"]

[tool.setuptools.dynamic]
dependencies = {file = ["requirements.txt"]}
```

## License

#### Why

When you release a package you should add a license to your package. A well known open source license is the [MIT License](https://choosealicense.com/licenses/mit/), it is for open source project.

If you don't know how to choose [here](https://choosealicense.com/) is a website to choose a license depending on your project.

#### How

Just add the text of the license in a file name **LICENSE** at the root of your project.

## Package Creation

### Generation

Now you can generate a distributution (tar.gz and .whl in the dist directory) of your package.

First install the [build](https://pypa-build.readthedocs.io/en/latest/) package. 

```python
pip install --upgrade build
```

Then you can install your package by going at the root of your project and typing.

```python
python -m build
```

### Installation

You can give one of the distribution (.whl or tar.gz file) to someone who can use your package by pip install it.

### (optional) Development mode

If you want to work on your package and use as well the modifications you are doing, you can install in your environment the package in an editable mode. This allows you to modify your source code and have the changes take effect without you having to rebuild and reinstall. 

Go to the root of your package and type

```python
pip install --editable .
```
