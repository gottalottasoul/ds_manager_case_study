# Purpose

This case study is intended to understand how you:
*	Frame a real-world data science problem
*	Apply hands-on modeling techniques
*	Translate analysis into actionable operational decisions
*	Communicate clearly with senior, non-technical stakeholders

This is not an exercise in achieving the highest possible model accuracy. We are more interested in your judgment, tradeoffs, and product thinking.
Deliverables

Please provide:
1.	Executive Summary (1–2 pages)
a.	Written for a Safety Director / Operations Executive
2.	Source Code
a.	Any code used for exploratory analysis, feature engineering, modeling, and evaluation

(Notebook or repository link preferred) 

# Scenario

You are a Data Science Manager supporting Suffolk’s Safety & Operations teams.

Suffolk uses digital platforms (e.g., Procore, HammerTech) to capture:
*	Safety observations and inspections
*	Follow-up tasks and corrective actions
*	Status, priority, categories, assignees, and timestamps

Leadership wants to reduce preventable safety incidents by identifying early warning signals in routine field data and focusing limited safety resources where they can have the greatest impact.
Because internal Suffolk data cannot be shared, you will use public NYC Department of Buildings (DOB) datasets as a realistic proxy for “project activity signals” and “leading indicators,” and a separate DOB dataset as the “incident outcome.”
 
# Data (NYC DOB Open Data)

You will use the following public datasets from NYC Open Data:
1.	Construction-Related Incidents (Outcome dataset)
2.	DOB Permit Issuance (Project activity / exposure proxy)
3.	DOB Complaints Received (Leading indicator / early warning proxy)
You may assume these datasets are representative of:
*	Incidents: recordable safety-related events
*	Permits: a proxy for project activity level / type / complexity (“exposure”)
*	Complaints: an early signal of potential issues requiring attention (311 + DOB-entered complaints)

# Objective
Design a weekly batch triage model that helps Suffolk answer:
“Which projects / sites should we focus on this week to reduce the likelihood of construction-related incidents?”

## Primary Objective (Required)
Using the DOB datasets above, build a model or scoring approach that identifies high-risk sites using:
*	Permits as a proxy for work activity / scope / churn / complexity
*	Complaints as a proxy for early warning signals
*	Historical incidents as prior-risk context (only if available at prediction time)
*	Assume the model will be used prospectively, not retrospectively (avoid leakage)

## Secondary Objective (Optional)
Explain how the same approach or signals could be extended over time to support schedule risk identification, even if you do not explicitly model it.
 
# Constraints & Assumptions
*	The model will be reviewed once per week
*	Safety leadership can only act on a limited number of sites/items
*	Only use information that would reasonably be known as of the scoring date
*	Preventing severe outcomes is more important than overall accuracy
*	Actionability matters more than model complexity
 
Suggested Modeling Framing (you can choose differently, but be explicit)
Unit of prediction (recommended): Site-week (e.g., BIN-week or address-week).
Target (example): “At least one construction-related incident at the site in the next 28 days.”

### Executive Summary Expectations
Your executive summary should address the following:
1.	Problem Framing
*	How you translated the NYC DOB datasets into a safety-risk problem
*	Key assumptions and tradeoffs you made (especially around joining, exposure bias, and reporting lag)
2.	Modeling Approach
*	Target definition
*	Feature types considered (permits, complaints, incident history)
*	Model(s) evaluated and why
*	How you handled data quality issues and imbalance
3.	Evaluation & Results
*	Metrics chosen and why they align to weekly triage
*	Summary of model performance and limitations
4.	Operational Use
*	What the weekly output looks like (ranked list + “why”)
*	How Safety or Operations would use it
*	How many sites you would flag and why (capacity-based reasoning)
5.	Recommendation
*	Should Suffolk deploy this model today?
*	What risks or limitations should leadership understand?
*	What would you prioritize next with additional time or data?

### Code Expectations
Your submission should include:
*	Reproducible analysis (notebook or scripts)
*	Clear structure and comments
*	Reasonable engineering hygiene (e.g., reproducibility, clarity)
 
### Follow-Up Discussion (Interview)
During the interview, you should be prepared to discuss:
*	How you would productionize this as a data product
*	How you would monitor, iterate, and improve it
*	How you would lead this work with a small team
*	How you would partner with Safety, Operations, and IT
 
Note
There is no single “correct” answer. This exercise is meant to create common ground for discussion in the interview—focus on how you frame the problem, make tradeoffs, and communicate. The data has not been fully vetted, and any quirks should be treated as real-world constraints to surface and address (including noting what additional data would materially improve the outcome).
