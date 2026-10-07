# CPSC 1710 Pseudocode Practice: Answers

**Fall 2026**

Try the [problems](Pseudocode_Practice_Questions.md) before reading these. Each answer below is one version that would earn full marks. Yours can be worded differently and still be correct. Check it against the notes under "What we look for".

Positions can be counted from 0 or from 1. Either is fine if you are consistent.

---

## 1. How accurate is the classifier?

```text
correct = 0
for each position i in images:
    if predict(images[i]) is the same as labels[i]:
        add 1 to correct

accuracy = correct / number of images
print accuracy
```

**What we look for:** a counter that starts at 0; a loop over every image; a comparison between the prediction and the label at the same position; the division done once, after the loop.

**A common slip:** dividing inside the loop, or comparing each prediction with the wrong label.

---

## 2. Is it a 3 or a 7?

- Step 1: `ideal_3 = average(threes)`
- Step 2: `d7 = distance(image, ideal_7)`
- Step 3: `if d3 is smaller than d7`

The two `ideal` lines run once, before any new image arrives. The lines under "to classify a new image" run again for each image.

**What we look for:** the distance is measured to both ideal images, and the smaller distance wins.

**A common slip:** writing Step 3 the wrong way round. A smaller distance means more alike.

---

## 3. Gradient descent on one weight

```text
w = 0
old_loss = loss(w)

repeat up to 1000 times:
    w = w - lr × slope(w)
    new_loss = loss(w)
    if old_loss - new_loss is less than 0.001:
        stop
    old_loss = new_loss

print w
```

**What we look for:** the update subtracts `lr × slope(w)`; the loss is measured again after each update; the new loss is compared with the one before it; `old_loss` is replaced at the end of each round; the loop cannot run more than 1,000 times.

**A common slip:** adding the slope where it should be subtracted, which moves `w` uphill. Another is forgetting to update `old_loss`, so every step is compared with the starting loss.

---

## 4. Where did overfitting start?

```text
best_epoch = 1
best_loss = val_loss[1]

for each epoch e from 2 to 20:
    if val_loss[e] is less than best_loss:
        best_loss = val_loss[e]
        best_epoch = e

print best_epoch and best_loss
```

**What we look for:** a "best so far" that starts from the first epoch; a loop over the rest; both the loss and the epoch number are replaced when a lower loss turns up; printing happens after the loop.

**A common slip:** starting `best_loss` at 0, so no loss is ever lower. Another is keeping the lowest loss but not the epoch it came from.

---

## 5. Turning text into numbers

1. **Line 4** is backwards. It stores each character under its number, which is the table for turning numbers back into characters. Line 7 needs to look up a number by its character. **Line 6** loops over the vocabulary, so it would go through each different character once. It should go through the text.
2. Corrected lines:

    ```text
    4      number_of[c] = i
    6  for each character c in text:
    ```

3. For `banana`, the vocabulary is `a`, `b`, `n`, so `a` is 0, `b` is 1 and `n` is 2. The pseudocode prints `[1, 0, 2, 0, 2, 0]`.

**What we look for:** you can say what each line is for, and you can trace the corrected version on a short example.

---

## 6. Make practice questions from a text

```text
examples = empty list

for each start position i from 0 to (length of text - 9):
    context = the 8 characters of text that begin at position i
    target = the character at position i + 8
    add (context, target) to examples
```

A text of 100 characters gives **92** examples. The last context covers positions 91 to 98, and its target is the last character, at position 99.

**What we look for:** one example per start position; the target is the character right after the context; the loop stops early enough that a target still exists.

**A common slip:** running the loop to the end of the text, where there are fewer than 8 characters left or no character to use as the target.

---

## 7. Run an RNN over a sentence

- Step 1: `h = h0`
- Step 2: `h = rnn_step(x, h)`
- Step 3: `add h to states`

If Step 2 always used `h0`, each hidden state would depend only on the current input and the starting state. Nothing would carry over from earlier inputs, so the network would have no memory of the sequence.

**What we look for:** the hidden state produced by one step is the one passed into the next step.

---

## 8. Choose the next character, with temperature

1. **C, D, A, B, E.** Divide the scores by `T`, raise *e* to each, divide by the total so they add up to 1, draw one character, and add it to the text.
2. When `T` is very small, dividing by it makes the gaps between scores much larger, so the character with the highest score is chosen almost every time and the text becomes repetitive. When `T` is large, the gaps shrink, the odds become more even, and the choices are more random.

**What we look for:** the division by `T` comes before the scores are turned into odds, and the draw comes after.

---

## 9. Train for several epochs, in batches

```text
for each epoch from 1 to 5:
    shuffle(data)
    total = 0

    for each start position s = 0, 50, 100, ... up to 950:
        batch = the 50 examples of data that begin at position s
        total = total + train_step(batch)

    print epoch and total / 20
```

`train_step` is called **100** times: 20 batches in each of 5 epochs.

**What we look for:** two loops, one inside the other; the shuffle is inside the epoch loop and outside the batch loop; `total` is set back to 0 at the start of each epoch; the average divides by the number of batches.

**A common slip:** setting `total = 0` once, before both loops, so later epochs include the losses of earlier ones.

---

*Drafted by Claude (Anthropic), based on the direction of Xiuye Chen.*
