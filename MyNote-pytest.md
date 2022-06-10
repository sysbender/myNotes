# MyNote-pytest


# python type-check

```
parameter : type
return: -> type:


# union

from typing import union

# not useful
def get（id: int) -> Union[Foo, Bar]:
def get（id: int) ->Optional[Foo]:
def get（id: int) ->Union[Foo, None]:


# A ny

```



### model:

array - setup, the conditions for the test
act - calling some function or method
assert - that some end condition is true


```
# test_with_pytest.py

def test_always_passes():
    assert True
    
def test_always_fails():
    assert False
    
```

## test result
* the system state - python and pytest version
* the rootdir to search under for configuration and tests
* the number of tests the runner discovered
* 
* dot - pass
* F - failed
* E - raised an unexpected exception


## state and dependency management

* implicit - setUp() and tearDown()
* explicit - fixture

fixture 
- are functions that create data or test doubles or initialize some system state for the test suite.
- Any test that wants to use a fixture must explicitly accept it as an argument


> aa

## Test Filtering

* Name-based '-k'
* Directory scoping
* Test categorization '-m', create marks or custom labels

## Test Prametrization

input and output are different, but test code are the same.


## Plugin-Based Architecture


# pytest tutorial


https://www.youtube.com/watch?v=ujkRo8cpdBA&list=PL_ppFIFzf4EFbnx9VvOjqAdjJRDh-HAxK&index=6

## Fixture

* setup and teardown
* available in 
    * file
    * direcotory and subdir - conftest.py
    * two way of using fixture
        * pass as a parameter
        * use @pytest.mark.userfixtures("fixtuer_name")
            * not get the return
    * return data from fixture



### fixture scope
* function - default scope if not specify
* module
* class
* package
* session


### pytest_namespace 

inject names into pytest's namespace during pytest_configure

```
import pytest
def pytest_configure():
    pytest.my_symbo = 'abc'

```

# advanced pytest

 
Floris Bruynooghe - The hook-based plugin architecture of py.test


https://www.youtube.com/watch?v=dYpfIz219vs

# abridged metaprogramming classics

https://github.com/obestwalter/abridged-meta-programming-classics






# simplify Your tests with Fixtures

https://www.youtube.com/watch?v=ErS0PPfLFLI


fixture is depency injection.
two way to inject:
* as a parameter
* as decorator


### what do these things have in common?
* context manager  - open/close file
* decorator
* fixture  - before/after test

"do something before/do something after" problem in different contexts


### fixture command line

```
pytest --fixtures # show all
pytest --fixtures-per-test

pytest --setup-plan  # show what would be done
pytest --setup-only     # run the fixture but not the tests
pytest --setup-show    # run tests and show fixture setup/teardown

```




# Automated testing with pytest and fixtures

https://www.youtube.com/watch?v=8mp_1Jt-xHQ



# reference

http://docs.pansaifei.com/python-pytest/contents.html

