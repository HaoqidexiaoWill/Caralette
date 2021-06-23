---
title: Linux常用命令
date: 2020-04-21 11:55:28
tags: Linux 常用命令
---

**SCP 远程拷贝：**scp + 本地目录 + 远程服务器目标地址

```
scp -r DATA/ liusongyan.2020@10.22.145.137:/data00/home/liusongyan.2020/workspace/dingpan_extraction/entity_mine/RelationExtraction/
```

**后台运行：**

```bash
CUDA_VISIBLE_DEVICES=3 nohup python main2.py> ./train0421.log 2>&1 &
```

