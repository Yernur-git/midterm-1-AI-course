# Midterm 1: answers

GitHub username: yernur-git
Session code: maple-66
Fingerprint: c318f7ae

> Fill in the three lines above from `my_data/DATA.md`. Do not rename headings or table columns: a script reads the numbers.
> Write only in the empty cells and lines. Percentages as 0.78 or 78 %, money as plain numbers.

## AI-use declaration

(About half a page: which assistants or tools you used and for what. If you used none, say so.)

## Part 1: Retrieval and cost decision

### 1a. Metrics (all 60 questions)

| config | recall@1 | recall@3 | recall@5 | MRR@10 |
|---|---|---|---|---|
| A | 0.667 | 0.733 | 0.800 | 0.713 |
| B | 0.400 | 0.633 | 0.667 | 0.515 |

### 1b. Recall and 95 % Wilson interval of each candidate (recall at its own k)

| candidate | recall@k | lower | upper |
|---|---|---|---|
| A, k=3 | 0.733 | 0.610 | 0.829 |
| A, k=5 | 0.800 | 0.682 | 0.882 |
| B, k=3 | 0.633 | 0.507 | 0.744 |
| B, k=5 | 0.667 | 0.541 | 0.773 |

### 1c. Annual model cost in USD

| candidate | annual cost |
|---|---|
| A, k=3 | 14600.06 |
| A, k=5 | 19498.16 |
| B, k=3 | 9386.01 |
| B, k=5 | 10808.08 |

### 1d. Decision (at most 150 words)

Chosen candidate: B, k=3B, k=3

i choose B, k=3. both A options are over the annual budget, so i cannot choose them. both B options are within the budget. B, k=3 costs less: $9,386.01 instead of $10,808.08 for B, k=5. the intervals of B, k=3 and B, k=5 overlap, so i cannot say that k=5 is clearly better. for B, k=3, recall@3 is 65% for EN, 75% for RU, and 50% for KK. kazakh users are served the worst, so this language needs more attention

### 1e. Next measurement (at most 60 words)

i would test more questions in each language, especially in Kazakh. this can show more clearly if B, k=5 is really better than B, k=3 or if the difference happened by chance

## Part 2: A document pipeline you can defend

### 2a. Numbers

| pipeline | overall accuracy | weakest cell (language, condition) | accuracy there | lower | upper | annual cost |
|---|---|---|---|---|---|---|
| H | 0.894 | KK, degraded | 0.800 | 0.627 | 0.905 | 64547.51 |
| L | 0.806 | KK, degraded | 0.533 | 0.361 | 0.698 | 21600.00 |

Personal-data pages per year sent abroad under H: 465375

### 2b. Memo (at most 300 words)

i would choose pipeline L. H has better overall accuracy: 89.4%, while L has 80.6%. the weakest group for both is Kazakh degraded invoices. H gets 80.0% [62.7%, 90.5%], and L gets 53.3% [36.1%, 69.8%]. the intervals overlap, so this test does not clearly prove the difference
H sends scans abroad. about 465,375 pages with names and IIN would leave Kazakhstan each year. i need to check where the vendor stores the scans, who can access them, and how long they keep them
L runs on the bank's server in Kazakhstan and costs less: $21,600 instead of $64,547.51. i would use access control, encryption, audit logs, deletion rules, and block external transfers. the main risk is weak results on bad Kazakh scans, so they should be checked manually

## Part 3: Explain your own numbers

### Q1

Number:
Why (at most 40 words): the total token ratio is different because input and output tokens have different prices. output tokens cost more, so the number of output tokens affects the final bill more

### Q2

Number:
Why (at most 40 words): the sentence starts after the model limit of 512 e5 tokens. a question matching only this sentence cannot retrieve the chunk. the model truncates the end silently, so there is no visible error

### Q3

Number:
Why (at most 40 words): top-p removes low-probability tokens and then renormalises the rest. lowering temperature changes all probabilities but does not delete tokens from the distribution


### Q4

Number:
Why (at most 40 words): i left out arithmetic sequences and multiplication because they use rules, not facts from training. i used birthdays and account numbers. “never invent a fact” cannot add missing knowledge; it can only make the model refuse

### Q5

Number:
Why (at most 40 words): this model has 4.8 times more tokens per parameter than chinchilla, so it is over-trained by this rule. chinchilla said that models like gpt-3 were under-trained because they had too few training tokens
