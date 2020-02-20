# npdoc2md

A simple python script for auto-converting numpy-style python docstrings to 
markdown for use with mkdocs, an entire package at a time.

### Installation

For now, `npdoc2md` can be used by cloning this repository:
```
git clone https://github.com/jwlodek/npdoc2md
```
In the future, it will also be available with `pip`:
```
pip install npdoc2md
```

### Usage

Below is the result of running `npdoc2md` with the `-h` flag:
```
usage: npdoc2md.py [-h] [-i IGNORE [IGNORE ...]] [-d] target output

positional arguments:
  target                The path to the target python project or file to
                        convert.
  output                The output directory where the markdown files should
                        be placed.

optional arguments:
  -h, --help            show this help message and exit
  -i IGNORE [IGNORE ...], --ignore IGNORE [IGNORE ...]
                        List of filenames/directories to ignore.
  -d, --debug           Add this flag to print detailed log messages during
                        conversion.
```
Basic usage will require at least a target and output locations that are valid.
```
py npdoc2md.py C:/Users/jwlodek/demo C:/Users/jwlodek/demo_output
```
You can also specify to enable debug printing with `-d`, and files to ignore with `-i` followed
by a list of files. For example to autogenerate [py_cui](https://github.com/jwlodek/py_cui) docs, the following command
is run:
```
py npdoc2md.py ..\..\..\py_cui ..\..\DocstringGenerated -i statusbar.py errors.py
```
which will ignore the `statusbar.py` and `errors.py` files.

The `npdoc2md` script will recursively search the target (if it is a folder) for files ending with the `.py` extension,
and will generate a markdown file for each one not specified in the ignore section.

### Doc Rules

You must follow strict docstring style rules to use npdoc2md:

* Each class, function's docstring must start and end with `"""`, and the initial description must be right after the initial `"""`. Ex: `"""Hello this is a function`
* Use numpy style guidelines for `Classes`, `Functions`, `Methods`, `Attributes`, `Parameters`, `Returns` lists
* The `Returns` list should give a return value name and type with the doc message

### Examples

As stated previously, [py_cui](https://github.com/jwlodek/py_cui) uses npdoc2md to auto-generate documentation to use with `mkdocs`. You may also see the `Npdoc2md.md` file in this repository which was generated by running this script on itself:
```
py .\npdoc2md.py .\npdoc2md.py .\example\.
```

### License

MIT License  
Copyright (c) 2020, Jakub Wlodek