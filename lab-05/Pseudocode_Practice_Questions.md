# CPSC 1710 Pseudocode Practice

**Fall 2026**

Nine short problems for practising pseudocode on paper. They use ideas from Weeks 1 to 5. The [midterm practice set](https://github.com/cpsc1710/labs/blob/main/lab-04/Midterm_Practice_Questions.md) has four more (Questions 1 to 4) and explains what we mean by pseudocode.

Try each problem on paper, without notes or AI. Most take three to six minutes. Then compare with the [answers](Pseudocode_Practice_Answers.md).

## Before you start

We check four things:

1. the steps are in the right order;
2. the values have names;
3. loops and conditions are shown where they are needed; and
4. another person could follow it.

Plain English is fine. You do not need Python.

Each problem lists what you **may assume**. You can use those helpers without explaining how they work. Everyday operations are always fine too: add things up, count, sort, take the length of a list.

The problems come in four formats: **write** the pseudocode yourself, **complete** the missing steps, **find the mistake**, or put steps in **order**.

---

## 1. How accurate is the classifier? (write)

You have trained a classifier that tells handwritten 3s from 7s. You are given:

- `images`: a list of held-back images
- `labels`: the correct answer for each image, in the same order
- `predict(image)`: returns the classifier's answer for one image, "3" or "7"

Write pseudocode that prints the **accuracy**: the fraction of the held-back images that the classifier gets right.

---

## 2. Is it a 3 or a 7? (complete)

Our first classifier in Week 3 compared a new image with the "average 3" and the "average 7". You may assume:

- `threes` and `sevens`: lists of training images
- `average(list of images)`: returns the average image
- `distance(a, b)`: returns one number. A smaller number means the two images are more alike.

Fill in the three missing steps.

```text
ideal_3 = ______________________________________     (Step 1)
ideal_7 = average(sevens)

to classify a new image:
    d3 = distance(image, ideal_3)
    d7 = ______________________________________      (Step 2)
    if ______________________________________:       (Step 3)
        answer "3"
    otherwise:
        answer "7"
```

Then answer in one sentence: which lines run once, and which lines run again for every new image?

---

## 3. Gradient descent on one weight (write)

A model has a single weight, `w`. You may assume:

- `loss(w)`: returns how wrong the model is when the weight is `w`
- `slope(w)`: returns the gradient of the loss at `w`. A positive slope means that increasing `w` makes the loss bigger.
- `lr`: the learning rate, a small positive number

Write pseudocode that starts from `w = 0` and improves `w` one step at a time. Stop when a step lowers the loss by less than 0.001, or after 1,000 steps, whichever comes first. Print the final `w`.

---

## 4. Where did overfitting start? (write)

You trained a model for 20 epochs. You are given `val_loss`, a list of 20 numbers: the loss on the validation set after each epoch. The validation loss falls at first and then rises again once the model starts to overfit.

Write pseudocode that finds the epoch with the lowest validation loss, and prints that epoch's number and its loss.

---

## 5. Turning text into numbers (find the mistake)

This pseudocode is meant to turn a text into a list of numbers, one per character, as `tiny_rnn.py` does. Two of its lines are wrong.

```text
1  vocabulary = the different characters in text, sorted
2  number_of = empty lookup table
3  for each character c in vocabulary, at position i:
4      number_of[i] = c
5  ids = empty list
6  for each character c in vocabulary:
7      add number_of[c] to ids
8  print ids
```

1. Which two lines are wrong, and what is wrong with each?
2. Write the corrected lines.
3. With your corrections, what does the pseudocode print when `text` is `banana`? Number the positions from 0.

---

## 6. Make practice questions from a text (write)

A language model learns by guessing the next character. You are given `text`, a long string of characters. Write pseudocode that builds a list called `examples`. Each example is a pair:

- **context**: 8 characters in a row from the text
- **target**: the one character that comes right after them

Make one example for every position in the text where this is possible.

Then answer: if the text has 100 characters, how many examples are there?

---

## 7. Run an RNN over a sentence (complete)

From Homework 4: `rnn_step(x, h)` takes one input `x` and the current hidden state `h`, and returns the new hidden state. You are given `inputs`, a list of numbers, and a starting hidden state `h0`.

Fill in the three missing steps so that `states` ends up holding the hidden state after each input.

```text
h = ______________________________________          (Step 1)
states = empty list

for each x in inputs, in order:
    h = ______________________________________      (Step 2)
    ______________________________________          (Step 3)

print states
```

Then answer in one or two sentences: what would go wrong if Step 2 always used `h0` in place of `h`?

---

## 8. Choose the next character, with temperature (order)

A model has given a score to each of 65 possible next characters. These are the steps for choosing the next character with temperature `T`. They are shuffled.

- **A.** Divide each result by the total of all the results, so that the numbers add up to 1.
- **B.** Draw one character at random, using those numbers as the odds.
- **C.** Divide every score by `T`.
- **D.** Raise *e* to the power of each divided score.
- **E.** Add the chosen character to the end of the text.

1. Write the letters in the right order.
2. What happens to the choices when `T` is very small, such as 0.1? What happens when `T` is large, such as 2?

---

## 9. Train for several epochs, in batches (write)

You are given:

- `data`: a list of 1,000 training examples
- `shuffle(list)`: puts a list into a random order
- `train_step(batch)`: runs one training step on a batch (prediction, loss, gradients, update) and returns that batch's loss

Write pseudocode that trains for 5 epochs with batches of 50 examples. Shuffle the data at the start of every epoch. At the end of each epoch, print the average loss over that epoch's batches.

Then answer: how many times is `train_step` called in total?

---

*Drafted by Claude (Anthropic), based on the direction of Xiuye Chen.*
