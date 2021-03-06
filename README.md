# Learning_python_tools
Crash research of useful python tools and their comparison with others
---
# pytest
 * In contrast to unittest, it proposes the use of tests as plain python functions, instead if using large test classes.
 * Makes it easy to write small tests
 * Simply by calling 'pytest', it will search and run all files of the form test_*.py or *_test.py in the current directory and its subdirectories.
 * pytest can be run through the pyton interpeter, there the tests to be run or the directory  where we want to explore them
 can be established. also, we can choose tests by expressions:
 ```
 pytest -k "MyClass and not method"
 ```
 * Still, you can make your testing classes with pytest XD and see intermediate values to find the failures. 
```pyhton
 # content of test_class.py
class TestClass(object):
    def test_one(self):
        x = "this"
        assert 'h' in x

    def test_two(self):
        x = "hello"
        assert hasattr(x, 'check')
```

### Sources
* https://www.slant.co/versus/9148/9149/~unittest_vs_pytest
#### To get strated
* https://docs.pytest.org/en/latest/getting-started.html#install-pytest
#### Conventions for Python test discovery and good integration practices:
* https://docs.pytest.org/en/latest/goodpractices.html#test-discovery
---
# coverage

Coverageis typically used to assess the effectiveness of tests. It can show which parts of your code are being exercised by tests, and which are not.
To run the previously created examples in pytest I used:
```
python2.7 -m coverage run --source=./ -m pytest 
```
And to run its report:
```
 python2.7 -m coverage report
```
Which resulted in:
```
Name              Stmts   Miss  Cover
-------------------------------------
test_class.py         7      0   100%
test_sysexit.py       6      0   100%
-------------------------------------
TOTAL                13      0   100%

```
with **--omit**, the chosen paths can be omitted from the coberture report (for example the coberture of the tests themselves maybe useless, we want the coberture of their underlying classes and functions.

### Sources
* https://coverage.readthedocs.io/en/coverage-4.5.1/
---
# flake8
* Is a modular source code checker
* It is a linter tool that helps to prevent bugs in your program.
* It is known as “the wrapper which verifies pep8, pyflakes and circular complexity “. It has low rate of false positives.
* Flake8 is a wrapper around these tools:
- PyFlakes
-  pycodestyle
-  Ned Batchelder’s McCabe script
* Example:
```python
 flake8 test_sysexit.py 
test_sysexit.py:3:1: E302 expected 2 blank lines, found 0
test_sysexit.py:6:1: E302 expected 2 blank lines, found 1
```
### Sources
* https://medium.com/python-pandemonium/what-is-flake8-and-why-we-should-use-it-b89bd78073f2
* http://flake8.pycqa.org/en/latest/
---

# cookiecutter

* Creates a Python package project from a Python package template O.o
* Es tricky de usar
* ¿Vale la pena usarlo si no necesariamente todos nuestros proyectos se van a justar a un template?

#### Sources 
* https://github.com/audreyr/cookiecutter
* http://cookiecutter.readthedocs.io/en/latest/first_steps.html

---
# tox

 Is a tool to pack and test python projects.
 tox runs a virtual environment :D.
 
 ## Requirements
 A tox.ini file must be created in the same path as a setup.py
 
 ### tox.ini
 The tox.ini file contains:
 * The python environment to be used 
```
[tox]
envlist = py27
``` 
 * The dependecies and commands to run in the environment.
 ```
 [testenv]
deps =
	coverage
	pytest-cov
	pytest
	pyspark
	numpy
	pandas
commands =

    py.test --cov-config .coveragerc --cov-report html --cov-report term-missing --cov=src test/ 

 ```
 Whole tox.ini example:
 ```
 [tox]
envlist = py27

[testenv]
deps =
	coverage
	pytest-cov
	pytest
	pyspark
	numpy
	pandas
commands =

    py.test --cov-config .coveragerc --cov-report html --cov-report term-missing --cov=src test/ 


[testenv:py27]
basepython = python2.7

 ```
 ### setup.py
 
 Contains the main data of the things that are being run in the tox environment. it includes the packages being run.
 ```
 from distutils.core import setup

setup(name='Inversiones',
      version='0.1',
      description='AnalyticBaseTable',
      author='Datio: Libertad',
      author_email='lpantoja@datoibd.com',
      url='http://www.datio.com',
      packages=['src','test']
     )
 ```
 ### .coveragerc
 
 Contains the coverage parameters and modifications required, for example any omits that may be needed.
 
 ```
 [run]
omit = */*__init__.py
```

#### Sources
* https://tox.readthedocs.io/en/latest/

* To avoid a setup.py https://www.codesd.com/item/how-do-i-run-tox-in-a-project-that-does-not-have-setup-py.html

---

# behave
* Objective: Use behaviour driven development to encourage collaboration between developers, QA, etc...
* Behavior testing simply means that we should test how an application behaves in certain situations. Often the behavior is given to us developers by our customers. They describe the functionality of an application, and we write code to meet their specifications. Behavioral tests are a tool to formalize their requirements into tests. This leads naturally to behavior-driven development (BDD).
* Behave uses tests written in a natural language style, backed up by Python code.
#### Sources
* https://github.com/behave/behave
* https://semaphoreci.com/community/tutorials/getting-started-with-behavior-testing-in-python-with-behave
