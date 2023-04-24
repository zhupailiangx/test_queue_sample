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
     

### 测试结果  
<body link="#0563C1" vlink="#954F72">

<table border=0 cellpadding=0 cellspacing=0 width=936 style='border-collapse:
 collapse;table-layout:fixed;width:702pt'>
 <col width=64 style='width:48pt'>
 <col width=108 span=2 style='mso-width-source:userset;mso-width-alt:3949;
 width:81pt'>
 <col width=113 style='mso-width-source:userset;mso-width-alt:4132;width:85pt'>
 <col width=83 span=2 style='mso-width-source:userset;mso-width-alt:3035;
 width:62pt'>
 <col width=76 style='mso-width-source:userset;mso-width-alt:2779;width:57pt'>
 <col width=100 style='mso-width-source:userset;mso-width-alt:3657;width:75pt'>
 <col width=64 style='width:48pt'>
 <col width=54 style='mso-width-source:userset;mso-width-alt:1974;width:41pt'>
 <col width=83 style='mso-width-source:userset;mso-width-alt:3035;width:62pt'>
 <tr height=20 style='height:15.0pt'>
  <td rowspan=3 height=60 class=xl65 width=64 style='height:45.0pt;width:48pt'>loop</td>
  <td colspan=5 class=xl65 width=495 style='border-left:none;width:371pt'>Linux</td>
  <td colspan=5 class=xl65 width=377 style='border-left:none;width:283pt'>Windows</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td colspan=2 height=20 class=xl65 style='height:15.0pt;border-left:none'>different
  device</td>
  <td colspan=2 class=xl65 style='border-left:none'>different queues</td>
  <td class=xl65 style='border-top:none;border-left:none'>same queue</td>
  <td colspan=2 class=xl65 style='border-left:none'>different device</td>
  <td colspan=2 class=xl65 style='border-left:none'>different queues</td>
  <td class=xl65 style='border-top:none;border-left:none'>same queue</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl65 style='height:15.0pt;border-top:none;border-left:
  none'>opencl:gpu</td>
  <td class=xl65 style='border-top:none;border-left:none'>level_zero:gpu</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue1</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue2</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue</td>
  <td class=xl65 style='border-top:none;border-left:none'>opencl:gpu</td>
  <td class=xl65 style='border-top:none;border-left:none'>level_zero:gpu</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue1</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue2</td>
  <td class=xl65 style='border-top:none;border-left:none'>queue</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl65 style='height:15.0pt;border-top:none'>1</td>
  <td class=xl65 style='border-top:none;border-left:none'>60ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>57ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>57ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>57ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>151ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>149ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>122ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>132ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>132ms</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl65 style='height:15.0pt;border-top:none'>2</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>140ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>153ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>3ms</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl65 style='height:15.0pt;border-top:none'>3</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>136ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>143ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>3ms</td>
 </tr>
 <tr height=20 style='height:15.0pt'>
  <td height=20 class=xl65 style='height:15.0pt;border-top:none'>4</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>7ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>137ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>153ms</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>&nbsp;</td>
  <td class=xl65 style='border-top:none;border-left:none'>2ms</td>
 </tr>
 <![if supportMisalignedColumns]>
 <tr height=0 style='display:none'>
  <td width=64 style='width:48pt'></td>
  <td width=108 style='width:81pt'></td>
  <td width=108 style='width:81pt'></td>
  <td width=113 style='width:85pt'></td>
  <td width=83 style='width:62pt'></td>
  <td width=83 style='width:62pt'></td>
  <td width=76 style='width:57pt'></td>
  <td width=100 style='width:75pt'></td>
  <td width=64 style='width:48pt'></td>
  <td width=54 style='width:41pt'></td>
  <td width=83 style='width:62pt'></td>
 </tr>
 <![endif]>

</table>


## 总结
本示例对比了linux 和Windows系统不同设备、不同queues、相同queue三种场景建立哈希表的性能区别。结果表明：
* 在不同GPU设备下，Linux系统任意queue建立哈希表之后，后面再使用同一个设备的queue建立哈希表，时间会大大缩短，而Windows系统则不行。
* 在相同设备不同queues下，Linux二次建表时间很短，Windows系统由于queue 重新初始化的原因，还需要花费和第一次相当的时间。
* 在相同queue下，都是初次建立哈希表需要花费一定时间，二次建表时间很短。\
最后，Linux系统上的可以理解为相同设备上进行相同操作，则会提高性能，而Windows则需要相同queue，才能提高性能。
