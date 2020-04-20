---
title: "Dynamic Pairs Trading strategy for brazilian ETF securities using the Kalman Filter"
author: 
- name: "Lucas S. Macoris"
  affiliation: "PhD Student at Insper - Institute of Research - São Paulo - Brazil"
  email: "Contact: lucassm4@al.insper.edu.br"
output: html_document
---


## Disclaimer

Disclaimer: the contents expressed herein are exclusively designed for educational purposes and does not represent, in any circumstances, the opinion of **Insper - Institute of Research**. This content should not be viewed as a financial advise. For additional information, contact can be made by email: lucassm4@al.insper.edu.br.

## **About this document**

This document is an application of a Pairs Trading Strategy using the Kalman Filter in order to dinamically update the hedge ratios of a pair of assets. This example is based on *Kris Longmore's* post [*"Kalman Filter Example: Pairs Trading in R*"](https://robotwealth.com/kalman-filter-pairs-trading-r/) in [RobotWealth](https://robotwealth.com/).

The first file, `Kalman Filter Backtest`, provides a simple dynamic linear regression by means of Kalman Filter updating. In this sense, we'll proceed by the following steps:

1. Select a bundle of ETF brazilian traded securities;
2. Perform cointegration and unit-root testing in a synthetic pair of ETF traded securities;
3. Perform the pairs trading analysis with each pair; and
4. Compare the results and point to which pairs are the most interesting to trade on.

After that, the second file, `Report`, uses the insights highlighted in the first analysis to provide an automated way to generate hedge-ratios, as well as other important parameters for Long-Short Strategies based on the following steps:

1. Perform a dynamic linear regression in each synthetic pair and generate the series of coefficients;
2. Create a residual series for each synthetic pair and analyze its distribution;
3. Create Threshold rules for entering into Long/Short Operations; and
4. Provide, based on the last trading day information, the 1-step-ahead forecasts for the coefficients of the Long-Short equation, for each synthetic pair.

**Important Remark:** for this second application, I've used downloaded data from the **MetaTrader** server. The reason for that is that it also provide data intraday data (like 1M ticks, for example) that are highly useful for backtesting purposes. In this file, I haven't considered backtesting strategies using intraday data, but the extrapolation from the simple backtesting procedure considered here is straighforward.

Additionally, Yahoo! Finance data may contain some measurement errors. Yahoo! Finance generally offers data with splits and dividends adjustments and therefore may not be the same as the brokerage information. In this sense, recommendations must also be analyzed through technical indicators presented on the brokerage account.