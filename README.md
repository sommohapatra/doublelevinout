(adapted from Quantopian/Quantlandian)

Intuitively, it might be possible to generate excess returns via cleverly timed entries and exits in and out of the equity market. This algo may be a first step toward developing a strategy that derives optimal moves in an out of the market on the basis of early indicators of equity market downturns. At the very least, the algo could start an interesting discussion regarding the sense and nonsense of trying to time market entry and exit in this way. Either way, your contribution is highly appreciated.

Backdrop for the initial code:
- Resources and industrial products are early in the value chain and
market value drops in corresponding firms are early indicators of
growth worries that ultimately affect other sectors and the broader
market
- Equity market value growth benefits substantially from cheap debt,
such that increases in bond yields (i.e., drops in bond prices)
should be an early indicator of a slowdown in growth
- Yet, no matter what these signals say, if the market drops by 30%
(‘once in a decade opportunity’), we want to be in

Measures used in the initial code:
- Resources: The DBB ETF (Invesco DB Base Metals Fund) provides the
signal. DBB tracks the prices of three key industrial metals:
aluminum, copper and zinc. A 7% drop over an approx. 3-month trading
period is considered a substantial drop.
- Industrials: The XLI ETF (Industrial Select Sector SPDR Fund)
provides the signal. XLI tracks the broad US industrial sector. A 7%
drop over an approx. 3-month trading period is considered a
substantial drop.
- Cost of debt: The SHY ETF (iShares 1-3 Year Treasury Bond) provides
the signal. SHY tracks short-term US Treasury debt (1-3 years) and
changes in this debt’s ‘risk-free’ interest yield should be
indicative of changes in firms’ cost of debt which is based on the
risk-free rate (risk-free rate + risk premium). A 60 basis points
increase (i.e., drop in the bond price) over an approx. 3-month
trading period is considered substantial.

Rules of the algo:
- In terms of equity, only the market (SPY) is traded
- If out of the market, the money is invested in bonds (IEF and TLT)
- If any of the indicators drops substantially, we go out of the
market and into bonds. We wait for 3 trading weeks for the dust to
settle, unless the market drops by 30% during the waiting period in
which case we enter immediately
- Notes: this algo’s focus is only on the market ‘entry vs exit’
decision, i.e. not on the ‘what equities do I select’ decision. The
assumption is that you will be able to plug your equity selection
logic into this algo and get an additional boost in terms of your
strategy’s returns. However, finding an optimal equity selection is
not the focus here (if you are interested in equity selection, see
other community forum contributions such as “Quality Companies in an
Uptrend” or “Uncovering Momentum”, among others). Scheduling
functions: Whether we ‘go out’ is checked daily since equity prices
usually drop quickly when things deteriorate and hence speed seems
paramount. In contrast, whether we ‘go back in’ is checked weekly and
this is a personal preference so that complex equity purchases only
have to be executed once a week, at the end of the week. This is so
that a ‘lazy’ trader who does not have the time to execute complex
reshuffles (other than doing a ‘sell all’ and going into bonds) of
the portfolio on a daily basis can combine the algo with a more
sophisticated equity selection strategy.

Outcomes for the initial algo:
- from 1 Jan 2008 to 2 Oct 2020, the total return is approx. 860% vs
190% for the SPY (= being always in)
- the backtest indicates a beta of 0.34 and the tear sheet shows an
alpha of 20%
- Note: regarding the backtest period, consider the launch dates of
the different ETFs. All of them should be available from 1 Jan 2008
onwards but some may be unavailable in earlier periods, creating a
limit regarding testing the algo in earlier time periods

Brainstorming regarding improvement opportunities:
- different ETFs/ways to measure prices of resources (e.g.,
additional key resources such as oil), industrial goods (e.g., a
stronger focus on industrial capital goods), and bonds (e.g.,
corporate bonds instead of government bonds)
- additional aspects—other than resources, industrial goods, and bond
yields—that could provide early indicators of equity downturns
- improvement of settings (e.g., waiting period, %-points indicating
‘substantial’ drops)
- code improvements (errors/unintended outcomes, efficiency)

