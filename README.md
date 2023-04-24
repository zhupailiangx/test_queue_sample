# test_queue_sample
## 引言
这个示例旨在分析Linux和windows上queue性能不同，对不同设备、不同queues、相同queue的三种场景分别做了测试。

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
     

### 不同设备测试
|    Linux                                   |     Windows                   |





|  i7-1165G7   |    JIT     | USE_DPL    |  MULTI_TEMPLATE | transform time(ms)  | sort time(ms)   |
|  ----        | ----       | ----       | ----            |  ----               |    ----         |
|  Linux       |    ON      | ON         |     ON          |    **41.6**         |    5.4          |
|              |    ON      | ON         |     OFF         |    40.5             |    5.4          |
|              |    ON      | OFF        |     ON          |    0.001            |    5.4          |
|              |    ON      | OFF        |     OFF         |    0.001            |    5.4          |
|  Windows     |    ON      | ON         |     ON          |    **72.3**         |    **5.4**      |
|              |    ON      | ON         |     OFF         |    **70.9**         |    5.4          |
|              |    ON      | OFF        |     ON          |    0.001            |    5.4          |
|              |    ON      | OFF        |     OFF         |    0.001            |    5.4          |


#### Linux 上测试结果
下面分别是在opencl:gpu和level_zero:gpu上的测试结果，cpu结果不在这里展示他，可以在代码运行结果中查看。
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
#### Windows上测试结果
下面分别是在opencl:gpu和level_zero:gpu上的测试结果，cpu结果不在这里展示，可以在代码运行结果中查看。
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
### 不同queues测试
#### Linux 结果
```bash
Test with two queues:

queue1 build hash table time=7ms

queue2 build hash table time=7ms
 
```
#### Windows 结果
```bash
Test with two queues:

queue1 build hash table time=122ms

queue2 build hash table time=132ms
 
```

### 相同queue测试
#### Linux 结果
```bash
Test with the same queue:
Loop = 1
  build hash table time=7ms

Loop = 2
  build hash table time=7ms

Loop = 3
  build hash table time=7ms

Loop = 4
  build hash table time=7ms

Loop = 5
  build hash table time=7ms
```

#### Windows 结果
```bash
Test with the same queue:
Loop = 1
  build hash table time=132ms

Loop = 2
  build hash table time=3ms

Loop = 3
  build hash table time=3ms

Loop = 4
  build hash table time=2ms

Loop = 5
  build hash table time=3ms
```


## 总结
本示例对比了linux 和Windows系统不同设备、不同queues、相同queue三种场景建立哈希表的性能区别。结果表明：
* 在不同GPU设备下，Linux系统任意queue建立哈希表之后，后面再使用同一个设备的queue建立哈希表，时间会大大缩短，而Windows系统则不行。
* 在相同设备不同queues下，Linux二次建表时间很短，Windows系统由于queue 重新初始化的原因，还需要花费和第一次相当的时间。
* 在相同queue下，都是初次建立哈希表需要花费一定时间，二次建表时间很短。\
最后，Linux系统上的可以理解为相同设备上进行相同操作，则会提高性能，而Windows则需要相同queue，才能提高性能。
