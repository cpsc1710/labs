# CPSC 1710 Midterm Practice

**Fall 2026**

This practice set helps you prepare for the paper-and-pen midterm covering course material through Week 5. It illustrates several question formats and levels of detail, but it is not a preview of the exact exam length, wording, or topic distribution.

Try the questions without the answer key first. A focused attempt should take about 45–60 minutes.

## What we mean by pseudocode

Pseudocode communicates the steps of a solution clearly. It does **not** need to be valid Python.

You may use plain English, Python-like notation, a diagram, or a mixture. We look for:

- the correct sequence of operations;
- meaningful inputs, outputs, and intermediate values;
- correct control flow, such as a loop or condition when one is needed; and
- enough detail that another person could follow the procedure.

Exact punctuation, memorized library names, and perfect Python syntax are not required unless a question explicitly asks for Python. For example, this is useful pseudocode:

```text
for each adjacent pair of tokens:
    add 1 to the count for that pair

for each current token:
    divide its pair counts by their total
```

This is too vague to show the procedure:

```text
Process the tokens and calculate probabilities.
```

---

## A. Read and explain pseudocode

### Question 1

Add a short comment explaining what each line accomplishes.

```python
tokens = text.lower().split()
vocab = sorted(set(tokens))
word_to_id = {word: i for i, word in enumerate(vocab)}
token_ids = [word_to_id[word] for word in tokens]
```

1. `tokens = ...`:
2. `vocab = ...`:
3. `word_to_id = ...`:
4. `token_ids = ...`:

### Question 2

Explain the role of each marked step in this training loop.

```text
for each batch of inputs and targets:
    predictions = model(inputs)                 # A
    loss = loss_function(predictions, targets)  # B
    clear_old_gradients()                       # C
    calculate_gradients(loss)                   # D
    update_weights()                            # E
```

What is happening at A, B, C, D, and E?

---

## B. Complete the pseudocode

### Question 3

Complete the missing steps for a bigram language model.

```text
tokens = tokenize(text)
bigram_counts = empty dictionary with default count 0

for i from 0 to length(tokens) - 2:
    current_token = tokens[i]
    next_token = tokens[i + 1]
    Step 1: ______________________________________________

bigram_probabilities = empty dictionary

for each current_token that appears in bigram_counts:
    Step 2: ______________________________________________
    for each possible next_token after current_token:
        Step 3: __________________________________________
```

### Question 4

Complete the generation loop. Assume `next_token_probabilities[current_token]` returns a probability distribution.

```text
current_token = choose_starting_token()
generated = [current_token]

repeat num_tokens_to_generate times:
    probabilities = ______________________________________
    next_token = _________________________________________
    _________________________________________
    _________________________________________

return join(generated)
```

---

## C. Trace a model by hand

### Question 5

Consider the scalar RNN update

```text
h_t = Wx × x_t + Wh × h_(t-1) + b
```

Use:

- `Wx = 2`
- `Wh = 0.5`
- `b = -1`
- `h_0 = 2`
- inputs `x_1, x_2, x_3 = 1, 3, 0`

Calculate `h_1`, `h_2`, and `h_3`. Show the substitution at each step.

### Question 6

A two-number hidden state can generate Fibonacci numbers without training. Let

```text
h_t = [F_t, F_(t+1)]
h_(t+1) = Wh @ h_t
```

1. Give an initial hidden state that begins with `0, 1`.
2. Fill in the four entries of `Wh` so that the next state is `[F_(t+1), F_t + F_(t+1)]`.
3. Show the first four state transitions.
4. Which component of the state should we read to obtain `0, 1, 1, 2, 3, ...`?

```text
Wh = [[__, __],
      [__, __]]
```

---

## D. Sequences, tokens, and attention

### Question 7

Annotate the RNN diagram.

```text
h_0 → [RNN] → h_1 → [RNN] → h_2 → [RNN] → h_3
       ↑                ↑                ↑
       A                B                C
```

1. What are A, B, and C?
2. What does the hidden state carry from one step to the next?
3. Are the three RNN boxes three independently trained models, or repeated uses of the same model parameters?

### Question 8

Compare character-, word-, and subword-level tokenization. For each method, give:

- one advantage;
- one disadvantage; and
- the likely effect on vocabulary size and sequence length.

### Question 9

An attention head has already calculated these attention weights:

```text
weights = [0.75, 0.25]
V_1 = [4, 0]
V_2 = [0, 8]
```

1. Calculate the weighted output `0.75 × V_1 + 0.25 × V_2`.
2. What does the larger weight on `V_1` mean conceptually?
3. In a decoder-only language model, why do we prevent a token from attending to future tokens during training?

---

## E. Short-format practice

### Question 10 — Multiple choice

Which task is a classification problem?

A. Predict tomorrow's temperature  
B. Predict the selling price of a house  
C. Decide whether an image contains a cat or a dog  
D. Estimate the number of minutes a trip will take

### Question 11 — Multiple answer

Which statements about training, validation, and test data are correct? Select all that apply.

A. Training data is used to update model parameters.  
B. Validation data can guide model and hyperparameter choices.  
C. Test data should be repeatedly consulted while designing the model.  
D. A final test set estimates performance on unseen data.  
E. Randomly duplicating validation examples into the training set keeps the evaluation independent.

### Question 12 — Ordering

Put these training steps in order:

- ___ Calculate the loss.
- ___ Update the weights.
- ___ Make predictions using the current weights.
- ___ Calculate gradients of the loss.
- ___ Clear gradients left from the previous iteration.

### Question 13 — Numeric comparison

For two image vectors

```text
a = [1, 2, 4]
b = [2, 0, 4]
```

1. Calculate the L1 distance.
2. Calculate the squared L2 distance, `sum((a - b)^2)`.
3. Which vector positions contribute no distance, and why?

### Question 14 — True or false

Mark each statement true or false and correct the false statements.

1. Two linear layers with no activation between them can represent any nonlinear boundary.
2. ReLU introduces a nonlinearity into a neural network.
3. An RNN uses a hidden state to carry information across positions in a sequence.
4. A token ID of 900 represents a token with nine times as much meaning as token ID 100.
5. Raising generation temperature generally makes the output distribution flatter and sampling less predictable.

### Question 15 — Brief explanation

In two or three sentences, explain the difference between:

1. tokenization and an embedding;
2. greedy next-token selection and sampling; and
3. an RNN's recurrent memory and attention's ability to look back.

---

## Study suggestions

- First attempt the practice without notes or AI assistance.
- Explain each answer aloud or to a classmate; recognition is easier than recall.
- Rework mistakes from quizzes, labs, and homeworks.
- Practice tracing small calculations on paper.
- When writing pseudocode, name what each value represents instead of trying to remember exact library syntax.

*Drafted by Codex (OpenAI), based on the direction of Xiuye Chen.*
