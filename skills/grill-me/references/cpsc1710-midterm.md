# CPSC 1710 midterm: what to practise and where it lives

Read this when the student is preparing for the CPSC 1710 midterm (Fall 2026). It tells you the exam's shape, the topics week by week, and where each topic is in the course folder. Paths assume the course folder layout from the setup guide, with the labs site saved under `course/labs/`. If a path is missing, look for the same file elsewhere in the folder, or ask the student.

## The exam

- Paper and pen, closed book, in class. No AI and no notes.
- It covers the course through Week 5.
- Pseudocode is welcome. Valid Python is not required.
- The date, length and point values are on Canvas. Do not guess them. If the student asks, say you do not know and point them to Canvas.

You have not seen the exam. Base your questions on the practice sets and the course materials.

## Question formats

These are the formats in the course's own practice set. Use all of them.

- Multiple choice, and multiple answer ("select all that apply")
- True or false, with a correction for the false ones
- Put steps in order
- Fill in the blank
- Numeric: trace a small calculation by hand and show the substitution
- Pseudocode: add a comment to each line, complete missing steps, or write it yourself
- Brief explanation in two or three sentences

## Pseudocode: the four checks

1. The steps are in the right order.
2. The values have names.
3. Loops and conditions are shown where they are needed.
4. Another person could follow it.

Plain English is fine. A line such as `vocab = build_vocab(tokens)` is not enough, because it names the step without saying how it is done. Everyday helpers (lowercase, split, sort, join, add up, count) may be assumed.

## The course's own practice material

Use these as the standard for level and wording. Do not show an answer key before the student has attempted the question.

| File | What it is |
|---|---|
| `course/labs/lab-04/Midterm_Practice_Questions.md` | 15 questions in every format, plus the pseudocode expectations |
| `course/labs/lab-04/Midterm_Practice_Answers.md` | answer key for those |
| `course/labs/lab-05/Pseudocode_Practice_Questions.md` | 9 pseudocode problems |
| `course/labs/lab-05/Pseudocode_Practice_Answers.md` | answers, what we look for, and a common slip for each |

If the student has not done these yet, recommend them: on paper, without notes, then check. Your questions should add to them, with new numbers and new wording.

## Topics, week by week

For each topic, the "ask about" line gives ideas that make good questions. Start with the idea, then move to a small calculation or a piece of pseudocode.

### Week 1. What deep learning is (Lab 1, Homework 1)
- Classification and regression. Ask about: which is which, with everyday examples.
- Training, validation and test data. Ask about: what each is for, and why a model is judged on data it has not seen.
- Using a pretrained model (transfer learning). Ask about: what is reused and what is trained.
- Where: `course/labs/lab-01/`

### Week 2. A classifier from one feature (Lab 2, Homework 2)
- A decision rule or threshold on one number, and what a decision boundary is.
- Weights and a bias. Ask about: what changing each one does.
- Where: `course/labs/lab-02/`

### Week 3. Handwritten digits (Lab 3, Homework 3)
- An image as numbers: 28 × 28 pixels is 784 numbers.
- Comparing images: L1 distance, squared L2 distance, and the "average 3" classifier. Ask about: small three-number examples by hand.
- A linear classifier: one weight per pixel plus a bias.
- Loss, gradient, learning rate, and the order of the training steps: predict, loss, clear old gradients, gradients, update.
- Batches and epochs. Accuracy on held-back data.
- Overfitting: what it looks like in training and validation loss. Regularisation as a small cost on large weights.
- Why a network needs a nonlinearity such as ReLU between linear layers.
- Where: `course/labs/lab-03/` (companion worksheets, the Python warm-up notebook, and two short explainers)

### Week 4. Language models with an RNN (Lab 4, Homework 4)
- The RNN step: `h_t = Wx × x_t + Wh × h_(t-1) + b`. Ask about: tracing two or three steps by hand; what the hidden state carries; that the same weights are reused at every step.
- Tokenisation: character, word and subword. Ask about: one advantage and one cost of each, and the effect on vocabulary size and sequence length. A token ID is a label, not a quantity.
- A bigram model: count pairs, turn counts into probabilities.
- Generating text: the loop of predict, choose, append. Greedy choice and sampling. Temperature: low is predictable, high is varied.
- Calling a model through an API: the URL, the key, the model ID and the messages; why a key is kept out of code. Embeddings as vectors that can be compared.
- Where: `course/labs/lab-04/`, including the notebook `openrouter-api-lab.ipynb`

### Week 5. Attention and the Transformer (Lab 5, Homework 5)
- The problem attention solves: an RNN's memory fades; attention lets a token look back directly.
- Query, key and value. Scores from matching a query with each key; weights that add up to 1; the output as a weighted sum of the values. Ask about: a weighted sum by hand with two or three small vectors.
- Why a model that predicts the next token may not look at later tokens.
- A Transformer block: attention, then a small network, each added to what was there.
- Embeddings and position. Context length. What the letters in GPT stand for.
- Parameters, which training finds, and the settings a person chooses.
- Training loss against held-back loss, and what a gap between them means.
- Where: `course/labs/lab-05/`, including the practice problems above

## Files you should not open as text

A few pages in `course/labs/` are single files of several megabytes with model weights and fonts packed inside. Reading them fills your context with noise. Tell the student to open them in a browser instead.

- `course/labs/lab-05/gpt-dev-tour/index.html` (the guided tour of the notebook)
- `course/labs/lab-05/look-back/index.html` (Tuesday's attention explainer)
- `course/labs/lab-05/pseudocode/index.html` (Pseudocode, by example)
- `course/labs/lab-04/week4-rnn-explainer.html` and its `.zip`

## Course rules that apply while practising

- Each homework question carries a label saying what AI may do. If a question is labelled "No AI", do not help answer it. Offer to practise the same idea with a different example once the student has made their own attempt.
- Quizzes and exams are closed book. Do not help during one.
