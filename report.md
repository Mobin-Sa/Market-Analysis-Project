## Report of Project :
# Analysis of Stock Price Behavior Using Monte Carlo Simulation: A Case Study of Apple, Google, and Microsoft (2020–2024)

**Date** : November 7, 2026  
**Author** : Mobin Salou   

<br>

## 1. Abstract

This study analyzes the price behavior of three major technology stocks—Apple, Google, and Microsoft—over the five-year period from 2020 to 2024. Daily price data were obtained from Yahoo Finance, and daily returns were computed. Descriptive analysis revealed that Apple exhibited the highest return and volatility. The correlation matrix indicated strong positive correlations among the three companies. To model future price paths, Monte Carlo simulation based on the Geometric Brownian Motion (GBM) model was employed, generating 1,000 scenarios for each stock. The results showed that Apple had the highest expected return and risk, whereas Microsoft was the least risky option. These findings can assist investors in making informed decisions. The primary limitation was the lack of access to reliable news data for sentiment analysis.

<br>

## 2. Introduction

Financial markets are among the most complex economic systems, whose behavior is shaped by a multitude of economic, political, and psychological factors. Understanding and predicting stock price movements has always been a central challenge for investors, analysts, and financial researchers. In this context, large technology companies hold particular significance due to their substantial weight in market indices. Apple, Google, and Microsoft, as pioneers in this sector, not only influence the stock market but also represent the broader trends of the technology industry.

The primary objective of this study is to analyze the price behavior of these three companies over the five-year period from 2020 to 2024 and to model future probabilities using Monte Carlo simulation. To this end, daily price data were first extracted from Yahoo Finance, and daily returns were calculated. Subsequently, descriptive analysis, correlation assessment, and finally Monte Carlo simulation based on the Geometric Brownian Motion (GBM) model were performed. This approach allows us to better understand past behavior while also outlining plausible future scenarios.

The significance of this research can be explained in two respects: first, it provides a comprehensive analytical framework for evaluating stock risk and return; second, it demonstrates the application of advanced quantitative methods in investment decision-making. The findings of this study can be useful for investors, portfolio managers, and financial researchers.

<br>

## 3. Methodology


### 3.1. Price Data:
Daily price data for three companies—Apple (AAPL), Google (GOOGL), and Microsoft (MSFT)—were extracted from Yahoo Finance using the yfinance library in Python. The study period spans from January 1, 2020, to December 31, 2024 (a full five years). The data include opening price, closing price, daily high and low, and trading volume.

### 3.2. Calculation of Daily Returns:
For each company, daily returns were calculated using the following formula:

$$
R_t = \frac{P_t - P_{t-1}}{P_{t-1}}
$$

where $P_t$ is the closing price of the stock on day $t$. The mean and standard deviation of daily returns were then computed as measures of return and risk, respectively.

### 3.3. Descriptive Analysis:
To gain an initial understanding of the data behavior, the mean, standard deviation, and price trend charts for all three companies were plotted. This analysis reveals which company has higher returns and which bears greater risk.

### 3.4. Correlation Analysis:
To examine the co-movement of the stocks, the Pearson correlation matrix between the daily returns of the three companies was calculated and visualized using a heatmap. The Pearson correlation coefficient is given by:

$$
\rho_{XY} = \frac{\sum_{t=1}^{T} (R_{X,t} - \bar{R}_X)(R_{Y,t} - \bar{R}_Y)}{\sqrt{\sum_{t=1}^{T} (R_{X,t} - \bar{R}_X)^2 \cdot \sum_{t=1}^{T} (R_{Y,t} - \bar{R}_Y)^2}}
$$

### 3.5. Monte Carlo Simulation:
To probabilistically model future prices, the Geometric Brownian Motion (GBM) model was employed. The discrete-time formula of this model is:

$$
S_{t+\Delta t} = S_t \exp \left( \left( \mu - \frac{\sigma^2}{2} \right) \Delta t + \sigma \sqrt{\Delta t} \varepsilon \right)
$$

where $\mu$ is the mean daily return, $\sigma$ is the standard deviation of daily returns, $\Delta t = 1/252$ (one trading day), and $\varepsilon \sim N(0,1)$. Using this formula, 1,000 price paths were generated for each company over a horizon of 252 trading days (one year). The expected return and risk for each company were then computed from the distribution of final prices. It is worth noting that to ensure reproducibility of the simulation results, a fixed random seed (numpy.random.seed(42)) was set before generating the random shocks.

<br>

## 4. Results


### 4.1. Descriptive Statistics:
Daily price data for the three companies—Apple (AAPL), Google (GOOGL), and Microsoft (MSFT)—were extracted for the period from January 1, 2020, to December 31, 2024 (1,258 trading days). The mean and standard deviation of daily returns for each company are presented in Table 1.

**Table 1: Descriptive Statistics of Daily Returns**

|      Company     | Mean Daily Return | Standard Deviation (Risk) |
|       :---       |      :---:        |           :---:           |
|   Apple (AAPL)   |      0.001182     |          0.019956         |
|  Google (GOOGL)  |      0.001022     |          0.020472         |
| Microsoft (MSFT) |      0.000988     |          0.019211         |

**Interpretation:**  
The results indicate that Apple has the highest mean daily return, but it also exhibits the highest volatility (risk). Microsoft has the lowest volatility and is therefore considered a lower-risk option.


### 4.2. Correlation Analysis:
The Pearson correlation matrix between the daily returns of the three companies is presented in Table 2. All correlation coefficients are positive and strong.

**Table 2: Correlation Matrix of Daily Returns**

|    Company   |      AAPL    |      GOOGL     |      MSFT     |
|     :---     |     :---:    |      :---:     |     :---:     |
|   **AAPL**   |   1.000000   |    0.648932    |    0.748327   |
|   **GOOGL**  |   0.648932   |    1.000000    |    0.746182   |
|   **MSFT**   |   0.748327   |    0.746182    |    1.000000   |

**Interpretation:**  
The high correlations among the three companies indicate that they are influenced by common market factors and tend to move in tandem. This poses a limitation for investors seeking diversification.


### 4.3. Monte Carlo Simulation Results:
Using the GBM model and 1,000 scenarios, the expected return and risk for each company over a one-year horizon were calculated (Table 3).

**Table 3: Monte Carlo Simulation Results**

|     Company     |   Expected Return   | Risk (Std. Dev. of Return) | Last Observed Price |
|      :---       |        :---:        |            :---:           |        :---:        |
|   Apple (AAPL)  |       0.418303      |          0.464365          |      248.615784     |
|  Google (GOOGL) |       0.346190      |          0.447580          |      188.316376     |
| Microsoft (MSFT)|       0.343350      |          0.410374          |      415.775696     |

**Interpretation:**  
Apple has the highest expected return, but its risk is also high. Google represents a balanced option, while Microsoft is considered the least risky choice. These results are consistent with the findings of the descriptive analysis. 


**Figures:**  
Figure 1 shows the price trends of the three companies over the 2020–2025 period. Figure 2 displays the correlation matrix as a heatmap. Figure 3 presents the simulated Monte Carlo paths for each company.  

<br>

## 5. Discussion

The results of this study indicate that the three companies—Apple, Google, and Microsoft—exhibited different behaviors in terms of return and risk over the five-year period from 2020 to 2025. Apple, with the highest mean daily return and simultaneously the highest standard deviation, is identified as a high-risk, high-potential option. This finding is consistent with financial expectations, as higher returns are typically associated with accepting greater risk. In contrast, Microsoft, with the lowest volatility, is considered a suitable option for conservative investors.

The correlation matrix revealed that all three companies have strong positive correlations with one another. This high correlation suggests that the stocks of these companies are influenced by common economic and market factors, and therefore, combining them in a portfolio does not provide significant diversification benefits. This is an important consideration for investors seeking to reduce risk through diversification.

The Monte Carlo simulation results were also consistent with the descriptive analysis. Apple had the highest expected return and the highest risk, while Microsoft was the least risky option. These results demonstrate that the GBM model, despite its simplicity, can provide a realistic picture of the probabilistic behavior of prices.

From a practical perspective, this study can assist investors in selecting stocks that align with their risk tolerance. Additionally, correlation analysis can be used to construct more diversified and efficient portfolios. However, it should be noted that financial modeling is always accompanied by uncertainty, and the results of this study should not be interpreted as definitive predictions.

<br>

## 6. Limitations and Future Work


### 6.1. Limitations

Despite its contributions, this study has several limitations that should be considered when interpreting the results:

1. **Lack of access to reliable news data**: Due to limitations in news APIs and the absence of a suitable public dataset for the 2020-2024 period, sentiment analysis was not performed in this study and remains a direction for future work.
2. **Assumption of normal distribution of returns in the GBM model**: The Geometric Brownian Motion model assumes that logarithmic returns follow a normal distribution, whereas in reality, financial returns may exhibit skewness and kurtosis. To address this limitation, GARCH-family models can be employed.
3. **Limited scope to three companies**: This study focuses solely on three large technology companies. Therefore, the results may not be generalizable to the broader market or other industries.
4. **Omission of macroeconomic factors**: Interest rates, inflation, monetary policies, and political events can influence stock prices, but they were not incorporated into this model.

### 6.2. Future Work

For future research, the following directions are suggested:

1. **Incorporating sentiment analysis**: Using reliable news data and advanced natural language processing (NLP) methods such as FinBERT, the impact of news on stock returns can be examined.
2. **Employing more advanced models**: GARCH-family models can be used to model conditional volatility and volatility clustering.
3. **Expanding the scope of the study**: Including more companies from various industries can enhance the generalizability of the results.
4. **Utilizing machine learning and higher-frequency data**: Machine learning algorithms such as random forests and neural networks can be applied to predict returns and identify complex patterns. Additionally, using higher-frequency data (e.g., hourly or minute-level) can improve the accuracy of the analysis.

<br>

## 7. References


Black, F., & Scholes, M. (1973). The pricing of options and corporate liabilities. Journal of Political Economy, 81(3), 637–654.

Harris, C. R., Millman, K. J., van der Walt, S. J., Gommers, R., Virtanen, P., Cournapeau, D., ... & Oliphant, T. E. (2020). Array programming with NumPy. Nature, 585(7825), 357–362.

Hull, J. C. (2018). Options, futures, and other derivatives (10th ed.). Pearson.

Markowitz, H. (1952). Portfolio selection. The Journal of Finance, 7(1), 77–91.

McKinney, W. (2010). Data structures for statistical computing in Python. Proceedings of the 9th Python in Science Conference, 51–56.

Merton, R. C. (1973). Theory of rational option pricing. The Bell Journal of Economics and Management Science, 4(1), 141–183.

Yahoo Finance. (n.d.). Historical stock data for AAPL, GOOGL, and MSFT. Retrieved from https://finance.yahoo.com

<br>

## 8. Appendix


**Appendix A :** Complete Project Code (available in `analysis.ipynb`).

**Appendix B :** Correlation Matrix of Daily Returns for the Three Companies.

**Appendix C :** Explanation of the Geometric Brownian Motion (GBM) Model and Monte Carlo Simulation Formula.

<br>

## Appendix A: Complete Project Code and Mathematical Formulae

The complete Python code for this project is provided in the Jupyter notebook `analysis.ipynb`. The notebook sequentially implements each step of the analysis, and the following mathematical formulations underpin the computations performed in the code. The notebook is designed to be executed sequentially in a `Python 3.12` environment with the following libraries installed: `pandas`, `numpy`, `matplotlib`, `seaborn`, and `yfinance`.     

### A.1. Daily Returns

For a given asset with closing price $P_t$ on day $t$, the daily return $R_t$ is calculated as :

$$
R_t = \frac{P_t - P_{t-1}}{P_{t-1}} \quad \text{for } t = 1, 2, \dots, T
$$

where $T$ is the total number of trading days in the sample.


### A.2. Mean Daily Return

The sample mean of daily returns over the entire period is :

$$
\bar{R} = \frac{1}{T} \sum_{t=1}^{T} R_t
$$


### A.3. Standard Deviation of Daily Returns

The sample standard deviation (volatility) of daily returns is :

$$
\sigma = \sqrt{\frac{1}{T-1} \sum_{t=1}^{T} (R_t - \bar{R})^2}
$$

### A.4. Pearson Correlation Coefficient

The Pearson correlation coefficient between the returns of two assets $X$ and $Y$ is :

$$
\rho_{XY} = \frac{\sum_{t=1}^{T} (R_{X,t} - \bar{R}_X)(R_{Y,t} - \bar{R}_Y)}{\sqrt{\sum_{t=1}^{T} (R_{X,t} - \bar{R}_X)^2 \cdot \sum_{t=1}^{T} (R_{Y,t} - \bar{R}_Y)^2}}
$$

This coefficient is computed using the `corr()` function in pandas.


### A.5. Geometric Brownian Motion (GBM) Monte Carlo Simulation

The discrete-time GBM formula used for simulating future price paths is :

$$
S_{t+\Delta t} = S_t \exp \left( \left( \mu - \frac{\sigma^2}{2} \right) \Delta t + \sigma \sqrt{\Delta t} \varepsilon \right)
$$

where :

- $S_t$ = price at time $t$
- $\mu$ = mean of simple daily returns (used as an approximation to log returns for small $\Delta t$ )
- $\sigma$ = standard deviation of simple daily returns (used as an approximation to log returns for small $\Delta t$ )
- $\Delta t$ = time step (here, $1/252$ of a year)
- $\varepsilon$ = standard normal random variable ($N(0,1)$)

In the code, $\mu$ and $\sigma$ are estimated from historical daily returns. The simulation generates 1,000 paths for each stock over 252 trading days, using `numpy.random.normal` to draw $\varepsilon$.

<br>

## Appendix B: Correlation Matrix of Daily Returns for the Three Companies

The Pearson correlation coefficients between the daily returns of Apple Inc. (AAPL), Alphabet Inc. (GOOGL), and Microsoft Corp. (MSFT) over the period from January 1, 2020, to December 31, 2024, are presented in Table B.1. The values have been rounded to four decimal places.


**Table B.1: Correlation Matrix**  


|                 |         AAPL         |        GOOGL        |       MSFT       |
|      :---       |        :---:         |        :---:        |       :---:      |
|     **AAPL**    |       1.000000       |       0.648932      |      0.748327    |
|    **GOOGL**    |       0.648932       |       1.000000      |      0.746182    |
|    **MSFT**     |       0.748327       |       0.746182      |      1.000000    |


### Interpretation

The three stocks exhibit a strong positive correlation, with values ranging from 0.648932 to 0.748327. These high correlations imply that the three companies are subject to common market forces, such as macroeconomic conditions, interest rate changes, and sector-wide news, and therefore their price movements tend to be synchronised. From a portfolio diversification perspective, combining these three assets offers limited risk-reduction benefits compared to a portfolio with assets from less correlated sectors.


### Mathematical Formula

The correlation matrix is computed using the Pearson correlation coefficient defined in Appendix A. For each pair of assets $i$ and $j$, the coefficient $\rho_{ij}$ is calculated as :

$$
\rho_{ij} = \frac{\sum_{t=1}^{T} (R_{i,t} - \bar{R}_i)(R_{j,t} - \bar{R}_j)}{\sqrt{\sum_{t=1}^{T} (R_{i,t} - \bar{R}_i)^2 \cdot \sum_{t=1}^{T} (R_{j,t} - \bar{R}_j)^2}}
$$

All diagonal elements are naturally equal to 1.0 because an asset is perfectly correlated with itself.

<br>

## Appendix C: Explanation of the Geometric Brownian Motion (GBM) Model and Monte Carlo Simulation


### C.1. Model Overview

Geometric Brownian Motion (GBM) is a continuous-time stochastic process commonly used to model the dynamics of asset prices. It is described by the stochastic differential equation (SDE) :

$$
dS_t = \mu S_t dt + \sigma S_t dW_t
$$

where :

- $S_t$ is the asset price at time $t$,
- $\mu$ is the drift coefficient (expected rate of return),
- $\sigma$ is the diffusion coefficient (volatility),
- $dW_t$ is an increment of a standard Wiener process.


### C.2. Discrete-Time Solution

For practical simulation, the SDE is discretised using Euler-Maruyama or an exact solution. The exact solution for a single time step of length $\Delta t$ is :

$$
S_{t+\Delta t} = S_t \exp \left( \left( \mu - \frac{\sigma^2}{2} \right) \Delta t + \sigma \sqrt{\Delta t} \varepsilon \right)
$$

where $\varepsilon \sim N(0,1)$. This formulation ensures that simulated prices remain positive and that the distribution of returns follows a log-normal distribution.


### C.3. Parameter Estimation

In this project, the parameters $\mu$ and $\sigma$ are estimated from the historical **simple daily returns** of each stock. For a small time step $\Delta t = 1/252$, simple returns provide a close approximation to log returns, which are the theoretical basis of the GBM model. Therefore, we set :

$$
\mu = \frac{1}{T} \sum_{t=1}^{T} R_t \quad \text{and} \quad \sigma = \sqrt{\frac{1}{T-1} \sum_{t=1}^{T} (R_t - \bar{R})^2}
$$

where $R_t$ are the simple daily returns defined in Appendix A.


### C.4. Monte Carlo Simulation Procedure

The Monte Carlo simulation proceeds as follows :

1. For each stock, estimate $\mu$ and $\sigma$ from historical daily returns.
2. Set the initial price $S_0$ equal to the last observed price in the dataset.
3. For $k = 1, 2, \dots, N$ (where $N = 1000$):
   - Generate a series of $\varepsilon$ values for $t = 1, 2, \dots, T$ (with $T = 252$).
   - Recursively apply the discrete-time GBM formula to produce a price path.
4. Record the final price $S_T^{(k)}$ for each path.
5. Compute summary statistics :
   - Expected final price :

    $$
    \frac{1}{N} \sum_{k=1}^{N} S_T^{(k)}
    $$

   - Expected return :
     
    $$
    \frac{1}{N} \sum_{k=1}^{N} \left( \frac{S_T^{(k)}}{S_0} - 1 \right)
    $$

   - Standard deviation of returns (risk) :
     
    $$
    \sqrt{\frac{1}{N-1} \sum_{k=1}^{N} \left( \frac{S_T^{(k)}}{S_0} - \text{mean return} \right)^2}
    $$

   
  
  This approach provides a probabilistic assessment of future price movements, which is essential for risk management and investment decision-making.
