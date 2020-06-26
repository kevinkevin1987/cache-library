# cache-library
Chacing library for python

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
