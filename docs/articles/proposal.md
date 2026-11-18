# BST 260 Final Project Proposal

**To the BST260 Teaching Team, Fall 2026**

I will study how permitless concealed carry spread across U.S. states
from 2014 to 2024 and how firearm mortality changed in adopting states
compared with states that continued to require permits.

## Vignette 1. Where and when did states remove permit requirements?

I will look at when each state stopped requiring a permit for concealed
carry and what rules it had before the change. Then I will look for
patterns. Did more states make the change in certain years or in certain
parts of the country? I will use `gunleg`, which contains policy records
and references to state laws from the RAND State Firearm Law Database.
The `finalproject` package includes a copy of the data.

``` r

data("gunleg", package = "finalproject")
```

I will use the following methods to build and compare state policy
histories.

- **Record filtering
  ([`filter()`](https://rdrr.io/r/stats/filter.html)).** Keep the laws
  about concealed carry. Include older laws so I can tell what rules
  each state had at the start of 2014.
- **Date sorting (`arrange()`).** Put each state’s laws in order by when
  they took effect. This will show when the state first dropped the
  permit requirement and when it made later changes. If a date is
  unclear, I will check the law itself.
- **Cross-tabulation.** Count how many states in each region switched
  from each type of permit rule. Mark cases where I cannot confirm the
  earlier rule.
- **Annual adoption counts.** Count each state once, in the year it
  first dropped the permit requirement. Use these counts to see which
  years had the most changes.
- **State timeline plot.** Give each state its own row and mark the year
  it dropped the requirement. Group the rows by region so states are
  easy to compare.
- **Cumulative adoption curves.** For each year, show what percentage of
  states in each region had dropped the requirement by then. Percentages
  make it easier to compare regions with different numbers of states.

## Vignette 2. How did firearm mortality change after adoption?

For each group of states that dropped the permit requirement in the same
year, I will look at how firearm death rates changed before and after
the law took effect. I will compare that change with what happened over
the same years in states that still required permits throughout that
period. I will check whether the two groups’ rates were already changing
differently before the law took effect and discuss whether other policy
changes might help explain the results. I will use `cdcfiremort`, which
contains annual age-adjusted firearm death rates per 100,000 residents
from CDC/NCHS. The `finalproject` package includes a copy of these data.

``` r

data("cdcfiremort", package = "finalproject")
```

I will use the following methods to compare mortality and assess
uncertainty.

- **Table join (`left_join()`).** Add each state’s adoption year to its
  mortality records. Check that there is one row for each state and
  year.
- **Three-year comparison windows.** Compare three full years before the
  law took effect with three full years after. Skip the year it took
  effect and use the same calendar years for both groups.
- **Group-mean line plots.** Plot the average death rate for each group
  in each year. Look at the years before the law took effect to see
  whether the groups were already moving in different directions.
- **Group-by-period interaction
  ([`lm()`](https://rdrr.io/r/stats/lm.html)).** For each adoption year,
  estimate how much more or less the death rate changed in states that
  dropped the requirement than in states that kept it. Report the
  difference in deaths per 100,000 people.
- **95% confidence intervals.** Calculate one before-and-after change
  for each state. Use those changes to estimate how uncertain the
  difference between the two groups is.
- **Two-year window check.** Repeat the comparison with the same states,
  using two years before and two years after. Check whether the
  estimated difference changes in size or direction.
