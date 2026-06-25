# 零售业务SQL数据分析实战项目
## 项目概述
本项目用于数据分析师求职面试，基于**星型模型零售数据集**开发：1张销售订单事实表 + 门店/商品/客户3张维度表，使用 `Python + SQLite + Jupyter Notebook` 完成全套SQL数据分析
所有Notebook代码完全独立解耦，单文件可单独运行

## 技术栈
- 数据处理：Python pandas
- 数据库：SQLite
- 开发环境：Jupyter Notebook
- 标准SQL语法，兼容MySQL/PostgreSQL等主流数据库

## 数据集架构（数仓星型模型）
1. 事实表：销售订单表（交易流水、销量、单价）
2. 维度表：门店信息表、商品信息表、客户信息表
区分事实表、维度表，符合企业数据仓库建模规范

## 仓库目录说明
retail-sql-sqlite-project/
├── 00-init-data.ipynb                    # 数据初始化脚本：Excel导入SQLite生成业务库
├── notebooks/                            # 8个独立分析Notebook（核心代码）
│   ├── 01_overview_agg.ipynb             全量业务指标统计
│   ├── 02_prov_category_group.ipynb      省份+品类营收交叉分析
│   ├── 03_month_trend_lag.ipynb          月度营收环比计算
│   ├── 04_shop_rank_three_window.ipynb   门店好评率三大排名函数
│   ├── 05_customer_tile_ntile.ipynb      用户价值分层分桶
│   ├── 06_customer_exists_high_spend.ipynb EXISTS存在匹配·大额消费客户明细
│   ├── 07_member_pivot_case.ipynb        会员营收行转列透视
│   └── 08_shop_moving_avg_window.ipynb    门店累计&移动平均
├── dataset/
│   └── 零售业务SQL分析数据集_商品名称去品牌.xlsx  # 原始数据源
├── docs/
│   └── 完整项目作品集说明.md              # 完整版业务需求、思路、知识点、结果解读
├── .gitignore                            # 缓存、数据库、系统文件过滤
├── LICENSE
└── README.md


## 8大分析模块
1. `01_overview_agg`：基础聚合函数、UNION ALL、全量数据探查
2. `02_prov_category_group`：多表INNER JOIN、多维度GROUP BY、营收占比计算
3. `03_month_trend_lag`：SQLite日期函数、LAG窗口函数、环比增长率
4. `04_shop_rank_three_window`：PARTITION BY、ROW_NUMBER/RANK/DENSE_RANK排名对比
5. `05_customer_tile_ntile`：NTILE分桶、客户分层运营
6. `06_customer_exists_high_spend`：EXISTS半连接存在性查询、复合排序、多表关联
7. `07_member_pivot_case`：CASE条件聚合、SQL行转列透视表
8. `08_shop_moving_avg_window`：累计求和窗口、移动平均窗口函数

## 一键运行流程
1. 克隆仓库到本地
2. 安装依赖：`pip install pandas openpyxl jupyter sqlite3`
3. 启动Jupyter Notebook
4. 优先运行 `01_init_data.ipynb`，自动生成 `retail_sales.db` 数据库
5. 打开任意notebooks内文件，单独执行，脚本互不依赖

## 项目核心亮点
1. 遵循标准数仓星型建模，清晰区分事实表、维度表，体现数据建模思维；
2. 所有Notebook完全独立，无需依赖其他脚本，代码解耦规范；
3. 无不规范写法，全部使用标准可移植SQL；
4. 每段SQL配套业务背景、解题思路、结果业务解读，不单纯堆砌语法；
5. 覆盖聚合、多表关联、子查询、CTE、全套窗口函数等面试核心内容；
6. 完整可复现：原始数据+入库代码+分析代码全套提供，面试官可本地复现效果
