# KellyCriterionParimutuelBetting

Parimutuel betting (from French pari mutuel, "mutual betting") is a betting system in which all bets of a particular type are placed together in a pool; taxes and the "house-take" or "vigorish" are deducted, and payoff odds are calculated by sharing the pool among all winning bets. In some countries it is known as the Tote after the totalisator, which calculates and displays bets already made.

Parimutuel betting differs from fixed-odds betting in that the final payout is not determined until the pool is closed – in fixed odds betting, the payout is agreed at the time the bet is sold.

The Kelly Criterion derives optimal bet sizing in fixed odd betting where the better has an edge on the house (due to superior information on the outcome), maximising long term growth rate over short term expected value. To many this is unintuitive, as shown by a study done where people were asked to maximise outcomes when betting on a biased (60% win) coin: https://elmwealth.com/lessons-from-betting-on-a-biased-coin-cool-heads-and-cautionary-tales/

In many real-world applications, particularly in finance, the Kelly Criterion overstates the portion of the portfolio that should be invested. The reasons for this are plentiful, one of which are the diminishing returns one yields when pursuing the same trading strategy with larger investments. This is particularly true for illiquid positions where the ideal investment size is large compared to the volume traded. 

<details>
  <summary>Demonstration</summary>

| Bet size  | odds | expected profit |
| ------------- | ------------- | ------------- |
| 1  | 10/11 -> 0.91 | 0.43$ | 
| 5  | 10/15 -> 0.67 | 1.25$ |
| 7.32  | 10/17.32 -> 0.58 | 1.33$ |
| 10  | 10/20 -> 0.5 | 1.25$ |
| 20  | 10/30 -> 0.33 | 0.00$ |
| 30  | 10/40 -> 0.25 | -1.875$ |

as can be seen, larger bet sizes continually worsen odds. The expected return is maximised at an investment of 7.32, a result which is derived in section one of the write up. betting more than 20$ actually yields negative returns as it pushes the odds below the real probability of 0.75.

![image](https://user-images.githubusercontent.com/62283469/123427909-1c951680-d5bd-11eb-9b54-baec5f09538e.png)

it is obvious that betting above the maximum expected value is never reasonable. However, Kelly teaches us that betting *at* the expected maximum is *also* not always the optimal system for long term growth - this occurs when the expected maximum exceeds the Kelly criterium. For instance, when the size of the portfolio itself is 7.32, it would be foolish to bet all of it, as there is a 25% chance of losing all and being unable to exploit the edge in the future.

It is therefore clear that the bet should never exceed the expected maximum, but also not exceed the Kelly criterion. This in turn poses its own problems, as this criterion is dependent on the edge you have on the house, however this edge diminishes with bet size (unlike fixed odds betting, with Kelly based his Mathematics off).
</details>

<details>
  <summary>Derivation</summary>
### Maximum expected value
  the ratio of the pool that is paid out in the scenario of a win is
  
  <img src="https://render.githubusercontent.com/render/math?math=\frac{x_{0}}{P_{L}+x_{0}}*(x_{0}+P_{L}+P_{W})">
</details>


