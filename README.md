## Option Pricing Tree Models
This repository contains implementations of various option pricing tree models in Python. The models included are:

1. **Binomial Model**
   - `Binomial.ipynb`: Contains the implementation of the Binomial option pricing model.

   The Binomial Option Pricing Model is a widely used method for valuing American options, which are options contracts that can be exercised at any point up until, and including, the expiration date. The process for computing both American and European option values in a binomial tree model are computed through backward induction. The desired asset data is retrieved, which allows for the computation of the most recent asset price, the volatility (sigma), and an appropriate strike price. The binomial american/european option model was constructed by first computing the upward/downward movements and their respective probabilities. From there, the tree of prices must be computed which requires iteration starting at the initial price S_0​ and multiplying it by the factors u and d corresponding to the number of up and down movements, respectively, needed to reach node n. The following function is used:
    S_n​ = S_0 * u^m * d^(n−m)
where m is the number of up movements from the initial node to node n, calculated as m = n - i. From there, the option type is determined at the final node, S_n:
   If the option is a call, the option value is computed as: max((S_n[i, n] - K), 0)
   If the option is a put, the option value is computed as: max((K - S_n[i, n]), 0)
Finally the desired option value can be computed. For a European option contract:
   Beginning at terminal nodes (node n), final option values are determined based on the stock price at maturity. Moving backward, intermediate nodes calculate option values using expected future payoffs discounted at the risk-free      rate, integrating probabilities from the binomial distribution for upward (u) and downward (d) movements. This process culminates at the starting node (node 0), yielding the initial option value and enabling the determination of      the option's fair price.
For an American Option Contract:
   The american option value uses the same option value computation logic as the european contract, but the option value is computed as the maximum value between the hold value, which is the computed option value at the specified node, and the exercise value, which is the option value at the terminal node. If the hold value > exercise value, the contract will be executed prior to expiry. If exercise value > hold value, the will be executed at the terminal node.

3. **Trinomial Model**
   - `Trinomial.ipynb`: Contains the implementation of the Trinomial option pricing model.

   The Trinomial Option Pricing Model is an extension of the Binomial Model that incorporates an additional price movement option at each time step, creating a three-branch tree instead of two. In a trinomial tree model, option values are calculated using backward induction. Starting at terminal nodes (node n), final option values depend directly on the stock price at maturity. Progressing backward, intermediate nodes compute option values by discounting expected future payoffs at the risk-free rate. This approach integrates probabilities derived from the trinomial distribution, considering possible movement up (u), no movement (m), or movement down (d) of the stock price. The process concludes at the starting node (node 0), yielding the initial option value and enabling the determination of the option's fair price.

4. **Whitepapers**
   - `Binomial_Huang284-286.pdf`: Pages 284-286 of "THE COMPLETE GUIDE TO Option Pricing Formulas SECOND EDITION" by ESPEN GAARDER HAUG which contains the theory and key equations utilized in the Binomial Model.
   - `Numerical-Methods-versus-Bjerksund-and-Stensland-Approximations-for-American-Options-Pricing-.pdf`: Comparative analysis of the Binomial, Trinomial, and Bjerksund-Stensland models with logic used to construct the Binomial/Trinomial Models.
