# Introduction into prompting

Further resources:

- [Anthropic Prompting Guide](https://docs.anthropic.com/en/docs/get-started)
- [OpenAI Prompting](https://platform.openai.com/docs/guides/text#prompt-engineering)

## Chain of Thought

### Standard prompt

```
A store sells apples at $0.40 each and bananas at $0.60 each. Tom buys 10 fruits in total for $5.20. How many apples and bananas did he buy?
```

### Chain-of-thought prompt

```
A store sells apples at $0.40 each and bananas at $0.60 each. Tom buys 10 fruits in total for $5.20. How many apples and bananas did he buy? Think through this step-by-step.
```

### Model response

```
Let me solve this step-by-step:

1. Define variables: Let a = number of apples, b = number of bananas
2. We know: a + b = 10 (total fruits)
3. We know: 0.4a + 0.6b = 5.2 (total cost)
4. From equation 1: b = 10 - a
5. Substitute into equation 2: 0.4a + 0.6(10-a) = 5.2
6. Simplify: 0.4a + 6 - 0.6a = 5.2
7. Solve: -0.2a = -0.8, so a = 4
8. Therefore: b = 6
9. Verify: 4 apples + 6 bananas = 10 fruits, and $0.4(4) + $0.6(6) = $1.6 + $3.6 = $5.20 ✓

Tom bought 4 apples and 6 bananas.
```

# Few-Shot Learning

### Poor prompt

```
Solve math problems.
```

### Effective few-shot prompt

```
Please solve these problems step-by-step:

Problem 1: If 5x + 3 = 18, what is x?
Step 1: Subtract 3 from both sides. 5x = 15
Step 2: Divide both sides by 5. x = 3

Problem 2: A rectangle has area 24 sq m and perimeter 20 m. Find its dimensions.
Step 1: Let length = l, width = w
Step 2: Area equation: l × w = 24
Step 3: Perimeter equation: 2l + 2w = 20, so l + w = 10
Step 4: From l + w = 10, we get l = 10 - w
Step 5: Substitute: (10-w) × w = 24
Step 6: Expand: 10w - w² = 24
Step 7: Rearrange: w² - 10w + 24 = 0
Step 8: Solve: w = 4 or w = 6
Step 9: If w = 4, then l = 6; if w = 6, then l = 4
Step 10: Both solutions are valid: 4×6 = 24 and 2(4+6) = 20

Now solve this new problem with similar steps:
[YOUR PROBLEM HERE]
```

## Logical Frameworks

### Scientific method framework prompt

```
Approach this question using the scientific method:

1. Observe the problem and gather key information
2. Formulate a hypothesis about the solution
3. Design a test procedure to validate your hypothesis
4. Execute the test and collect results
5. Analyze results and draw conclusions
6. Refine or confirm your hypothesis
```

### Model response

```
Scientific analysis of whether increasing minimum wage reduces employment:

1. Observation: Debate exists about minimum wage effects on employment
2. Hypothesis: A 10% minimum wage increase will not significantly reduce employment
3. Test design: Compare employment rates before/after wage increases across similar regions
4. Results: Data shows varied effects—small decreases in some sectors, no change in others
5. Analysis: Effects are heterogeneous across industries; service sector shows 0.3% decrease
6. Conclusion: The hypothesis is partially supported; effects are sector-dependent and relatively small
```

## Critical Analysis Framework

### TEAR method prompt

```
Analyze this argument using the TEAR method:
T - State the main Thesis/claim
E - Examine the Evidence provided
A - Assess Alternative perspectives
R - Reach a conclusion based on the strength of reasoning
```

### Model response

```
TEAR Analysis of "Social media causes depression in teenagers":

T - Thesis: The claim argues that social media usage directly causes depression in adolescents.

E - Evidence: The argument cites correlational studies showing increased depression rates alongside rising social media use, and limited experimental studies where reducing usage improved mood.

A - Alternatives: Other perspectives include: (1) depressed teens may use more social media, not vice versa; (2) underlying factors like social comparison or cyberbullying, not simply usage time, drive negative outcomes; (3) positive effects exist for some users through community building.

R - Reasoning Assessment: The evidence establishes correlation but insufficient causation. The relationship appears bidirectional and context-dependent rather than universal. A more nuanced thesis about specific usage patterns and risk factors would be better supported by available evidence.
```

## Self-Consistency

### Self-consistency prompt

```
The price of a book is $80. After a 25% discount and then adding 10% tax, what is the final price? Generate three different solution approaches and check if they agree.
```

### Model response

```
Approach 1: Calculate sequentially

- 25% discount: $80 × 0.75 = $60
- Add 10% tax: $60 × 1.1 = $66

Approach 2: Use a combined factor

- Discount factor: 0.75 (keeping 75%)
- Tax factor: 1.1 (adding 10%)
- Combined: 0.75 × 1.1 = 0.825
- Final price: $80 × 0.825 = $66

Approach 3: Calculate total adjustments

- 25% discount means -25% adjustment
- 10% tax means +10% on the discounted price, which is +7.5% of original
- Net adjustment: -25% + 7.5% = -17.5%
- Final price: $80 × (1 - 0.175) = $80 × 0.825 = $66

All approaches give $66, confirming the answer.
```

## Problem Decomposition

### Complex problem prompt

```
A company needs to schedule 3 presentations in 3 different rooms. There are 5 available presenters, and each room needs exactly 1 presenter. How many different scheduling possibilities are there? Break this down into manageable steps.
```

### Model response

```
Let me break this down into smaller steps:

1. First, how many ways can we select 3 presenters from 5?
   This is a combination problem: C(5,3) = 5!/(3!(5-3)!) = 10 ways

2. For each selection of 3 presenters, how many ways can we assign them to 3 specific rooms?
   This is a permutation: P(3) = 3! = 6 different assignments

3. Combine the results: Total possibilities = Step 1 × Step 2
   = 10 × 6 = 60 different scheduling possibilities

Therefore, there are 60 different ways to schedule the presentations.
```

## Verification and Assumptions

### Verification prompt

"After solving this probability problem, verify your solution by checking for errors, ensuring probabilities sum to 1, and confirming all possible outcomes were considered."

### Model response

```
Verification of my solution:

- Are my calculated probabilities between 0 and 1? Yes (0.3, 0.45, 0.25)
- Do all probabilities sum to 1? Yes (0.3 + 0.45 + 0.25 = 1)
- Have I accounted for all possible outcomes? Yes (A, B, and neither)
- Is my conclusion consistent with the calculations? Yes
- Potential error check: I initially assumed events were independent
  Examining the problem statement confirms this assumption is valid

The verification confirms my solution is mathematically sound and complete.
```

## Assumptions prompt

"When analyzing this economic scenario, explicitly state your assumptions and the limitations of your analysis."
