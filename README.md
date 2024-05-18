## Option Pricing Tree Models
This repository contains implementations of various option pricing tree models in Python. The models included are:

1. **Binomial Model**
   - `Binomial.ipynb`: Contains the implementation of the Binomial option pricing model. <br/> 

   The Binomial Option Pricing Model is a widely used method for valuing American options, which are options contracts that can be exercised at any point up until, and including, the expiration date. The process for computing both       American and European option values in a binomial tree model is conducted through backward induction. <br/> 

   First, the desired asset data is retrieved to compute the most recent asset price (S_0), the volatility (σ), and an appropriate strike price (K). The binomial American/European option model is constructed by first computing the       upward (u) and downward (d) movements and their respective probabilities (p). The up and down factors are calculated as: <br/> 
      u = exp⁡(σΔt) <br/> 
      d = exp⁡(−σΔt) <br/> 
      p = exp⁡(rΔt)−d / (u−d) <br/> 

   Next, the tree of prices is computed, which requires iteration starting at the initial price S0S0​ and multiplying it by the factors u and d corresponding to the number of up and down movements, respectively, needed to reach node      nn:
      S_(n,i) = S_0⋅u_(n−i)⋅d_i 
   where m is the number of up movements from the initial node to node n, calculated as m = n−i.

   At the final nodes of the binomial tree, the option value is determined based on the option type. If the option is a call, the option value is computed as:
      value = max⁡[S_(n,i) − K, 0]
   If the option is a put, the option value is computed as:
      value = max⁡[K - S_(n,i), 0]

   For a European option contract, beginning at the terminal nodes (node n), final option values are determined based on the stock price at maturity. Moving backward, intermediate nodes calculate option values using expected future    payoffs discounted at the risk-free rate, integrating probabilities from the binomial distribution for upward (u) and downward (d) movements. This process culminates at the starting node (node 0), yielding the initial option          value and enabling the determination of the option's fair price:
      value_(i,j) = exp⁡(−rΔt)⋅[p⋅value_(i,j+1) + (1−p)⋅value_(i+1,j+1)]

   For an American option contract, the value calculation uses the same backward induction logic as the European contract. However, at each node, the option value is computed as the maximum between the hold value, which is the           computed option value at the specified node, and the exercise value, which is the option value at the terminal node. Specifically:
   value_(i,j) = max⁡(exercise value, hold value)
   where:

    Exercise Value for Call: max⁡[S_(i,j) − K, 0]
    Exercise Value for Put: max⁡[K - S_(i,j), 0]
    Hold Value: exp⁡(−rΔt)⋅[p⋅value_(i,j+1) + (1−p)⋅value_(i+1,j+1)]

   If the hold value exceeds the exercise value, the contract is executed prior to expiry. If the exercise value exceeds the hold value, the contract is executed at the terminal node. Through this method, the Binomial Option Pricing     Model provides a robust framework for valuing American and European options.

2. **Trinomial Model**
   - `Trinomial.ipynb`: Contains the implementation of the Trinomial option pricing model.

   The Trinomial Option Pricing Model is an extension of the Binomial Model that incorporates an additional price movement option at each time step, creating a three-branch tree instead of two. In a trinomial tree model, option values are calculated using backward induction. Starting at terminal nodes (node n), final option values depend directly on the stock price at maturity. Progressing backward, intermediate nodes compute option values by discounting expected future payoffs at the risk-free rate. This approach integrates probabilities derived from the trinomial distribution, considering possible movement up (u), no movement (m), or movement down (d) of the stock price. The process concludes at the starting node (node 0), yielding the initial option value and enabling the determination of the option's fair price.

3. **Whitepapers**
   - `Binomial_Huang284-286.pdf`: Pages 284-286 of "THE COMPLETE GUIDE TO Option Pricing Formulas SECOND EDITION" by ESPEN GAARDER HAUG which contains the theory and key equations utilized in the Binomial Model.
   - `Numerical-Methods-versus-Bjerksund-and-Stensland-Approximations-for-American-Options-Pricing-.pdf`: Comparative analysis of the Binomial, Trinomial, and Bjerksund-Stensland models with logic used to construct the Binomial/Trinomial Models.
