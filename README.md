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
2) Create dictionary call **sample** with **50** maximum items and timer of **10** seconds. Once the timer is up, the dictionary will be empty. 
```python
>>> sample = CacheLibrary(max_len=50,timer=10)
```
3) Put or replace **'value'** for **'key'** with timer of **10** seconds..
   Users can choose not to set the timer for the key as per second command. If timer is not set, the timer of the dictionary will be used instead.  
```python
>>> sample['key'] = ('value',10)
>>> sample['key'] = 'value'
```
4) Get value of a key in the dictionary.
   Returns value in the form of **('value',time to expiry)** if it is in the dictionary and **False** if not. If the key or dictionary had expired the command will return **False** also.
```python
>>> sample.get('key')
('value',5.9555263519218711)
```
5) Check if the dictionary contains the key **'key'**
   Returns **True** if key is in the dictionary and **False** if not. If the key or dictionary had expired the command will return **False** also.
```python
>>> sample.contains('key')
True
```
6) Delete key **'key'** in the dictionary.
   Returns the key and values **('key','value')** if successful and and **False** if not. If the key or dictionary had expired the command will return         **False** also.
```python
>>> sample.pop('key')
('value',5.9555263519218711)
```
7) Get the time to live (ttl) in seconds of the key.
   If key is not in the dictionary, **False** would be returned.
```python
>>> sample.ttl('key')
5.9555263519218711
```
8) Get all the key and values in the dictionary.
   Would only show keys that have not expired. If dictionary is empty would show **[]**.
```python
>>> sample.CacheValues()
[('key','value')]
```
9) Get all the key and values with the their to live in the dictionary.
   Would only show keys that have not expired. If dictionary is empty would show **[]**.
```python
>>> sample.CacheValuesTime()
[('key','value',5.9555263519218711)]
```

## License

**MIT** licensed library. See [LICENSE](LICENSE) for details.

## Contributing

If you have suggestions for improving, please [open an issue](https://github.com/kevinkevin1987/cache-library/).
