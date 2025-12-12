**Created by:** Francesca Murphy  
**Updated by:** Francesca Murphy   
**Date Created:** December 7, 2025  
**Date Updated:** December 12, 2025  
**Version:** 1.0  
**LLM Used:** GBT-5 ; Gemini 3.0 Pro

**MEMORANDUM**  
**To:** Chief Financial Officer / Treasury Committee  
**From:** Francesca Murphy, Senior FX Treasury Analyst   
**Subject:** FINAL RECOMMENDATION: EUR 4.5M Receivable Hedging Strategy

**Exposure Summary**  
The company holds a receivable of €4,500,000 due in 360 days. The underlying risk is that we are “Long EUR / Short USD”. This means that if the Euro depreciates against the American Dollar over the next year, the USD value of this cash flow will diminish, potentially impairing our ability to meet the USD-dominated budget commitments.

1. Current Market Context  
   1. Spot Rate (S0): 1.1619  
   2. Market Forward Rate (F0): 1.0875

*The market is pricing a significant depreciation of the Euro (forward discount), creating a challenging environment for standard forward hedging.*

**Summary of Hedge Outcomes**  
We evaluate three primary hedging strategies. All figures represent Net USD Proceeds after transaction costs (CT=0.05%).

| Strategy | Mechanism | Net USD Proceeds | Certainty Profile |
| :---- | :---- | :---- | :---- |
| 1\. Forward Contract | Lock rate at F0(1.0875) | $4,891,303 | High. Locked at F0. |
| 2\. Money Market (MM) | Borrow EUR, convert Spot, invest USD | $5,243,640 | Highest. Value locked at S0 |
| 3\. Put Option | Strike at 1.0875 (Kput) | $4,823,837\* | Variable. Floor exists, but premium reduces yield.  |
| 4\. Unhedged | Convert at future Spot (ST) | $5,228,550 | None. Full exposure to FX volatility.  |

*\*Put Option proceeds assume that the option is exercised at the floor. If EUR rallies, proceeds will increase.*  
*Critical Observation: There is a material deviation from the Interest Rate Parity. The Money Market Hedge yields \~$352,000 more than the Forward Contract. The market forward rate (1.0875) is significantly lower than the theoretically implied forward rate (\~1.1658).*

**Sensitivity Interpretation**  
We stress-tested the strategies against a range of future Spot Rates (ST) at maturity:

1. Scenario 1: EUR Depreciation (EUR crash to 1.00)  
   1. *Unhedged: Catastrophic loss of value; \~$4.5 M proceeds).*  
   2. *Forward: Protects value at $4.89 M.*  
   3. *Money Market: Outperforms, protects value at $5.24 M.*  
   4. *Put Option: Protects downside, but premium cost results in lower net proceeds ($4.82 M) compared to forwards.*   
2. Scenario 2: EUR Appreciation (EUR rally to 1.25)  
   1. *Unhedged: Significant windfall (\~$5.6 M proceeds).*  
   2. *Forward: Opportunity loss; Locked in at low rate ($4.89 M).*  
   3. *Money Market: Opportunity loss.; Locked in at spot rate of $5.24 M.*  
   4. *Put Option: Participates in upside, but the high upfront premium creates a high breakeven point. The EUR must rally significantly to beat the risk-free Money Market return.*  
      

**Strategic Recommendation**  
**Execute the Money Market Hedge immediately.**   
I explicitly advise against the Forward Contract and the Put Option for this specific exposure. The Money Market hedge generates $5.24 M in guaranteed proceeds. This exceeds the Forward contract’s proceeds ($4.89 M) by \~7.2%.  
This is an opportunity driven by the disconnect between the Spot Rate (1.1619) and the depressed Market Forward Rate (1.0875). Utilizing the Money Market hedge by borrowing EUR, converting it to USD, and investing the USD, we effectively synthesize a forward rate of \~1.1658, bypassing the inefficient public forward rate. 

**Executive Justification**

1. Profit Maximization: The Money Market hedge adds $352k directly to the bottom line compared to the standard policy Forward hedge.   
2. Cash Flow Stability: We convert the FX risk into interest rate risk (which is locked) and credit risk (managed via investment grade counterparties). The USD cash flow is fixed today.  
3. Budget Certainty: This strategy exceeds our budget rate. We can recognixe the revenue certainty immediately, removing 12 months of FX volatility from our forecasting.  
4. Operational Feasibility: While operationally heavier than a forward (requires balance sheet usage), a 7.2% yield increase justifies the administrative effort (the loan and deposit setup). 

