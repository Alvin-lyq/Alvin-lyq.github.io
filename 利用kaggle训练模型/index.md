# 利用kaggle训练模型


本文介绍如何利用kaggle上免费的GPU资源训练模型.

<img src="https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681976502.jpg" alt="v2-0b52e2b5ccc433a4d0965f2ba1672d8f_1200x500" style="zoom: 50%;" />

<!--more-->

## 每周限额

官方提供每周30hGPU、30hTPU

**GPU**

![image-20230420154512047](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681976712.png)

**TPU**

![image-20230420154545458](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681976745.png)

## 具体步骤

### 1.创建notebook
![1](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977128.png)
类似于jupyter notebook的写法
![2](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977141.png)

 1. 点击保存版本，每个版本可在独立保存
 2. 添加数据集 ----------- '/kaggle/input'
 3. 运行结果（输出）-------------------'./'
 4. 使用语言选择 
 5. 是否使用加速器（GPU、TPU）
 6. 运行(结束)这个notebook
 7. 查看在运行的环境
 8. 控制台
 ==注意输入路径和输出路径==


```python
'/kaggle/input' #输入
'./'            #输出
```

### 2.保存输出
![3](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977155.png)
选择Save&Run All 会运行notebook全部代码，保存输出结果
![4](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977169.png)
保存输出、选择加速器
![5](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977183.png)

### 3.下载输出
![6](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977204.png)
![7](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977219.png)
![8](https://raw.githubusercontent.com/Alvin-lyq/picture/main/2023/04/upgit_20230420_1681977242.png)

 1. 此版本代码
 2. 输入、输出
 3. 运行日志
 4. 选择版本

