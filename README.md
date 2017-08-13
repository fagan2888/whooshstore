Whooshstore
-----------

This is a simple Python module for indexing and searching files
on your local hard drive. It supports incremental indexing, pagination,
and provides an API.

Example CLI usage
=================

```
ws-update -b --index my.idx datadir  # build the index
ws-update -b --append --index my.idx datadir  # incremental update
ws-update --help  # complete command line syntax

ws --index my.idx hello world     # query the index
ws --help  # complete command line syntax
```

Python API
==========

```python
from whooshstore import util, open_index, update_index, search

# Build the index.
ix = open_index('my.idx', False)
files = util.find_files('datadir', ('*.txt',))
update_index(files, ix = ix, incremental = False, batch = True)

# Query.
for result in search('hello world', ix = ix, limit = 20):
    print result
```