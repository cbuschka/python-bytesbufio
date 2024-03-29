# Python package bytesbufio
[![Sources](https://img.shields.io/badge/sources-github-blue)](https://github.com/cbuschka/python-bytesbufio) ![Written in Python](https://img.shields.io/badge/python-3.6,%203.7,%203.8,%203.9-blue.svg) [![PyPI](https://img.shields.io/pypi/v/bytesbufio)](https://pypi.org/project/bytesbufio/) [![Build](https://github.com/cbuschka/python-bytesbufio/workflows/build/badge.svg)](https://github.com/cbuschka/python-bytesbufio/actions) [![codecov](https://codecov.io/gh/cbuschka/python-bytesbufio/branch/master/graph/badge.svg)](https://codecov.io/gh/cbuschka/python-bytesbufio) [![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/cbuschka/python-bytesbufio/blob/master/license.txt)

### bytesbufio provides BytesBufferIO - an io.BytesIO implementation whose value can be accessed after it has been closed

* [Test that shows the problem](./tests/bytesio_test.py)
* ["Fixed" implementation - BytesBufferIO](./bytesbufio/bytes_buffer_io.py)

## Installation
```
pip install bytesbufio
```

## Usage

```python
import io

from bytesbufio import BytesBufferIO

bytesbuf = BytesBufferIO()
with io.TextIOWrapper(bytesbuf, encoding='utf-8') as textout:
    textout.write("Hello world.")

text = bytesbuf.getvalue().decode('utf-8') # BytesIO would have raised an ValueError here 
print(text)
```

## Related
* [Python Issue 22003 - BytesIO and shared bufferes](https://bugs.python.org/issue22003)
* [Python Issue 23099 - value not available after close](https://bugs.python.org/issue23099)

## License
Copyright (c) 2020 by [Cornelius Buschka](https://github.com/cbuschka).

[Apache License, Version 2.0](./license.txt)
