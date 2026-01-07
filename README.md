# Risk Premium Assessment & Aggregate Stop-Limit Analysis
# Motor Insurance – British Courier Company
# Project Overview
This project assesses the 2019 risk premium per vehicle for a British courier company’s motor insurance programme and evaluates the likelihood that annual damage losses exceed the aggregate stop limit. The analysis combines historical claims experience, loss development techniques, programme-specific deductibles, and stochastic simulation.
The work is designed to replicate a real-world non-life insurance pricing and risk assessment exercise, integrating Excel-based actuarial modelling with R-based probabilistic analysis.

# Objectives
	Estimate the expected injury premium per vehicle (no deductible).
	Estimate the expected damage premium per vehicle:
	without deductible (ground-up loss),
	with deductible (insurer-paid loss).
	Evaluate the probability that annual damage losses exceed the aggregate stop limit of £10,118,100.
	Provide a clear interpretation of results in line with the insurance programme structure.

# Data Sources
	18-year claims triangulation (used to derive development factors and ultimate losses).
	Itemised claims data covering approximately 8.5 years (ground-up, net of non-ranking excess).
	Historic exposure data by vehicle type (cars and other vehicles).
	2019 exposure assumptions:
	Cars: 661
	Other vehicles: 1,637




# Insurance Programme Structure
	Deductible per claim
	Cars: £150,000
	Other vehicles: £250,000
	Non-ranking excess
	£10,000 for ADFTWS claims (Accidental Damage, Fire, Theft, Windscreen)
	Aggregate stop limit
	£10,118,100 per year
	Applies only to the ranking layer:
	TP claims between £0 and deductible
	ADFTWS claims between £10,000 and deductible
	Insurer-paid losses above the deductible do not count toward the aggregate.
# Methodology
1. Loss Development
	An 18-year cumulative claims triangle was constructed.
	Link ratios and cumulative development factors (LDFs) were calculated.
	Ultimate loss factors were applied to develop all historical claims to ultimate.
2. Claim-Level Programme Application
For each claim:
	Ultimate loss was calculated using the relevant development factor.
	Insurer-paid loss was derived by applying the deductible.
	Ranking loss was calculated according to programme rules (including the £10k ADFTWS exclusion).
3. Premium Calculation
Annual losses were aggregated by year and vehicle group and divided by exposure to obtain:
	Injury premium per vehicle (deductible = 0),
	Damage premium per vehicle without deductible (ground-up),
	Damage premium per vehicle with deductible (insurer-paid).
The 2019 premium estimates were obtained by averaging the most recent six years of experience.

4. Aggregate Stop-Limit Risk
	Annual total ranking losses were exported to R.
	A bootstrap simulation was used to generate a large number of possible annual outcomes.
	The probability of exceeding the aggregate stop limit was estimated as:
P("Annual Ranking Loss">£10,118,100)

# Key Results (Summary)
	Injury losses contribute a relatively small but stable premium per vehicle.
	Damage losses are largely retained by the insured due to high deductibles.
	The insurer-paid damage premium per vehicle is low, consistent with the programme’s design.
	Bootstrap simulations indicate that the aggregate stop limit is very unlikely to be breached, with no exceedances observed in 200,000 simulated years.
	The aggregate stop limit is therefore conservative relative to historical experience.

