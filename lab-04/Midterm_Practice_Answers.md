# CPSC 1710 Midterm Practice Answer Key

**Fall 2026**

Try the questions before reading this key. Many pseudocode questions have more than one correct expression. The examples below show the required ideas, not the only acceptable wording or syntax.

---

## A. Read and explain pseudocode

### Question 1

1. Convert the text to lowercase and split it into word tokens at whitespace.
2. Remove duplicate tokens and sort the resulting vocabulary. Sorting makes the ID assignment reproducible.
3. Create a dictionary that maps every vocabulary word to a unique integer ID.
4. Replace each token in the original sequence with its corresponding ID.

### Question 2

- **A:** Run the model's forward pass to produce predictions from the inputs.
- **B:** Measure the difference between the predictions and the targets.
- **C:** Remove gradients retained from the previous iteration so they do not accumulate unintentionally.
- **D:** Use backpropagation to calculate how the loss changes with respect to the trainable parameters.
- **E:** Use the gradients and the optimizer's rule to adjust the parameters.

The essential order is forward pass, loss, clear old gradients, backpropagation, and update. Some frameworks clear gradients at the end of the previous iteration instead; that is also correct if they are cleared before the next backward pass.

---

## B. Complete the pseudocode

### Question 3

```text
tokens = tokenize(text)
bigram_counts = empty dictionary with default count 0

for i from 0 to length(tokens) - 2:
    current_token = tokens[i]
    next_token = tokens[i + 1]
    Step 1: add 1 to bigram_counts[current_token, next_token]

bigram_probabilities = empty dictionary

for each current_token that appears in bigram_counts:
    Step 2: total = sum of counts for pairs beginning with current_token
    for each possible next_token after current_token:
        Step 3: probability = count(current_token, next_token) / total
```

A nested-dictionary representation is equally valid. The required ideas are counting adjacent pairs and normalizing each current token's counts so its next-token probabilities sum to 1.

### Question 4

```text
current_token = choose_starting_token()
generated = [current_token]

repeat num_tokens_to_generate times:
    probabilities = next_token_probabilities[current_token]
    next_token = sample according to probabilities
    append next_token to generated
    current_token = next_token

return join(generated)
```

Choosing the highest-probability token instead of sampling describes greedy generation. It is a valid algorithm, but it does not implement the sampling requested here.

---

## C. Trace a model by hand

### Question 5

```text
h_1 = 2(1) + 0.5(2) - 1
    = 2

h_2 = 2(3) + 0.5(2) - 1
    = 6

h_3 = 2(0) + 0.5(6) - 1
    = 2
```

Therefore, `h_1 = 2`, `h_2 = 6`, and `h_3 = 2`.

### Question 6

Use

```text
h_0 = [0, 1]

Wh = [[0, 1],
      [1, 1]]
```

The first new component copies the old second component. The second new component adds the two old components.

```text
[0, 1] → [1, 1] → [1, 2] → [2, 3] → [3, 5]
```

Reading the first component, including the initial state, gives `0, 1, 1, 2, 3, ...`.

An equivalent convention such as storing `[F_t, F_(t-1)]` with a different transition matrix is also correct when it is explained and produces the sequence.

---

## D. Sequences, tokens, and attention

### Question 7

1. `A = x_1`, `B = x_2`, and `C = x_3`, the inputs or input-token representations at the three time steps.
2. The hidden state carries a fixed-size summary of information from earlier positions.
3. The boxes are repeated uses of the same RNN cell with shared parameters, not three independently trained models.

### Question 8

One reasonable comparison is:

| Method | Advantage | Disadvantage | Typical vocabulary and sequence |
|---|---|---|---|
| Character | Can represent arbitrary text with a very small vocabulary | Long sequences and weak word-level units | Small vocabulary, long sequence |
| Word | Tokens are easy for people to interpret | Very large vocabulary and difficulty with unseen or unusual words | Large vocabulary, short sequence |
| Subword | Balances reusable pieces with reasonably short sequences; can construct unfamiliar words | Boundaries can look unintuitive and depend on the learned tokenizer | Medium or large vocabulary, medium-length sequence |

Exact sizes depend on the language, corpus, and tokenizer.

### Question 9

1. `0.75[4, 0] + 0.25[0, 8] = [3, 0] + [0, 2] = [3, 2]`.
2. For this query, the model is drawing more information from `V_1` than from `V_2`.
3. During next-token training, future tokens are the answers the model is supposed to predict. A causal mask prevents information leakage and preserves the rule that generation can depend only on tokens already available.

---

## E. Short-format practice

### Question 10

**C.** Cat versus dog is a choice between discrete classes. The other examples predict continuous quantities and are regression tasks.

### Question 11

**A, B, and D.**

The test set should remain separate during model development. Moving validation examples into training data would make validation results less independent.

### Question 12

1. Make predictions using the current weights.
2. Calculate the loss.
3. Clear gradients left from the previous iteration.
4. Calculate gradients of the loss.
5. Update the weights.

As noted in Question 2, clearing gradients at the end of the preceding iteration is an equivalent implementation.

### Question 13

The element-wise differences are `[-1, 2, 0]`.

1. L1 distance: `|-1| + |2| + |0| = 3`.
2. Squared L2 distance: `(-1)^2 + 2^2 + 0^2 = 5`.
3. The third position contributes no distance because both vectors contain `4` there.

If ordinary L2 distance were requested, the answer would be `sqrt(5)`. This question asks for squared L2 distance.

### Question 14

1. **False.** Composing linear layers without a nonlinear activation is still a linear transformation.
2. **True.**
3. **True.**
4. **False.** Token IDs are identifiers, not ordered measures of meaning.
5. **True.** A higher temperature generally flattens the probability distribution and increases randomness, assuming the usual temperature transformation.

### Question 15

1. **Tokenization versus embedding:** Tokenization divides text into units and assigns IDs. An embedding maps an ID to a learned vector that can represent useful relationships.
2. **Greedy selection versus sampling:** Greedy selection always chooses the highest-probability next token. Sampling draws from the full distribution, so lower-probability tokens can sometimes be selected.
3. **Recurrent memory versus attention:** An RNN repeatedly updates a fixed-size hidden state as it moves through the sequence. Attention lets a position directly weight and combine information from earlier positions rather than relying only on a repeatedly updated summary.

Equivalent explanations that correctly distinguish each pair should receive credit.
