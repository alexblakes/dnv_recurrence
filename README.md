# Thinking about *de novo* recurrence
What is the probabibility of observing a recurrent *de novo* variant in a rare disease cohort?

## Some assumptions
**A human genome has 3 billion base pairs.**
That's the haploid genome length, but for this exercise we don't care which allele the variant falls on.

**There are 3 possible SNVs at each position**

**Each individual carries 100 *de novo* SNVs**
Just to make the maths straightforward.

## The simple case: two individuals
How likely is it that two unrelated individuals carry a matching *de novo* variant?

Let's take **person A** and **person B**.
Person A has 100 *de novo* SNVs in their 3 billion bp genome. 
So does person B.

How likely is is that one of the variants in person B is identical to one of the variants in person A?

The easiest way to frame this is to consider the probability that none of the variants in person B matches any of the variants in person A.
We can break this down for each of the 100 variants, and then combine the probabilities.

### The first variant
What is the probability that the first variant in person B **does** match one of the variants in person A?

$$\frac{100\ opportunities\ to\ match}{(3,000,000,000bp*3\ possible\ SNVs)}=1.1 * 10^{-8}$$

The probability that this variant **does not match** one of the variants in person A is 1 minus this number.
$$ 1 - 1.1 * 10^{-8} $$

### The second variant

Likewise, the probability that the second variant in person B **does not** match one of the variants in person A is:
$$ 1 - 1.1 * 10^{-8} $$

(Technically, because the 100 SNVs are assumed to be different, we should minus one from the denominator in the equation above.
But with numbers at this scale, this doesn't matter.)

### Combining the probabilities of the first two variants
What is the probability that neither the first nor the second variant in person B matches either of the variants in person A?

$$(1 - 1.1 * 10^{-8})  * (1 - 1.1 * 10^{-8}) = (1 - 1.1 * 10^{-8})^{2} = 0.99999998$$

### All 100 variants
What is the probability that none of the 100 variants in person B matches any of the variants in person A?

$$(1 - 1.1 * 10^{-8})^{100}=0.9999989$$

So a match between any two people is highly unlikely.

Conversely, the probability that at least one of the variants matches is 1 minus this number:
$$1-0.9999989 = 1.1*10^{-6}$$

## Extending from two individuals to a large cohort
The GEL *de novo* cohort has around 13,000 trios.
What is the probability that a *de novo* variant will be shared by any two offspring in the cohort (bearing in mind lots of assumptions.)

We already have the probability that any two random people will share at least one *de novo* SNV ($1.1*10^{-6}$).

So we need to ask how many different comparisons can we make between two individuals in a cohort of 13,000 people?

This is 13,000 *choose* 2:
$$ _{13,000}C_{2} = \frac{13000!}{2! * (13000-2)!} = 84493500 $$

I.e. we need to make 84,493,500 pair-wise comparisons.
To find the **expected number** of matches, we multiply the probability of a match between any two individuals, by the number of pairwise comparisons.

$$ 84493500 * 1.1*10^{-6} = 93.882 $$

In this cohort, we would expect to find 94 pairs who share at least 1 *de novo* SNV.
This is the **expected number** of matches.
(This is not quite the same as the number of *de novo* SNVs we expect to see in >1 individual... But it's not far off.)

## The probability of observing a match in a large cohort
We already know the probability of **not making a match** between any two random individuals ($(1 - 1.1 * 10^{-8})^{100}=0.9999989$)

By extension, the probability of not matching across anyone in this cohort is:
$$ 0.9999989^{84493500} = 1.69 * 10^{-41}$$

I.e. very small indeed!

So we are almost certain to find at least one pair of individuals who have a matching variant *de novo* SNV in a cohort of 13,000.

## What is the smallest size of cohort for which you would expect a 50% probability of at least one recurrent DNM?
There is a shortcut to calculate this number, although I am not sure how it is derived.

The probability of two random people matching is $1.1*10^{-6}$

Expressed as a fraction, this is approximately $\frac{1}{900000}$

The number needed for the probability of a match to be approximately 50% is (using the shortcut):
$$1.2 * \sqrt{900000} = 1138.42$$

Which, to me at least, is surprisingly small.