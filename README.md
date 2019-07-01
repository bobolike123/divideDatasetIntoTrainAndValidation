# divideDatasetIntoTrainAndValidation
一键将数据集分为训练集和验证集，免去手动操作的烦恼

- 对数据集的布局要求如下：
```
DatasetName
│  
├─category1
│      sample1
│      sample2
│      sample3
│      ...
│      sampleN
├─category2
│      sample1
│      sample2
│      sample3
│      ...
│      sampleN
├─category3
│      sample1
│      sample2
│      sample3
│      ...
│      sampleN
└─categoryN
│      sample1
│      sample2
│      sample3
│      ...
│      sampleN

```

其中`DatasetName`为数据集所在的文件夹,`category1`至`categoryN`为样本的类别，`sample1`至`sampleN`为各类别下的样本

比如数据集是恶意代码文件，那么category可以是恶意代码的家族名，而sample是属于该家族的样本

- 所需参数：`origin_path`,`goal_path`,`divide_ratio`,其中
  - `origin_path`:数据集所在的绝对路径
  - `goal_path`:将划分好后的数据集存放的路径
  - `divide_ratio`:划分出验证集的比例（0-1之间），默认0.2 。 比如0.2表示训练集：验证集= 8 ：2
  - ***注：验证集为随机从数据集中划分出的，调用了random.sample()方法***

- 步骤与效果：
  1.  打开`divideDataset.py`在下面代码中令**yourDatasetPath=origin_path** , **yourGoalPath=goal_path**
  ```
  if __name__ == '__main__':
    yourDatasetPath=''
    yourGoalPath=''
    divide_ration = 0.2 # 默认为0.2 .即以8:2划分训练集和验证集
    runAPP(yourDatasetPath,yourGoalPath,divide_ration)
  ```
  2. 运行runAPP()
  3. 假设origin_path中的目录结构如下：
  ```
  Dogs
  │  
  ├─blackdogs
  │      bdog1
  │      bdog2
  │      bdog3
  │      ...
  │      bdog10
  ├─whitedogs
  │      wdog1
  │      wdog2
  │      wdog3
  │      ...
  │      wdog10
  ├─yellowdogs
  │      ydog1
  │      ydog2
  │      ydog3
  │      ...
  └─     ydog10
  ```
  
  则经过划分后在goal_path形成如下目录结构
  
  (validation为按比例随机划分出的，以下结构仅作为示范例子，divide_ratio=0.2)：
  ```
  Dogs
  └─train
    ├─blackdogs
    │      bdog1
    │      bdog3
    │      ...
    │      bdog10
    ├─whitedogs
    │      wdog2
    │      wdog3
    │      ...
    │      wdog10
    ├─yellowdogs
    │      ydog1
    │      ydog2
    │      ...
    └─     ydog10
  └─validation
    ├─blackdogs
    │      bdog2
    │      bdog8
    ├─whitedogs
    │      wdog1
    │      wdog9
    ├─yellowdogs
    │      ydog3
    └─     ydog6
  ```
  
  **如果代码对你有帮助，希望能点个Star,您的支持将是我前进的动力**
  
  **如有有什么建议或者意见，请联系邮箱：wb516100@163.com**
