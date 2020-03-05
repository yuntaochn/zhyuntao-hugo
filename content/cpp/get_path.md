---
title: "C++ 获取(绝对)路径"
date: 2020-03-05T13:40:59+08:00
draft: false
---

某些情况下，配置文件的相对位置随执行可执行程序的位置而不固定，因此，程序执行过程中，将配置文件的路径转换为绝对路径。
方法若干

###　方法一，利用``/proc/self/exe``链接至当前程序，获取程序的路径，进而得到配置文件或其他文件的绝对路径。

``` cpp
#include <linux/limits.h>
#include <unistd.h>
std::string GetExePath() {
    char result[PATH_MAX];      // PATH_MAX=4096
    size_t count = readlink("/proc/self/exe", result, PATH_MAX);
    std::string base_path = std::string(result, (count>0)?count:0);

    return base_path.substr(0, base_path.find_last_of("/"));
}
```

### 方法二，``std::filesystem::current_path``
需要C++17支持
```c++
#include <iostream>
#include <filesystem>
namespace fs = std::filesystem;
int main()
{
    std::cout << "Current path is " << fs::current_path() << '\n';
}
```

### 方法其他  
待定  
$\cdots$

其他
GetModuleFile()
等