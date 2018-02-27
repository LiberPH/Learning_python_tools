# Learning_python_tools
Crash research of useful python tools and their comparison with others

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

# Coverage

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

