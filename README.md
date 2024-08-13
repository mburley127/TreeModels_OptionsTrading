## Option Pricing Tree Models
This repository contains implementations of various option pricing tree models in Python. The models included are:

1. **Binomial Model**
   - `Binomial.ipynb`: Contains the implementation of the Binomial option pricing model. <br/> 

   The Binomial Option Pricing Model is a widely used method for valuing American and European options. American options can be exercised at any point up until expiration, making their valuation more complex than European options, which can only be exercised at maturity. The binomial model uses a backward induction process to calculate option values, constructing a tree of possible asset prices over time. <br/> 

   To start, the model requires the most recent asset price, volatility, and an appropriate strike price. Using these inputs, the model calculates the possible upward and downward movements in asset price and their respective probabilities. The tree is then built by iterating from the initial asset price and applying these movements at each step. <br/> 

   At the final nodes of the tree, the option value is determined based on whether it's a call or put option. For European options, the process involves calculating the option's value at maturity and then working backward through the tree, using expected future payoffs discounted at the risk-free rate. This process results in the fair price of the option at the initial node. <br/> 

   For American options, the model also uses backward induction but adds the flexibility of early exercise. At each node, the option's value is computed as the maximum between the value of holding the option and the value of exercising it. This ensures that the model accurately reflects the option's potential to be exercised before expiration. <br/> 

2. **Trinomial Model**
   - `Trinomial.ipynb`: Contains the implementation of the Trinomial option pricing model.

   The Trinomial Option Pricing Model is an extension of the Binomial Model that incorporates an additional price movement option at each time step, creating a three-branch tree instead of two. In a trinomial tree model, option values are calculated using backward induction. Starting at terminal nodes (node n), final option values depend directly on the stock price at maturity. Progressing backward, intermediate nodes compute option values by discounting expected future payoffs at the risk-free rate. This approach integrates probabilities derived from the trinomial distribution, considering possible movement up (u), no movement (m), or movement down (d) of the stock price. The process concludes at the starting node (node 0), yielding the initial option value and enabling the determination of the option's fair price.

4. **Whitepapers**
   - `Binomial_Huang284-286.pdf`: Pages 284-286 of "THE COMPLETE GUIDE TO Option Pricing Formulas SECOND EDITION" by ESPEN GAARDER HAUG which contains the theory and key equations utilized in the Binomial Model.
   - `Numerical-Methods-versus-Bjerksund-and-Stensland-Approximations-for-American-Options-Pricing-.pdf`: Comparative analysis of the Binomial, Trinomial, and Bjerksund-Stensland models with logic used to construct the Binomial/Trinomial Models.
