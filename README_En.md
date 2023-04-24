# test_queue_sample
## Introduction
This sample aims to analyze the difference in queue performance between Linux and Windows, and tested three scenarios of different devices, different queues, and the same queue.

### On Linux
* Install oneapi(2023.0.0)
* git clone https://github.com/zhupailiangx/test_queue_sample.git
* cd test_queue_sample/test_queue_sample
* source /opt/intel/oneapi/setvars.sh
* dpcpp test_queue_sample.cpp -o test_queue_sample
* ./test_queue_sample

### On Windows

* Install oneapi(2023.0.0) and Visual Studio

#### Visual Studio IDE
* Open Visual Studio
* Select menu "File > Open > Project/Solution",find "test_queue_sample" folder and select "test_queue_sample.sln"
* Check if include directory contains dpct file path
*  Select menu "Project > Build" ，and view the results

### Different devices
#### Test results on Linux
The following are the test results on opencl:gpu and level_zero:gpu respectively. The cpu results are not displayed here, but can be viewed in the code running results.
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

#### Test results on Windows
The following are the test results on opencl:gpu and level_zero:gpu respectively. The cpu results are not displayed here, but can be viewed in the code running 
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
### Different queues
#### Test results on Linux
```bash
Test with two queues:

queue1 build hash table time=7ms

queue2 build hash table time=7ms
 
```
#### Test results on Windows
```bash
Test with two queues:

queue1 build hash table time=122ms

queue2 build hash table time=132ms
 
```

### The same queue

#### Test results on Linux
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

#### Test results on Windows
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

## Summary
This sample compares the performance difference of building a hash table in three scenarios of different devices, different queues, and the same queue in Linux and Windows systems.
* Under different GPU devices, after creating a hash table for any queue in the Linux system, and then using the queue of the same device to build the hash table later, the time will be greatly shortened, but not in the Windows system.
* Under the same device and different queues, the second table creation time of Linux is very short, and the Windows system still needs to spend the same time as the first time due to the reason of queue reinitialization.
* Under the same queue, it takes a certain amount of time to build the hash table for the first time, and the second time to build the table is very short.\
Finally, on the Linux system, it can be understood that performing the same operation on the same device will improve performance, while Windows requires the same queue to improve performance.
