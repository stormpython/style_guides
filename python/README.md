# Python Style Guide

* [PEP8 Style Guide for Python Code](http://legacy.python.org/dev/peps/pep-0008/)
* [The Hitchhiker's Guide to Python!](http://docs.python-guide.org/en/latest/)

**PEP 8** is the de-facto code style guide for Python.

Conforming your Python code to PEP 8 is generally a good idea and helps make 
code more consistent when working on projects with other developers. There is a 
command-line program, pep8, that can check your code for conformance. Install it 
by running the following command in your Terminal:

```bash
$ pip install pep8
```

Then run it on a file or series of files to get a report of any violations.

```bash
$ pep8 optparse.py
optparse.py:69:11: E401 multiple imports on one line
optparse.py:77:1: E302 expected 2 blank lines, found 1
optparse.py:88:5: E301 expected 1 blank line, found 0
optparse.py:222:34: W602 deprecated form of raising exception
optparse.py:347:31: E211 whitespace before '('
optparse.py:357:17: E201 whitespace after '{'
optparse.py:472:29: E221 multiple spaces before operator
optparse.py:544:21: W601 .has_key() is deprecated, use 'in'
```
