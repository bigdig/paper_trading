# Paper Trading


![image](http://www.github.com/cao6237699/paper_trading/blob/master/data_flow.jpg)

##更新预告
本来就想写一个撮合交易的程序，没想到在实际使用过程中需求不断的产生，那就继续搞下去吧

1、增加资金申请和归还功能，类似于券商的融资融券；

2、增强交易报告中的内容；

3、完善模拟交易页面的功能，例如撤单功能、可用资金/证券的计算，行情查询、定时计算收益；

4、完善交易结果查询页面的功能；

5、完成日K线训练web页面的开发；


## 2020年4月10日更新
1、增加模拟交易系统api连接机制，所有账户在连接交易API时均需要登录；

2、调整系统架构，将所有数据的计算和查询全部放到内存中进行，数据是否持久化，根据setting中的数据持久化模式决定；如果想提高回测效率，请选择手动持久化；

3、修正交易报告中最大回撤统计的错误；

4、修正了其他BUG


## 2020年4月更新
1、增加了开发模式，用于web开发；

2、增加了模拟交易web页面及功能；

3、增加了交易结果查询web页面查询功能；

4、修改了实时模拟成交的默认行情源为pytdx；

5、修订了系统若干BUG；

6、调整了交易结果及报告的函数，使其更易于扩展；



## 2020年3月更新
1、调整系统架构，提高扩展能力，去掉了交易引擎的工作模式，使用独立的回测市场取代回测模式。
完善市场基类的方法和属性，如果想新建立一个模拟交易市场可以仅继承并修改几个属性和方法即可完成。

2、优化了引擎方法；

3、增强了系统错误处理机制；

4、增加账户建立时修改账户参数的功能；

5、修订了系统若干BUG；

6、增强了图形化显示报告及记录的功能；


## 2020年2月更新
1、修复若干BUG

2、增加持仓记录模式

3、完善报表功能


## 2020年1月更新
1、将市场订单撮合放在内存中进行；

2、增加flask config，配合系统启动模式使用；

3、加入控制台命令切换启动模式功能；

4、修改账户模型，将SETTINGS中得参数映射到新建立得账户中，以满足不同账户不同参数的使用需求

5、增加报表功能；

6、修订了若干BUG；


## 安装

### 安装Python

至少Python3.7以上

### 安装mongodb和pymongo

安装好之后将mongodb服务开启

```
pip install pymongo
```

### 安装tushare

安装tushare，并在tushare官网上注册你的账号

```
pip install tushare
```

参考：https://tushare.pro

#### 安装flask

```
pip install flask
```

#### 安装其他依赖

```
pip3 install -r requirements.txt
```

## 配置

### 配置你的setting.py

setting.py 包括了所有模拟交易程序的运行参数。你要自己考虑需要什么样的模拟交易程序


### 配置flask app

根据你的需要修改run.py中的IP地址和端口，及调试模式

## 使用
```
python run.py
```
开始模拟交易吧

## 接口
flask app 只提供了模拟交易服务的接口，需要你自己向这个接口发送不同的请求。
你可以自己用requests或者其他工具写一个url请求模块，把server.py中的接口都封装一下，或者直接使用exampe。
把example文件夹中的pt_api.py文件放入你的量化交易程序，在引入相关函数后，你就可以使用模拟交易程序的功能了。

## 各模块功能

* api

  > 模拟交易程序使用到的api

  * db.py

    > mongodb数据服务类
    
  * pytdx_api.py

    > 封装了pytdx的行情服务模块，主要用来获取市场实时行情
    
  * tushare_api.py

    > 封装了tushare的行情服务模块，主要用来获取市场实时行情

* docs

  > 系统说明文档

* app

  > 使用flask为模拟交易程序提供网络接口

* event

  > 事件引擎类，直接使用了VNPY中的事件引擎类

* example

  > pt_api.py 已经包括了对flask 服务的封装，你可以将pt_api.py放到你的量化交易程序中，import你需要的函数进行使用

* trade

  > 核心模块
  * account.py
  
    > 与账户、持仓、交易记录、订单薄有关的所有函数集合
  
  * data_center.py
  
    > 数据中心，包含web功能常用的行情数据
  
  * market.py
  
    > 交易市场类，里面包含了两种撮合成交的模式，注意根据你的使用需求进行配置
    
  * pt_engine.py
  
    > 程序主引擎
    
  * report_builder.py
  
    > 与报表相关，主要用来生成交易结果报表

* utility

  > 工具箱
  * constant.py
  
    > 常量类，所有的常量都在这里
    
  * errors.py
  
    > 错误类，继承自Exception
    
  * event.py
  
    > 事件引擎使用的所有事件类型
    
  * model.py
  
    > 数据模型类
    
  * setting.py
  
    > 设置
  
## 感谢
https://github.com/markqiu


## 项目参考

[https://github.com/cao6237699/paper_trading.git]
