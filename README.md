# test_queue_sample
## 引言
这个示例旨在分析Linux和windows上queue性能不同，分别测试每个计算单元建立哈希表的时间并分析和系统的关系。

### 在Linux系统上
* Install oneapi(2023.0.0)
* git clone https://github.com/zhupailiangx/test_queue_sample.git
* cd test_queue_sample/test_queue_sample
* source /opt/intel/oneapi/setvars.sh
* dpcpp test_queue_sample.cpp -o test_queue_sample
* ./test_queue_sample

### 在 Windows 系统上
* 安装oneapi(2023.0.0) 和 Visual Studio

#### Visual Studio IDE
* 打开 Visual Studio
* 选择菜单 "File > Open > Project/Solution",找到"test_queue_sample"文件夹和选择"test_queue_sample.sln"
* 检查包含目录是否包含dpct文件路径
* 选择菜单 "Project > Build" ，然后执行代码
     


### Linux 上测试结果
下面分别是在opencl:gpu和level_zero:gpu上的测试结果
```bash
Device: opencl:gpu
Queue: 0
 build hash table time=60ms

Queue: 1
 build hash table time=7ms

Queue: 2
 build hash table time=7ms

Queue: 3
 build hash table time=7ms
 
...

____________________________________________

Device: ext_oneapi_level_zero:gpu
Queue: 0
 build hash table time=57ms

Queue: 1
 build hash table time=7ms

Queue: 2
 build hash table time=7ms

Queue: 3
 build hash table time=7ms

...

```
### Windows上测试结果
下面分别是在opencl:gpu和ext_oneapi_level_zero:gpu上的测试结果
```bash
Device: opencl:gpu

Queue: 0
 build hash table time=151ms

Queue: 1
 build hash table time=140ms

Queue: 2
 build hash table time=136ms

Queue: 3
 build hash table time=137ms
 
...

____________________________________________

Device: ext_oneapi_level_zero:gpu
Queue: 0
 build hash table time=149ms

Queue: 1
 build hash table time=153ms

Queue: 2
 build hash table time=143ms

Queue: 3
 build hash table time=150ms

...

```
## 总结
本示例对比了linux 和Windows系统GPU设备queue建立哈希表的性能区别。结果表明，在同一个GPU设备下，Linux系统任意queue建立哈希表之后，后面再使用同一个设备的queue建立哈希表，时间会大大缩短，而Windows系统则不行。
