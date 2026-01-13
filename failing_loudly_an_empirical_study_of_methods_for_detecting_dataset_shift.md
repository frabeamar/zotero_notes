BBSD: black box shift detection

distribution of the source labels differs wrt distrbution of the target labels

MMD = take feature -> transform via kernel - > calculate the means - > and the differnce

two sample test can be taken via a permutation test

permutation test = select samples at random and you calculate your statistics.   
p\_value = n\_test > Tobs / num\_permutations

for mmd you randomly shuffle the labels (test stastistics, vs target statistics)

Chi-squared test

- you expect the same distribution of classes between your test and reference set
- when SAMPLING from a normally distributed population, the square of the samples follows the chi squared distribution