### What I learned from this run

The silhouette comparison selected **k = 2**, with a mean of 0.219 on 1,000 sampled fitting loans. The gap between the two highest silhouette scores was 0.031. The curve's bend heuristic points to k = 3. It does not agree with the silhouette choice, so I would not present k as an obvious answer. These checks describe the grouping under my chosen features and transformation; they do not establish a true number of borrower types.

The individual silhouette plot adds some context: 11.0% of the evaluated fitting loans had negative silhouettes. The reserved-loan silhouette was 0.229. I would read those results together with the cluster sizes and profiles. The PCA picture retains 58.0% of the transformed feature variation, so it only shows part of the space used by K-means.

Scaling changed the assignments. Relative to the main log-and-standardized grouping, original units gave ARI -0.020; standardization without logs gave 0.423. These values show how sensitive the groups are to my representation of the loans. They do not show which version predicts repayment best.

The largest fitting group was Cluster 1, with 4,963 loans. Its median loan amount was $16,000, annual income was $74,000, DTI was 19.0, and FICO was 685. Those original-unit summaries help me explain what the group contains without treating its cluster number as a risk score.

Changing the initialization seed produced reserved-assignment ARIs from 0.935 to 0.990. Refitting preprocessing and K-means on 80% of the fitting loans produced ARIs from 0.893 to 0.982. These are only three checks of each kind, but they show how much the assignments move under these changes. I kept the reserved loans out of fitting and did not adjust k after seeing them.

After fixing the groups, the highest observed charge-off share in the reserved data was in Cluster 1: 21.9%, based on 1,235 loans. The lowest was in Cluster 2: 17.1%, based on 765 loans. That is a descriptive gap of 4.7 percentage points. I would check the intervals and group sizes before reading much into that difference. The outcomes did not determine the clusters, and these percentages are not a validated prediction rule.

For my capstone, the useful part is having groups I can compare and ask better questions about. I would next check whether similar profiles appear in later-issued loans and whether the differences remain. I would not use a cluster label by itself to decide how a borrower should be treated.
