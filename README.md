<p align="center">
  <img src ="https://github.com/msincenselee/vnpy/blob/master/huafu_on_premise.jpg"/>
</p>


# “当你想放弃时，想想你为什么开始。埃隆·马斯克”

###Fork版本主要改进如下
1、 事件引擎，增加运行效率调试功能

2、 增加rabbitMQ通信组件

3、 增加tdx 免费数据源,包括

    
     - 提供主力合约/指数合约的信息获取
     - 提供期货/股票数据bar 和分笔成交数据下载
     - 提供每日增量更新期货数据=> csv文件，可配合NFS+Celery，实现分布式回测
     
4、 增加App: tick_recorder, 直接异步写入csv文件

5、 增加App: index_tick_publisher, 订阅通达信指数行情=》rabbit_mq 推送

6、 增强ctp_gateway，包括:

    
    - 提供指数行情订阅
    - 使用RabbitMQ指数源，或tdx单一数据源    
    - 提供自定义合约功能，实时提供其合成后的tick行情

7、 增加component组件，包括:


    - 提供cta_line_bar k线组件，支持国内文华/交易师/TB等分钟/小时的计算模式，支持任意秒/分钟/小时/天/周等周期，支持k线数据实时生成。
    - 提供cta_renko_bar k线组件，支持x跳动/千分比跳动 【特定开源对象】
    - 提供cta_fund_kline 资金曲线组件，策略实例/账号基本的实时资金曲线 【特定开源对象】
    - 提供cta_position 组件，支持多/空/净仓位记录，支持套利
    - 提供cta_policy 组件，持久化复杂的策略执行逻辑
    - 提供cta_period 组件，支持策略中‘周期’的逻辑
    - 提供cta_grid_trade组件，支持网格交易、复杂的策略持仓逻辑、持久化 

8、 增加App: cta_strategy_pro，包括：

  
    - 提供策略实例的单独日志记录文件
    - 去除统一的策略数据持久化功能，改为策略内部自行实现。
    - 去除加载k线/tick初始化服务，改为策略内部自行实现。
    - 提供单独重启某一策略实例功能，可在线更新策略源码后，重启某一策略实例，不影响其他运行实例。
    - 支持单策略多合约行情订阅，支持指数合约行情订阅
    - 提供组合回测引擎，能够直接加载cta_strategy_pro_setting.json文件进行组合回测。
    - 拆分组合回测引擎和回测引擎，组合回测引擎支持bar/tick级别的组合回测
    - 增加定时器，推动策略on_timer
    - 增加定时推送策略持仓event
    - 增加CtaPro模板，支持精细化策略持久模板，
    - 增加CtaPro期货模板，支持FAK委托，自动换月等
    - 增加CtaSpread模板，支持FAK正套/反套
    - 增加Spread组合引擎tick级别回测，支持多策略实例得套利共享账号回测。
    
9、  增强主引擎，包括：

    - 支持同一类gateway，多个接入配置
    - 增加获取当前价格接口
    - 增加风控引擎入口 self.rm_engine
    - 增加算法引擎入口，支持自定义套利合约得手工/程序化交易转移至算法引擎实现
    
10、增加App: account_recorder， 包括：
    
    - 异步更新账号资金/委托/成交信息至Mongo数据库
    - 异步更新策略持仓数据至Mongo数据库
    - 异步查询股票历史委托/历史成交至Mongo数据库 

11、算法引擎


    - 支持自定义套利合约得算法，及算法下单。
    - 可通过vnpy界面/cta_strategy_pro策略，直接发出套利单，由算法引擎执行
    
12、 增加App: cta_crypto，包括：
    
    - 增加币安合约交易vnpy.gateway.binancef，支持每个合约独立杠杆比率
    - 增肌币安合约数据接口 vnpy.data.binance.binance_future_data
    - 独立的CTA引擎 cta_crypto，运行数字货币时，替代原版cta_strategy引擎。
    - 支持bar方式回测/组合回测
    - 增强期货交易模板
  
大佳
QQ/Wechat：28888502


--------------------------------------------------------------------------------------------
#  原版 vn.py - 基于python的开源交易平台开发框架
https://github.com/vnpy/vnpy
--------------------------------------------------------------------------------------------
### License
MIT
