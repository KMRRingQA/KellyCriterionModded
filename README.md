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
  <summary>Maximum Expected Value</summary>
  the expected return after betting is<br><br>
  
  <img src="https://render.githubusercontent.com/render/math?math=\frac{x_{0}}{L+x_{0}}*(x_{0}+L+W)*p-x_{0}"><br>
  
  where x<sub>0</sub> is the size of the bet, W is the size of the winning pool (excluding bet), L is the size of the losing pool & p is the probability of       winning.  
    
  ![image](https://user-images.githubusercontent.com/62283469/123427909-1c951680-d5bd-11eb-9b54-baec5f09538e.png)   
  after differentiating and simplifying we find that the maximum turning point, or the derivatives' root of interest, is found using the expression:<br><br>
  
  <img src="https://render.githubusercontent.com/render/math?math=\frac{-\sqrt{\LWp-\LWp^{2}}-\W\p%2B\W}{\p-1}"><br>
  
  this is the maximum expected value. Betting higher than this amount is never correct. Betting at this amount is only correct if the portfolio is so large that the amount is at or above the Kelly Criterium. In most cases, the Kelly Criterium will be significantly lower. 
</details>
<details>
  <summary>Vanilla Kelly Criterion</summary>
  To understand the mechanism and large assumptions behind this system, it is useful to derive the Kelly Criterion as it related to fixed-odd betting.
  Here, rather than having to take into account pot sizes and the magnitude of the own capital, the growth rate is solely dependent on a single factor which determines the fraction of capital that should be put at risk with each bet. 
  This means that, on the nth bet, the expected returns are:<br><br>
    
  <img src="https://render.githubusercontent.com/render/math?math=A_{n}=A_{0}(1%2B\bx)^{W}(1-x)^{L}"><br>

  where A<sub>n</sub> is the returns after n steps, A<sub>0</sub> is the initial capital, b are the fixed odds set by the house, x the fraction of invested capital, W the number of wins and L the number of losses. 
   Since this fraction can vary greatly based on current ownings in parimutuel betting, this basic assumption can not be fullfilled, and the binomial tree on which Kelly bases his theory cannot be constructed without discrepencies.
  
  ![image](https://user-images.githubusercontent.com/62283469/123478733-c396a400-d5f7-11eb-8a38-73cba11cada2.png)

  as shown above, each path in a parimutuel betting tree results in slightly different values, even when the number of wins and losses are the same, thus differing from a tree purely based on a kelly coefficient.
  
  returning to the derivation: the growth rate of any system is defined as<br>
  
  <img src="https://render.githubusercontent.com/render/math?math=G=(\frac{A_{n}}{A_{0}})^{\frac{1}{n}}-1"><br>
  
  rearranging<br>
  ```math
  A_{n}=A_{0}(1%2B\bx)^{W}(1-x)^{L}
  ```

  <img src="https://render.githubusercontent.com/render/math?math==(\frac{A_{n}}{A_{0}})^{\frac{1}{n}}=[(1%2B\bx)^{W}(1-x)^{L}]^{\frac{1}{n}}"><br>
  <img src="https://render.githubusercontent.com/render/math?math==(1%2B\bx)^{\frac{W}{n}}(1-x)^{\frac{L}{n}}"><br>
  
  W/n and L/n are equialent to the probability of winning = p or losing = q, respectively. Since 0<=x<=1, we can show that the function<br>
  <img src="https://render.githubusercontent.com/render/math?math=(1%2B\bx)^{\p}(1-x)^{\q}"><br>
  
  which is equivalent to<br> 
  <img src="https://render.githubusercontent.com/render/math?math=e^{ln((1%2B\bx)^{\p}(1-x)^{\q})}"><br>
  
  is maximised when ln((1+bx)<sup>p</sup>+ln(1-x)<sup>q</sup> is maximised. Now, <br>
  
  <img src="https://render.githubusercontent.com/render/math?math=\f(x)=\ln((1%2B\bx)^{\p}(1-x)^{\q})=\ln(1%2B\bx)^{\p}%2B\ln(1-x)^{\q}=\pln(1%2B\bx)+\qln(1-x)"><br>
  
  <img src="https://render.githubusercontent.com/render/math?math=\therefore \f'(x)=\p\cdot\frac{1}{1%2B\bx}\cdot\b+\q\cdot\frac{1}{1-x}\cdot(-1)=\frac{\pb}{1%2B\bx}%2B\frac{-\q}{1-x}"><br>
    <img src="https://render.githubusercontent.com/render/math?math=\therefore x=\K=\frac{\bp-\q}{\b}"><br>
  which is the Kelly Criterion for fixed-odd bets.
</details>



