<h1 align="center">stock api</h1>

## 简介

一款聚焦在 `股票实时数据` 和 `周边相关服务` 的接口小助手。

## 股票数据

### 已实现

|   名称   | 接口名  |      搜索股票代码       |      获取股票实时数据       |      获取股票组实时数据       |               官网               |
| :------: | :-----: | :---------------------: | :-------------------------: | :---------------------------: | :------------------------------: |
| 网易财经 | netease | [已实现](#搜索股票代码) | [已实现](#获取股票实时数据) | [已实现](#获取股票组实时数据) | [传送门](https://money.163.com/) |
| 腾讯股票 | tencent | [已实现](#搜索股票代码) | [已实现](#获取股票实时数据) | [已实现](#获取股票组实时数据) |   [传送门](http://gu.qq.com/)    |

### 待实现

|   名称   | 接口名 |      搜索股票代码       |      获取股票实时数据       |      获取股票组实时数据       | 官网                                      |
| :------: | :----: | :---------------------: | :-------------------------: | :---------------------------: | ----------------------------------------- |
|   雪球   | xueqiu | [已实现](#搜索股票代码) | [待实现](#获取股票实时数据) | [待实现](#获取股票组实时数据) | [传送门](https://xueqiu.com/)             |
| 新浪股票 |  sina  | [已实现](#搜索股票代码) | [待实现](#获取股票实时数据) | [待实现](#获取股票组实时数据) | [传送门](https://finance.netease.com.cn/) |

## 安装

```shell
npm install stock-api
```

## 使用

### 接口概览

- [选择数据源](#选择数据源)
- [搜索股票代码](#搜索股票代码)
- [获取股票实时数据](#获取股票实时数据)
- [获取股票组实时数据](#获取股票组实时数据)

### 股票代码

由于每个交易所数据规则不一样，为了能统一规范对代码定义了规则 `交易所+股票代码`。

| 交易所     | 代号 | 实例     |
| ---------- | ---- | -------- |
| 上海交易所 | SH   | SH000001 |
| 深圳交易所 | SZ   | SZ399001 |
| 香港交易所 | HK   | HKHSI    |
| 美国交易所 | US   | USDJI    |

### 选择数据源

##### 可选导入

```typescript
import { stocks } from "stock-api";

// 数据源
const netease = stocks.netease;
const tencent = stocks.tencent;
```

### 搜索股票代码

##### 示例

```typescript
import { stocks } from "stock-api";

// 获取股票组实时数据
stocks.netease.searchStocks(["510500"]).then(console.log);
```

##### 输出

```typescript
[
  {
    code: "SH510500",
    name: "500ETF",
    percent: 0.028383,
    now: 7.174,
    low: 6.93,
    high: 7.184,
    yesterday: 6.976,
  },
];
```

### 获取股票实时数据

##### 示例

```typescript
import { stocks } from "stock-api";

// 获取股票实时数据
stocks.netease.getStock("SH510500").then(console.log);
```

##### 输出

```typescript
{
  code: 'SH510500',
  name: '500ETF',
  percent: 0.028383,
  now: 7.174,
  low: 6.93,
  high: 7.184,
  yesterday: 6.976
}
```

### 获取股票组实时数据

##### 示例

```typescript
import { stocks } from "stock-api";

// 获取股票组实时数据
stocks.netease.getStocks(["SH510500"]).then(console.log);
```

##### 输出

```typescript
[
  {
    code: "SH510500",
    name: "500ETF",
    percent: 0.028383,
    now: 7.174,
    low: 6.93,
    high: 7.184,
    yesterday: 6.976,
  },
];
```
