# A Hitchhiker's Guide to Statistical Comparisons of Reinforcement Learning Algorithms
#### Colas, Sigaud, Oudeyer (2019)

In this work, the authors discuss some considerations in order to guide the reader towards more reliable comparisons of two RL algorithms. They first define a few fairly basic statistics concepts which I thought were a useful reminder. Then the authors compare several statistical tests and end up generally recommending the use of Welch's t-test with confidence level smaller than 0.05. Finally they give recommendations on how to build and compare learning curves for different RL algorithms and warn against multiple comparisons.

**Reasonnable assumptions for RL experiments (trainings)**
* RL performances are measured at random and independently of one another
* The samples are not paired between algorithms
* The samples have the same size between the two algorithms (controlled by experimenter)

**Potentially violated assumptions for RL experiments**
* Normal distributions of performances (very commonly in RL, we have bimodal, skewed or truncated distributions of performances)
* Continuous distributions (very often the support of performances distributions is bounded: reward function, finite episodes)
* Known standard deviations (often not the case)
* Equal standard deviations between algorithms (often not the case)

**Conclusions and recommendations**
* They found the t-test and Welch's t-test more robust to violations of its assumptions than other tests.
* Recommend sample size of N=100 for relative effect size of 0.5, N=20 for relative effect size of 1 and N=10 for relative effect size of 2.

**On learning curves**
* One point of the curve is the performance average of *E* offline (deterministic) evaluation episodes
* A collection of those point throughout training gives the learning curve
* By collecting multiple learning curves (from training runs with different seeds) we can represent the algorithm performance as the mean of those learning curves. The standard deviation (SD) across those curves represents the variability of the performances and the standardf error (SE) represent the uncertainty on the mean estimate. Note that those two should be used when performances are approximately normally distributed across different training runs. When it is not normal, interpercentile ranges are preferred (10%-90%). For small sample sizes (number of training runs smaller than 10) one can consider plotting them all directly along with their mean curve.

**Multiple tests**
Finally, the authors suggest that one could perform multiple statistical tests along the whole curves rather than simply for final performance. However, this approach would be subject to some pitfalls related to multiple comparisons (see supplementary materials).
