Shareable Cuts:

# Week 8 Demo Outline & Shareable Cuts

1. The question (60 sec)
FlyRank's content teams can't manually review every page in a growing portfolio.
Can pre-decision signals — position, depth, age — help prioritize which pages
are quietly declining, without the model just training on the outcome it's
supposed to predict?

2. The method (90 sec)
- Built a proxy label from first-half vs. second-half clicks within one month
- Compared a rule baseline, logistic regression, and a client-grouped Random
  Forest on the *same* split
- Deliberately added a label-derived column to prove leakage would be caught
  (AUC jumped toward 1.0) — then removed it and kept the honest number

3. One chart (60 sec)
Show the AUC comparison chart — rule baseline vs. logistic regression (0.670)
vs. Random Forest across three seeds (0.785–0.850). The model beats both
baselines, but the seed-to-seed spread is a real caveat, not swept under the rug.

4. One honest result (60 sec)
The model's predicted probabilities rarely exceeded 0.53 — even the "riskiest"
pages weren't flagged with high confidence. That's why the final output is a
*ranking*, not a hard classifier: built for a human to review top candidates,
not to auto-flag pages as declining.

5. One recommendation (30 sec)
Ship it as a monthly-refreshed priority queue for the content team — 1,776
pages flagged `VISIBLE_BUT_AT_RISK`, 1,242 `STRIKING_DISTANCE_DECLINING` — with
mandatory human review before any edit, and a re-validation check against the
sealed June month before anyone trusts it further.



## Shareable Cuts

Social post (methodology-focused):

Spent 7 weeks building a page decline classifier from raw search performance
data — and the most useful thing I found wasn't the model, it was catching my
own leakage. Deliberately injected a label-derived feature just to watch AUC
jump toward 1.0, confirmed the trap worked, then threw it out and reported the
honest 0.670 baseline instead. Final model hit 0.79–0.85 AUC, but with probabilities rarely above
0.53, so it ships as a ranking for human review, not an autopilot. Rigor over
a flashier number.

Employer-facing summary (3 sentences):

I built a client grouped Random Forest classifier to rank content pages by
decline risk, using one month of FlyRank's anonymized search performance
warehouse data and five pre decision signals (position, depth, age, type,
intent). The model outperformed both a rule-based and logistic-regression
baseline (AUC 0.79–0.85 vs. 0.670) while surviving a deliberate leakage audit
and a client-grouped validation design to avoid overstating its accuracy. The
output is a monthly refreshable, human reviewed priority queue for FlyRank's
content team, with explicit no-go rules for where the model should not be
trusted.
