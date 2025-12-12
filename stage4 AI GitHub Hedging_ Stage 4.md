**Stage IV: Structured AI Prompt: EUR Receivable FX Hedging Model**

1. **Persona & Goal**  
   * Goal:   
     1. Imagine you are a Senior FX Treasury Analyst. Your task is to generate a comprehensive, professional, and fully self-contained Excel spreadsheet model. This model will include detailed markdown tables that represent the spreadsheet structure, including specific formulas. This will evaluate and compare three distinct FX hedging alternatives (Forward, Money Market, and Option) for a one-year, EUR dominated receivable.   
   * Context and Persona  
     1. *Scenario: A company has a receivable of EUR due in T\_DAYS days.*  
     2. *Role: Financial Modeler / Treasury Analyst.*  
     3. *Task: Generate a single Excel workbook with clear, auditable logic for each hedging strategy, including sensitivity analysis and professional formatting.*   
   * Context Files: Use the logic in  
     1.  *[https://github.com/example/fin321/stage2-spec.md](https://github.com/example/fin321/stage2-spec.md)*  
     2.  *[https://github.com/example/fin321/stage3-skeleton.xlsx](https://github.com/example/fin321/stage3-skeleton.xlsx)* 

2. **Input Data/Assumptions:** Provide all numerical constants and rates.

   * ## Inputs (Known Variables)

| Section | Variable Name | Description / Purpose | Unit | Variable Amount | Source |
| ----- | ----- | ----- | ----- | ----- | ----- |
| I. Core Variables | FC\_AMT | Foreign-currency receivable | EUR | 4,500,000 | Company data |
|  | S₀ | Current EURUSD spot rate | USD/EUR | 1.1619 | Yahoo Finance 2025 |
|  | F₀ | 1-year EURUSD forward rate | USD/EUR | 1.0875 | Provided |
|  | r\_USD | USD 1-year interest rate | % annual | 3.66% | FRED Treasury Yield |
|  | r\_EUR | EUR 1-year interest rate | % annual | 3.31% | Euribor Rates 2025 |
|  | t | Time to maturity | Years | 1.0 | Derived |
| II. Option Variables | K\_put | EUR Put strike | USD/EUR | 1.0875 | Analyst choice |
|  | K\_call | EUR Call strike | USD/EUR | 1.0875 | Analyst choice |
|  | Premium\_put | Put premium | USD per contract | 0.015 | Scenario |
|  | Premium\_call | Call premium | USD per contract | 0.018 | Scenario |
|  | T\_DAYS | Time to maturity  | days | 360 | Scenario |
| III. Final Results | FWD Hedge USD Proceeds | FWD proceeds, certainty benchmark | USD |  | Reference Calc Tab 2 Result |
|  | MM Hedge USD Proceeds | Cross-check | USD |  | Reference Calc Tab 3 Result |
|  | Unhedged USD Proceeds (at F₀) | Expected Value | USD |  | Calculate (FC\_AMT  F₀) |

## 

## 

   

   

   b. 	Named Range Definitions

| Standardized name | Source/Calculation |
| :---- | :---- |
| FC\_AMT | Input variable |
| S₀\_in | Input variable |
| F₀\_in | Input variable |
| r\_USD | Input variable |
| r\_FC | Input variable |
| CT | Transaction Cost (Assumption) |
| K\_put | Input variable |
| K\_call | Input variable |
| Premium\_put | Input variable |
| Premium\_call | Input variable |
| T\_DAYS | Input variable |
| T\_YRS | Calculated: \= T\_DAYS / 360 |

## c. Assumptions & Constraints

* Interest rates are simple annual yields on a 360-day basis.  
  * Forward rate follows interest-rate parity – F0 \= S0  1 \+ rUSD1 \+ rEUR.  
  * Option premium is paid upfront in USD.  
  * Transaction costs (ct) of 0.05% apply equally to all hedges.  
  * Exchange rates are quoted as USD per EUR.  
  * There are no taxation, credit, or liquidity frictions.  
  * Options are European-style and exercised only at maturity.  
  * Results are expressed in USD proceeds at the 1-year horizon.

3. **Formatting & Color Coding:** The spreadsheet must strictly adhere to the following color-coding standards:  
1. YELLOW (e.g., RGB 255, 255, 0): Inputs / Decision Variables such as FC\_AMT, S₀*in, K*\_PUT)  
2. BLUE (e.g., RGB 173, 216, 230\): Assumptions such as R\_USD, R\_FC, CT, T\_YRS calculation  
3. GREEN (e.g., RGB 144, 238, 144): Formulas (intermediate and final results of the hedging calculations).  
4. GRAY (e.g., RGB 211, 211, 211): Outputs and Key Performance Indicators (KPIs); Final net proceeds of each hedge and the verification check.

4. **Spreadsheet Requirements**  
   * Model Components: The workbook must be logically organized into labeled sections and include:  
     1. *Inputs/Assumptions Table (using named ranges)*  
     2. *Forward Hedge Calculation*  
     3. *Money Market Hedge (3-step) Calculation*  
     4. *Option Hedges (Put and Call) Calculation*  
     5. *Summary of Final Net USD Proceeds*  
     6. *Sensitivity Table*  
     7. *Verification / Parity Check*  
   * Transaction Costs: Apply a total transaction cost (CT=0.05%) to the final net proceeds of all hedging strategies (Forward, MM, Put, Call).  
   * Sensitivity Table Analysis: Create a two-column table to analyze the final outcome of the four strategies across different market spot rates at maturity (St).  
     1. *Range: Vary St from 0.95  S0 to 1.05  S0.*  
     2. *Increment:Use a step size of S00.1010*    
     3. *Columns:*  
        1. *ST(Market Rate at Maturity)*  
        2. *Unhedged Proceeds*  
        3. *Forward Hedge Proceeds (reference the final Forward result)*  
        4. *Money Market Hedge Proceeds (reference the final MM result)*  
        5. *Option (put) Proceeds*  
        6. *Option (call) Proceeds*

5. **Model Logic (Formulas):** Implement the following precise logic for a 1-year horizon.  
   * Forward Hedge Calculation

     USDfwd= FC\_AMT  F0(1-CT)

   * Money Market Hedge Calculation

| Calculation Step | Formula/Logic | Result  |
| :---- | :---- | :---- |
| PV of Receivable (EUR) | PVEUR= FC\_AMT(1+rEURTYRS) | Calculate in EUR |
| Convert to USD  (at S0) | USD0=PVEUR S₀\_in | Calculate in USD |
| Future Value of USD Investment | USDmm=USD0(1+r\_USDT\_YRS)(1-CT) | Calculate in USD |

   * Option Hedges (Formulas for Sensitivity Table)  
     *I. Formula A: Option (put)*

USDput=\[FC\_AMT  MAX(St,Kput) \- (FC\_AMT Premium\_put)\] (1-ct) 

*II.  Formula B: Option (call)*

USDcall=\[FC\_AMT  St \-(FC\_AMT Premium\_call)\] (1-ct) 

6. **Verification & Auditability**  
   * Parity Validation: Explicitly perform an interest rate parity check in a separate cell.  
     1. *Check: Does the implied forward rate calculated using S0 and the interest rates equal the market forward rate F0.*  
        Fimplied=S₀\_in (1 \+ r\_USD  T\_YRS)(1 \+ r\_fc  T\_YRS)  
     2. *Confirmation: The model must explicitly display a check that validates that Net Forward Proceeds is nearly equal to Net Money Market Proceeds, highlighting any material difference.*  
   * Formula Mapping**:** After generating the spreadsheet, provide a separate section or a markdown table detailing the cell reference and the full formula used for the key results (Final USD Proceeds for Forward, MM, Put, and Call).  
   * Named Range Confirmation: Confirm in a final step that all 11 required named ranges have been successfully created and are referenced in the model’s formulas.

7. **Export:** Return a downloadable, fully functionable Excel file (.xlsx) containing the model and the accurate analysis of the scenario.

