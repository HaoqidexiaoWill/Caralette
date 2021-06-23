---
title: Python常用脚本
date: 2020-04-21 16:04:48
tags: JSON读写
---

**Python3 按行读JSON:**

```
SQL_PATH = 'xxx.json'
sql_data = []
with open(SQL_PATH, encoding='utf-8') as inf:
    for idx, line in enumerate(inf):
        sql = json.loads(line.strip())
        if use_small and idx >= 1000:
            break
        sql_data.append(sql)

```

**Python3 按行写JSON：**

```python
import numpy
class NumpyEncoder(json.JSONEncoder):
    """ Special json encoder for numpy types """
    def default(self, obj):
        if isinstance(obj, (numpy.int_, numpy.intc, numpy.intp, numpy.int8,
                            numpy.int16, numpy.int32, numpy.int64, numpy.uint8,
                            numpy.uint16, numpy.uint32, numpy.uint64)):
            return int(obj)
        elif isinstance(obj, (numpy.float_, numpy.float16, numpy.float32,
                              numpy.float64)):
            return float(obj)
        elif isinstance(obj, (numpy.ndarray,)):
            return obj.tolist()
        return json.JSONEncoder.default(self, obj)

    
fw = open(output_path,'a', encoding='utf-8')
for sql_pred in sql_preds:
    json.dump(sql_pred,fw,ensure_ascii=False,cls = NumpyEncoder)
    fw.writelines('\n')
fw.close()
```

