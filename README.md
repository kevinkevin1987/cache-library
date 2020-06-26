# cache-library
cache-library is a Python caching library. It creates an ordered dictionary with an user defined maximum lenght and values that automatically expires when the timer is up. The dictionary and values can expires at different time but the values maximum timer is the timer of the dictionary. During expiration the object is locked during cleanup. If the dictionary is full, the oldest value is deleted,

## Installation

Install from PyPI:
```
pip install cache-library
```
Or using alternative command:
```
pip install https://github.com/kevinkevin1987/cache-library/archive/master.zip
```
Or from source use:
```
python setup.py install
```

## Supported python versions

* at least 2.7

## Examples

Basic usage
1) Import library
```python
>>> from cache-library import CacheLibrary
```
2) Create dictionary call 'sample' with '50' maximum items and timer of '10' seconds 
```python
>>> sample = CacheLibrary(max_len=50,timer=10)
```
3) Put or replace 'value' for 'key'.
```python
>>> sample['key'] = 'value'
```
4) Get value of a key in the dictionary
   Returns 'value' if it is in the dictionary and False if not. If the key or dictionary had expired the command will return False.
```python
>>> sample.get['key']
'value'
```
5) 
>>> cache.has('key')
False
>>> cache.get('key', default='default')
'default'
>>> cache.update('key', 'value')
>>> cache.get('key')
'value'
>>> cache.disable()
>>> cache.get('key')

## License

**MIT** licensed library. See [LICENSE](LICENSE) for details.

## Contributing

If you have suggestions for improving, please [open an issue or
pull request on GitHub](https://github.com/duboviy/minicache/).
