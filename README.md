# econ3916-lab17-classification
# Classification: When 90% Accurate Is Worthless

## Objective
I used simulated loan applications to show why accuracy is the wrong score for a rare outcome like default, and how to choose a decision threshold from the cost of each error.

## Methodology
- Simulated 6,000 loan applications with a default rate of 9.6%, so a rule that approves everyone is 90.4% accurate.
- Fitted a logistic regression and compared it with that do-nothing rule at the usual 0.5 threshold.
- Read the coefficients as log-odds and as odds ratios, and applied one odds ratio (1.63 for one more prior default) at three different starting probabilities to see that it means different changes in probability.
- Traced precision and recall across six thresholds.
- Priced the two errors, a missed default and a wrongly declined applicant, and chose the threshold that minimises the expected cost, searching on the training applicants and pricing the result once on the test applicants.
- Wrote a small function, precision_recall_at(), that gives a classifier's precision and recall at any threshold.

## Key Findings
- At the usual 0.5 threshold the model's accuracy was 90.4%, the same as approving everyone, because it made 0 predicted defaults.
- The cost-minimising threshold was 0.121, against a closed-form threshold of 0.118 from the two costs alone.
- Its expected cost was 944 per applicant, against 1,147 at 0.5.
- At the closed-form threshold, precision was 0.181 and recall was 0.477.
