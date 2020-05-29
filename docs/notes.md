# Steps

1. create a repo in github
1. clone to local drive
1. set up the correct file structure

```
package_name
├── docs
│ ├── build
│ ├── make.bat
│ ├── Makefile
│ └── source
├── LICENSE
├── README.md
├── requirements.txt
└── package_name
  └── package_name.py
```

1. install sphinx: `pip install sphinx`
1. install RTD theme: `pip install sphinx-rtd-theme`
1. run: `sphinx-quickstart` and select y to separate source and build
1. add the following extensions to conf.py:

    ```python
    extensions = [
    'sphinx.ext.autodoc',
    'sphinx.ext.viewcode',
    ]
    ```

1. uncomment and edit the following lines at the top of conf.py:

    ```
    import os
    import sys
    sys.path.insert(0, os.path.abspath('../../package_name/'))
    ```

1. if publishing to read the Docs:
   1. change the theme `html_theme = 'sphinx_rtd_theme'`
   1. create a `requirements.txt` file in the package root directory

1. write your docstrings and any edits to the index.rst file
1. change to the `../docs/` directory and run `sphinx-apidoc -f -o ./source ../package_name` which will create a `package_name.rst` file
1. it is good practice to then add an `intro.rst` and `examples.rst` file to the source files.
1. finally `package_name` `intro` and `examples` needed to be added to the `toctree` in `index.rst`

To generate the API docs in html run `make clean` then `make html` from the `../docs/` directory.
```

.. toctree::
:maxdepth: 2
:caption: Contents:

intro
package_name
examples

```

## Guides

[Restructured Text (reST) and Sphinx CheatSheet](https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html)

[A “How to” Guide for Sphinx + ReadTheDocs](https://sphinx-rtd-tutorial.readthedocs.io/en/latest/index.html)

[Mastering Markdown](https://guides.github.com/features/mastering-markdown/)

[Writing your own programming language and compiler with Python](https://blog.usejournal.com/writing-your-own-programming-language-and-compiler-with-python-a468970ae6df)
