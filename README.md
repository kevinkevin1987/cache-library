# cache-library
cache-library is a Python caching library. It creates an ordered dictionary with an user defined maximum lenght and values that automatically expires when the timer is up. The dictionary and values can expires at different time but the values maximum timer is the timer of the dictionary. During expiration the object is locked during cleanup. If the dictionary is full, the oldest value is deleted,

## Supported python versions

* at leasts 2.7

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
'value',5.9555263519218711
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
## Design considerations
1) Local caching vs network/cloud caching
Local caching has the advantage of being fast, as it does not require any access to a remote cache over the network. Using network/cloud based chaching would cause the network speed to slow down the speed of chaching
2) Maximum items available for the caching
The ideal case would be infite number of item space in the dictionary but in real life the space available for caching is limited by the amound of system memory available. Having a large size cache can fill up the entire system memory, causing the system to kill the process of shut down the whole operating system if the system memory is used up.
3) Timer using time-to-live (TTL) for expiring cache and items in cache
To reduce the memory usage of cache and preventing it from filling up and using up all the item space, a timer need to be set for the cache and the items in the cache to remove items to clear space for new items.
4) Policy to expire items in cache
The cache created is designed to expire that least recently used (LRU) items in the cache if the cache is full. This will happen even if the items have not reach its ttl for expiry.

## License

**MIT** licensed library. See [LICENSE](LICENSE) for details.

## Contributing

If you have suggestions for improving, please [open an issue](https://github.com/kevinkevin1987/cache-library/).
