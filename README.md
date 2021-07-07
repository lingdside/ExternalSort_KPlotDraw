## 实验描述

### 1. 输入数据

**all_us_stock_daily.csv**

| **列名**  | **类型** | **描述**       | **示例**   |
| --------- | -------- | -------------- | ---------- |
| Date      | datetime | 交易日期       | 2013-12-10 |
| Symbol    | string   | 股票代码       | AISA.JK    |
| Open      | float    | 开盘价         | 1420.0     |
| High      | float    | 最高价         | 1440.0     |
| Low       | float    | 最低价         | 1420.0     |
| Close     | float    | 收盘价         | 1430.0     |
| Adj Close | float    | 复权后的收盘价 | 1424.19812 |
| Volume    | float    | 成交量         | 11394000.0 |

**all_zh_stock_daily.csv**

| **列名**          | **类型** | **描述**               | **示例**            |
| ----------------- | -------- | ---------------------- | ------------------- |
| date              | datetime | 交易日期               | 2006-04-20          |
| symbol            | string   | 股票代码               | sh600004            |
| open              | float    | 开盘价                 | 2.94                |
| high              | float    | 最高价                 | 2.94                |
| low               | float    | 最低价                 | 2.88                |
| close             | float    | 收盘价                 | 2.89                |
| volume            | float    | 成交量                 | 7889751.0           |
| outstanding_share | float    | 流动股本               | 476000000.0         |
| turnover          | float    | 换手率=成交量/流动股本 | 0.01657510714285714 |

### 2. 计算涨跌额和涨跌幅：

计算每只股票每日的涨跌额和涨跌幅。计算公式如下：

涨跌额 = 今日收盘价 – 昨日收盘价

涨跌幅 = （涨跌额 / 昨日收盘价）* 100%

将计算出的涨跌额和涨跌幅添加到原来的数据集中，即新增两列，存成文件。

### 3. 外排序：

将每日股票行情数据按照涨跌幅从大到小排列，日期由近及远。即对数据集按照日期和涨跌幅两列进行降序排列，先排日期，最靠近现在的日期排在最前；再对同一日内的所有股票行情按照涨跌幅的降序排列。

### 4. 计算夏普比率：

计算每只股票每年内涨跌幅的平均值和标准差，这里视为股票的年平均收益和标准差，用年平均收益除以标准差计算出该股票该年的夏普比率。

### 5. 输出某月单日涨跌幅最大的k条股票交易数据：

对某一个指定的单月份的数据（已划分好的单月份数据的外部存储），进行外部排序。排序的关键字为涨跌幅 的绝对值，按降序排序。指定单月份后（例如2020年06月），访问读取并排序单月份数据（如2020-06.csv），单日涨跌幅最大的k条股票交易数据。严格限制内存大小（最多使用10M内存空间），通过检查Windows任务管理器的监控内存占用并测试。

### 6. 可视化：

任意选择某时间段（365天）内，夏普比例最高的10只股票，使用QT和外部库画出他们在指定期间（1年）的日K线图。 



## 运行事项

1. 需要打开terminal运行框，接受提示并根据相关提示输入年份或月份
2. 输出的K线图不在运行中show，而在Build文件夹中输出PNG
