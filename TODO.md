# dividend-drop: does the share price really fall by the dividend amount?

## Goal
In theory, on the ex-dividend date the price falls by exactly the dividend. In practice
it falls slightly less. Measure that ratio, and see what it says about the taxation of
the holders.

## Data
- `yfinance`: `.dividends` gives ex-dates and amounts, `.history()` gives the previous
  close and the opening price on the day.
- Universe: CAC 40 and S&P 500 constituents, 15 years of history.

## Steps
- [ ] Set up repo and dependencies
- [ ] Build the event table: (ticker, ex-date, dividend, close D-1, open D)
- [ ] Clean: exclude splits, special dividends, days with news
- [ ] Compute the drop ratio = (close D-1 minus open D) / dividend
- [ ] Distribution of the ratio: median, spread, outliers
- [ ] Neutralise the market move of the day (subtract the index return)
- [ ] Regress the ratio on dividend yield and market capitalisation
- [ ] Compare France and the United States, where the tax regimes differ
- [ ] README: the observed ratio, and the tax interpretation

## Done when
A defensible number for the median drop ratio in each market, with a confidence
interval, and an explanation of why it differs from 1.

## Traps
- The market noise of the day is larger than the effect you are chasing, so
  neutralising by the index is not optional.
- Stock dividends are not cash dividends. Exclude them.
