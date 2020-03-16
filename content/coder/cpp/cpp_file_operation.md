---
title: "C++ 文件操作"
date: 2020-03-16T09:46:15+08:00
draft: false
---

文件操作
```cpp
#include <fstream>
#include <iostream>

ofstream fout("output.txt", std::ios::out); // out 清空追加， app追加

fout << "helloworld" << std::endl;
fout.flush(); // 清空缓存，否则没有fout.close()则没有文件或文件为空

fout.close();
```
