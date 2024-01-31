# Lab Assignment for Week 04
## Simulation-based hypothesis testing for coin flip sequences
## Due on [Canvas](https://psu.instructure.com/courses/2306358/assignments/15951415) on Wed., Feb. 7 at 11:59pm

The main objective of today's lab is to test a hypothesis using a statistic that is very difficult to analyze theoretically but relatively easy to simulate.  A secondary objective is to give you a bit of practice writing and adapting code; if you're new to programming, this assignment may stretch you a bit but please seek help as needed because we don't intend for the programming to become a major obstacle.

**Before you start**:  Without using any kind of coding, type a sequence of 200 coin flips by hand, using the letters H and T, that you generate yourself.  Your goal is to mimic a random sequence of coin flips as well as you're able to do so.  Yes, it's a bit tedious, but there's a point!

Once you've written down your sequence, count the number of changes (from Heads to Tails or Tails to Heads) in your sequence.  For example, the 8-flip sequence H H T T H H T T has three changes.

**A quick note on the big picture here**:  An old trick sometimes used by instructors of probability classes is to assign students, as homework, to flip a coin a few hundred times and record the results.  It's often the case that the instructor can detect those who actually did the assignment and those who simply ignored the instructions and wrote down what they thought to be a random-looking sequence of coin flips.  Now that we've begun Chapter 11, we have the tools available to try playing the role of the instructor using sheer computing power along with a bit of knowledge of testing hypotheses.

Nearly all of the code you should need is in [Section 9.3](https://inferentialthinking.com/chapters/09/3/Simulation.html) and [Section 11.1](https://inferentialthinking.com/chapters/11/1/Assessing_a_Model.html) of the textbook.  When you turn in your work, it should not contain any irrelevant text and code boxes; therefore, if you use the textbook as the basis for your work, please delete text and code boxes unrelated to the assignment before you turn in your lab.

**Objective**:  Simulate the distribution of changes for a sequence of 200 coin flips under a "model" (or null hypothesis) that says the flips are truly random.  Then compare the statistic you have generated by hand with that distribution to see whether that statistic seems suspiciously too extreme to have arisen from that model.

**Your assignment** is as follows:

1. In a text box, copy-paste your 200-flip sequence that you generated and also report the value of the number of changes you counted by hand in the "before you start" section.  As always, whatever you write should use clear, complete sentences. 

2. Write a bit of code that will simulate 200 random, independent coin flips.  Check Section 9.3 for some guidance on this.  Demonstrate your code by including output from one sequence of 200 flips.

3. Write code that will count the number of changes (Heads to Tails or Tails to Heads) in a sequence of coin flips.    **Hint**:  Start with the code in [Section 9.3](https://inferentialthinking.com/chapters/09/3/Simulation.html) that converts an array of `'Heads'` and `'Tails'` to `True` and `False` using `sequence=='Heads'`.  This code then applies the `np.count_nonzero` method to return the number of `True` values.  Instead of `np.count_nonzero`, apply [`np.diff`](https://numpy.org/doc/stable/reference/generated/numpy.diff.html), which gives a new array of length one less than the original array in which the *i*th entry is `True` whenever there is a change (from `True` to `False` or `False` to `True`) at the *i*th place.  Applying `np.count_nonzero` to the result gives the total number of changes in the original array. 

4. Simulate at least 10,000 sequences of 200 coin flips, and produce a histogram of the change statistics simulated under the model of random, independent flips.  Include the observed value of the change statistic from part 1 as a red dot, as seen in Section 11.1.6.

5. In statistics, the definition of a p-value is this:  The p-value is the probability under the hypothesized model of a statistic at least as extreme as the one observed.  Use your output to calculate a p-value in this example.  **Hint**: The "hypothesized model" here is that the flips are truly random and independent.  Your histogram in step 4 therefore represents the probability distribution of the statistic under the hypothesized model, so your p-value should equal the fraction of that histogram at least as extreme as the point represented by the red dot.  In this case, "extreme" could be interpreted to mean far away from the histogram's center in **either** direction, but since this concept is new in this class, it's okay here if you simply calculate the proportion of your histogram in the smaller part that is at least as extreme as the observed statistic.

6. As an example, in Section 11.1.6., the red dot is entirely separated from the histogram, which means that the proportion of the histogram of model-based statistics that are at least as extreme as the observed statistic (the red dot) is zero.  Therefore, the simulation-based p-value in Section 11.1.6 could be reported as zero or, if you want to be really precise, as "< 0.0001" (that is, less than 1/10000).

7. In a text box, explain your reasoning as to whether you think this procedure shows that the hypothesized model can be rejected as having led to the sequence you produced by hand at the beginning.  **Hint**: If a p-value is very small, we have evidence to reject the hypothesized model.  Traditionally, "very small" has been interpreted to mean "less than 0.05".  

8. _Optional, for up to 1 extra point_.  Use a different statistic to test your hand-created sequence:  The length of the longest string of flips without a change.  Follow the same procedure as above, namely, simulate the distribution of the statistic from the model and then compare the observed statistic to obtain a p-value.

9. _Optional, for up to 1 extra point_.  In a sequence of n coin flips, consider the question of the expected number (mean) of the longest string of flips without a change.  Simulate an approximation to this mean for n=100, 200, ..., 1000 and plot the result graphically.   

When you've completed this, you should select "Print" from the File menu, then somehow save to pdf using this option.  The pdf file that you create in this way is the file that you should upload to Canvas for grading.  Recall that sometimes the right side of the notebooks are chopped off by this print procedure, but we have found that if you can select the "A3" paper size from the advanced options, this often seems to solve the problem.
