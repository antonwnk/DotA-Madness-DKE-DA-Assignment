# DotA Madness

## Data Analysis (KEN3450) assignment code / write-up

### Approach
The analysis was split into two sections, each answering different questions.
Consequently, the code is also split into 2 files.

### Common part
Both notebooks start from a common code-base which covers the integration of several different data sources and provides functions to allow querying the data.

### Part 1
Attempts to answer the following question: 

**Do heroes cluster by stat type (*Strength/Agility/Intelligence*) and/or hero role (*Carry/Support/Initiator/Nuker etc.*) when projected into a lower dimensional space based on either one of:**
* ***computed statistics* (average number of kills/deaths/assists, avg. number of last hits/denies etc.),**
* ***predefined hero stats* (Str/Int/Agi gain, attack speed, movement speed etc.) or**
* ***both***.

First, heroes which are highest and lowest in the computed statistics are presented. The results seem to be consistent with what a DotA player would also know from gameplay experience (most gold for Alchemist, most last hits for Magina, least wards placed for Spectre, least played hero Chen). <br>
Scatter plots are also generated for each pair of variables along with histograms for each variable and the obvious linear relationships can be seen where the variables have causal relationships (strength stat and hero health / last hit count and gold earned etc.)

Second, PCA models are built on the three variants of the dataset: **only statistics**, **only hero stats** and **both**.
Projections on the first 2 principal components with the data colored by both hero stat and role are presented, along with the corresponding loading plots.

While the hero roles fail to emerge as clusters in all of the PCA models, the hero stat is nicely clustering in all three.
The hero stat would definitely be expected to cluster on the models including the hero stats values, as they have a direct relationship, but some degree of separation can be observed in the first principal component of the model only containing hero statistics.


### Part 2
The second part attempts to answer:

**Which hero combinations, in terms of stat (*Strength/Agility/Intelligence*) or role (*Carry/Support/Initiator/Nuker etc.*), is best in regards of win-rate?**

The game statistics are used to estimate win-rates for each observed combination and once again, common knowledge seems to be reflected: Balanced team compositions perform well while unbalanced ones not (e.g. *Carry/Carry/Carry/Carry/Carry* or *str/str/str/str/str* are amongst the worst performing compositions).
