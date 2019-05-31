---
title: python3
date: 2019-05-31 15:56:13
tags:
---

## Compression
### 1. compress

```
import zlib

...
zlib.compress(str.encode("utf-8"))
// compress requires byte
```

### 2. decompress

```
import zlib

...
zlib.compress(byte).decode("utf-8")
```

### 3. Dynamodb Binary

```
from boto3.dynamodb.types import Binary

# dynamodb.Binary Obj has attr: value
if isinstance(Item[column_name], Binary):
	box_plot_str = zlib.decompress(Item[column_name].column.value).decode("utf-8")
```

## Json
json -> str

```
json.dumps()
```

str -> json

```
json.loads()
```

## File

```
file.open('sample.txt', 'w')
file.write()
file.close()
```