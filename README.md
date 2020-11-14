# Trend_Analysis

美股数据可以从Yahoo Finance的api获取，使用教程为:https://github.com/ranaroussi/yfinance

画K线图的包叫mplfinance, 教程为 https://github.com/matplotlib/mplfinance

利用pandas_datareader的包可以快速从yahoo finance获取daily的股票数据

以上三个包均可直接pip install 安装

除了一般的K线、Moving Average线、Trading Volume的Bar Chart以外，我们还可以在mplfinance画出的图上自定义添加内容（如直线、斜线、标记等），只需标记位置即可

示例如下：
![Image](https://github.com/YZhang0303/Trend_Analysis/blob/main/AAPL_candle_line.jpg?raw=True)

具体见Trend Analysis_base.ipynb



