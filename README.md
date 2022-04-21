# Challenge-5


## Financial Planning with APIs and Simulations

In this Challenge, I’ll create two financial analysis tools by using a single Jupyter notebook:

Part 1: A financial planner for emergencies. The members will be able to use this tool to visualize their current savings. The members can then determine if they have enough reserves for an emergency fund.

Part 2: A financial planner for retirement. This tool will forecast the performance of their retirement portfolio in 30 and 10 years. To do this, the tool will make an Alpaca API call via the Alpaca SDK to get historical price data for use in Monte Carlo simulations.


---

## Technologies

This project leverages Pandas on Jupyter notebook

---

## Open Guide

Before running the application first open Jupyter lab in terminal:

```
  1. Activate dev environment by: "conda activate dev"
  2. Open Jupyter Notebook by: "Jupyter lab"
```


---

## Usage

To use the analysis simply clone the repository and run the **financial_planning_tools.ipynb** within the Jupyter Notebook.\
*Import the following libraries and dependencies:*

``` python
import os
import requests
import json
import pandas as pd
from dotenv import load_dotenv
import alpaca_trade_api as tradeapi
from MCForecastTools import MCSimulation
%matplotlib inline
```

---

## Part 1: Create a Financial Planner for Emergencies

Evaluate the Cryptocurrency Wallet by using the **Request** Library:
1. Set monthly income to 12000.
2. Use the *requests.get* function to get the current price of Bitcoin (BTC) and Ethereum (ETH) by using the API endpoints.
3. Use *json.dumps* to review the response data from API call, set *indent and sort_key* parameters to make the object readable.
4. Navigate the price of each crypto to access the current price.
5. To compute the current value in each holdings, simply multiple the **price** with **amount**.
6. The total value of crypto wallet will be the sum of **BTC** and **ETH**, which is **$66,430.80**.

Evaluate the Stock & Bond Holding by using the **Alpaca** SDK:
1. Store the **Alpaca API Key** and **Alpaca Secret Key** in a **.env** file.
2. Use *os.getenv* function to generate the keys.
3. Use *tradeapi.REST* to create the object.
4. Set **tickers** to **SPY** and **AGG**, **timeframe** to **1Day**, **start date** and **end date** will both be **2020-08-07**.
5. Use *alpaca.get_bars* function to get current closing prices for **SPY** and **AGG**, including *.df* to make the DataFrame. 
6. Reorganize and concatenate the DataFrame.
7. Access the closing prices for **SPY** and **AGG** by using the *float* function. 
8. To compute the current value in each portion, simply multiple the **price** with **shares**.
9. The total value of the portfolio will be the sum of **SPY** and **AGG**, which is **$60688.7**.
10. The total value of the member's saving portfolio will be the sum of **Total Crypto Wallet** and **Total Stock/Bond Portfolio**, which is **$127,119.50**.

Evaluate the Emergency Fund:
1. Create a DataFrame for the consolidated portfolio for **Total Crypto Wallet** and **Total Stock/Bond Portfolio**. 
2. Plot *pie* chat to visualize the composition. 
![<pie>](<Starter_Code/Images/pie.png>)
3. **Emergency Fund** is **3** times **monthly income** which is 36000.
4. Create a condition statement to see if the **Total Portfolio** is **greater**, **less than** or **equal to** the **Emergency Fund**. A corresponding message will be printed based on each condition. 

*In this analysis, the member has enough money in the fund.*

---

## Part 2: Create a Financial Planner for Retirement

Forecast Cumulative Returns in 30 Years
1. Use 3 years of historical closing prices to predict future returns. Thus, set the **start date** to **2017-08-07** and **end date** to **2020-08-07**.
2. Use *alpaca.get_bars* and *.df* to make API calls and make the calls into a DataFrame. 
3. Reorganize and concatenate the **Stock** and **Bond**.
4. Use *MCSimulation* function to forecast 30 years cumulative returns, 40% to AGG and 60% to SPY in weight. 
5. Review the imput data by *portfolio_data* function.
6. Run the result to see the forecast by *calc_cumulative_return* function.
7. Plot both **line** and **histogram** to visualize the distribution. 

![<30 line>](<Starter_Code/Images/30 line.png>)

![<30 hist>](<Starter_Code/Images/30 hist.png>)
8. Generate the summary by using *summarize_cumulative_return* function.
9. Analyze the forecasts by calculating 95% lower and upper confidence level. 

*There is a 95% chance that a current balance of $60688.7,the stock and bond portion in the portfolio over the next 30 years will end within in the range of $144633.30 and $2308779.34.*

Forecast Cumulative Returns in 10 Years
1. Repeat steps above, but change the weight to 20% AGG and 80% SPY as well as forecasting year to 10. 
2. Plot both **line** and **histogram** to visualize the distribution. 

![<10 line>](<Starter_Code/Images/10 line.png>)
![<10 hist>](<Starter_Code/Images/10 hist.png>)

3. Analyze the forecasts by calculating 95% lower and upper confidence level. 

*There is a 95% chance that a current balance of $60688.7,the stock and bond portion in the portfolio over the next 10 years will end within in the range of $43217.22 and $444467.52.*

---

## Conclusion

*By analyzing both returns in different weights and different years, I can tell that although there's a chance to lose money in 10 years, the risk is far less than investing in 30 years, because 10 years has a standard deviation of 1.66 and 30 years has 10.47.*

---

## Contributors

Feier Ou 

ffeierou1003@gmail.com 

---

## License

Feier Ou 
