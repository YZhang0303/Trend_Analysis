# Trend_Analysis

美股数据可以从Yahoo Finance的api获取，使用教程为:https://github.com/ranaroussi/yfinance

画K线图的包叫mplfinance, 教程为 https://github.com/matplotlib/mplfinance

利用pandas_datareader的包可以快速从yahoo finance获取daily的股票数据

以上三个包均可直接pip install 安装

除了一般的K线、Moving Average线、Trading Volume的Bar Chart以外，我们还可以在mplfinance画出的图上自定义添加内容（如直线、斜线、标记等），只需标记位置即可

示例如下：
![Image](https://raw.githubusercontent.com/YZhang0303/Trend_Analysis/main/AAPL_candle_line.jpg)

具体见Trend Analysis_base.ipynb


# 如果图片没有正常显示
如果你的github上的图片不显示

解决方法:https://blog.csdn.net/Gladys_Huang/article/details/104360854
修改一下hosts文件即可

### 调参的注意事项（请大家补充）
- 待调参数：【目标函数：突破线后30天内最大涨/跌幅超过20%的概率】
    - 寻找局部最值用的时间窗口
    - 合并各个**相邻峰**所用的标准差倍数
    - 合并**各条线**所用的方法（具体股价区间如2%近90天价差？还是峰附近股价的标准差？如果是标准差那么倍数和时间窗是多少？）
        - 注意第二条和第三条不是一件事！合并相邻峰是为了找important points，把横向相邻的点合并成一个；合并各条线则是已经找好points画好线之后，把纵向相邻的线合并成一条
- 模型流程：
    - 起床，画线
    - 开盘，如果突破，开始跟踪30天
    - 睡觉，要决定今天用过的线是否保留以后再用
- 评价指标：【突破定义为，当日收盘价高于线价3%】
    - #线坚持的时长（period）：之后过了多久股价没有触及该线
    - #触及次数（n）：该点之后股价触及该线的次数，无论是向上或向下【这里有个问题，就是被突破后，再看有没有触及还是否有意义】 #我觉得这两个是不是可以作为参数？
    - 【现在只看这一个】疯狂程度（crazy）：突破后，股价最大上涨的幅度/波动性变动的程度
- 新的要求：
    - 股价突破线后是否回调（折腾）：突破后又回落的不好，找突破后不再回落到箱体内的边沿
    - 更注重“卧薪尝胆”的趋势股（股价几年趴窝，但超过某个点后突然**起爆**不再回头，找的就是这个点），而不是具有短期趋势的震荡股
    - 不能偷看未来数据！！
