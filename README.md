## Option Pricing Tree Models
This repository contains implementations of various option pricing tree models in Python. The models included are:

1. **Binomial Model**
   - `Binomial.ipynb`: Contains the implementation of the Binomial option pricing model.

   The Binomial Option Pricing Model is a widely used method for valuing American options, which are options contracts that can be exercised at any point up until, and including, the expiration date. Option values in a binomial tree model are computed through backward induction. Beginning at terminal nodes (node n), final option values are determined based on the stock price at maturity. Moving backward, intermediate nodes calculate option values using expected future payoffs discounted at the risk-free rate, integrating probabilities from the binomial distribution for upward (u) and downward (d) movements. This process culminates at the starting node (node 0), yielding the initial option value and enabling the determination of the option's fair price.

2. **Trinomial Model**
   - `Trinomial.ipynb`: Contains the implementation of the Trinomial option pricing model.

   The Trinomial Option Pricing Model is an extension of the Binomial Model that incorporates an additional price movement option at each time step, creating a three-branch tree instead of two. In a trinomial tree model, option values are calculated using backward induction. Starting at terminal nodes (node n), final option values depend directly on the stock price at maturity. Progressing backward, intermediate nodes compute option values by discounting expected future payoffs at the risk-free rate. This approach integrates probabilities derived from the trinomial distribution, considering possible movement up (u), no movement (m), or movement down (d) of the stock price. The process concludes at the starting node (node 0), yielding the initial option value and enabling the determination of the option's fair price.

3. **Whitepapers**
   - `Binomial_Huang284-286.pdf`: Pages 284-286 of "THE COMPLETE GUIDE TO Option Pricing Formulas SECOND EDITION" by ESPEN GAARDER HAUG which contains the theory and key equations utilized in the Binomial Model.
   - `Numerical-Methods-versus-Bjerksund-and-Stensland-Approximations-for-American-Options-Pricing-.pdf`: Comparative analysis of the Binomial, Trinomial, and Bjerksund-Stensland models with logic used to construct the Binomial/Trinomial Models.
