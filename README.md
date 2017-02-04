Automata
========

Automata is a customized personal assistant module which can be integrated with your python scripts. You can easily plug your own modules with it and that's not even the best part :)


Installation
------------

```
pip install automata
```


Usage
-----

### Example

```python
from automata import automata

ob = automata.Automata()
res = ob.execute('What is the meaning of life?')

print res
```

### Output

```bash
The answer to the ultimate question of life, the universe and everything is 42.
```


It has some pre defined modules like:

1. Telling day, date and time
2. Finding meaning of words
3. Telling meaning of life for the lost souls

To develop your own module, follow the module development guide below.


Module dev guide
----------------


Below are some general guidelines for developing your own module:

1. The name of the python script should always start from ```mod_```. Example ```mod_time.py```
2. It should have a global list named 'KEYWORDS' containing some keywords which will trigger this module. Example for the ```mod_time.py```, the list is something like this ```KEYWORDS = ['what', 'time']```
3. Every module should contain a method names ```run(query='')``` which will receive the input query. Example:
```python
from datetime import datetime

KEYWORDS = ['what', 'date']

def run(query=''):
	return datetime.now().strftime("%Y:%m:%d")
``` 
4. The ```run(query='')``` should return the response generated by it which could be used for further processing.
5. Any processing of the input query should be done in the ```run(query='')``` method.
6. These modules should be places in a single folder and you need to give the path to that module while instantiating the **Automata class**. Example;
```python
from automata import automata

ob = automata.Automata('/Users/testuser/modules')
res = ob.execute('What is the meaning of life?')

print res
```