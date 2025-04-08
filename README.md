# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

<hr>

We are comparing two pivot selection strategies:

1. Picking the first element of the subarray as the pivot
2. Picking the median of the first, middle, and last elements of the subarray as the pivot

For Case 1 (first element pivot), any single `n` element is equally likely to be in the first position, so the probability that the first element falls in the good pivot range of $\frac{n}{4} \ \text{to} \ \frac{3n}{4}$ is:
$$
  \text{good pivot chance} = \frac{n}{2} \div n = \frac{1}{2}
$$

Meaning we have a 50% chance for Case 1 (first element pivot) to pick a good pivot.


For Case 2 (median pivot), we choose the medium of the first, middle, and last elements in the subarray. These 3 elements are independently random samples from the subarray.  

There are a couple scenarios for these 3 elements.

1. All 3 elements can be in the good pivot range
2. Only 2 elements are in the good pivot range, and 1 is on the far edges
3. 1 Element is in the good pivot range, and the other 2 are on the far edges (the median ensures at least 1 in the good pivot range)

Scenario 1:

The probability that all 3 elements are in the good pivot range of $\frac{n}{4} \ \text{to} \ \frac{3n}{4}$ is:
$$
  \text{all 3 good pivot chance} = (\frac{1}{2})^3 = \frac{1}{8}
$$

Scenario 2:

The probability that 2 elements are in the good pivot range, and 1 is on one of the edges:
$$
	\text{2 good pivot chance, 1 bad} = (\frac{1}{2})^2 * \frac{1}{4} = \frac{1}{16}
$$

$$
	\frac{1}{16} * \text{2 edge ranges} = \frac{6}{16}
$$

Scenario 3:

The probability that 1 element is in the good pivot range, and 2 are in the edges (both sides)
$$
	\text{6 possible combinations} * [(\frac{1}{4})^2 * \frac{1}{2}] = \frac{3}{16}
$$

Combining All probabilities:
$$
	\text{total probability for median method} = \frac{1}{8} + \frac{6}{16} + \frac{3}{16} = \frac{11}{16} = 68.75 \text{\% chance of having a good pivot}
$$

Therefore choosing the medium of 3 elements has a larger percentage chance of choosing a good pivot point vs the first element.

Intuitively, choosing the median value from a larger spread sample size of elements with this method would result in a larger chance of hitting the middle good pivot range, vs choosing a single random element- so this answer makes sense to me.
