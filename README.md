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
```python
>>> from minicache import cache
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
