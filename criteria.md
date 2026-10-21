# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## 1. Overall accuracy reaches at least 0.70 across all categories

Given a held-out test dataset of labeled r/financialindependence posts, the model correctly predicts the primary category for at least 70% of the inputs.

**Why this target:** A naive random guess across my 3 categories (`milestone`, `plan`, `query`) yields ~33% accuracy. Setting a 0.70 baseline ensures the classifier provides enough real-world utility to reliably organize community feeds, while leaving room for the inherent ambiguity in open-ended text posts (such as a post that shares a milestone and then asks what to do next, blurring `milestone` and `query`).

---

## 2. Per-label performance reaches an F1 score of at least 0.55 for every category

Given evaluated performance on the held-out test set, no individual post category scores lower than a 0.55 F1 score.

**Why this target:** High-volume topics (like generic portfolio questions) easily dominate the training set over minority topics (like specific FIRE milestone celebrations). A hard 0.55 F1 floor prevents the model from achieving a high overall accuracy by completely ignoring lower-frequency labels.

---

## 3. Agreement with the staff-labeled set reaches at least 80%

Given the 30 posts in `data/staff_posts.csv`, labeled under the staff's own taxonomy in `data/staff_taxonomy.md` and scored with `agreement.py`, my labels match the staff's labels on at least 80% (24/30) of the posts.

**Why this target:** Financial forum posts frequently blur boundaries (for instance, asking for advice while detailing a personal budget story), and the staff set was deliberately built to include some genuinely ambiguous calls. With only 30 posts, each disagreement moves the rate by more than 3 points, so 80% leaves room for a handful of defensible disagreements without treating the staff's taxonomy as something I should match perfectly.

---

## 4. Class imbalance stays within a 10% floor and a 60% ceiling in the training set

Given the curated training dataset, no single category represents more than 60% or less than 10% of total training samples.

**Why this target:** Extreme class skew causes model loss functions to overfit heavily on dominant categories. Setting these explicit boundaries ensures gradient updates remain stable during training, requiring data re-balancing or broader data collection if natural post volume strays outside this window.

---

## 5. The most-confident third of predictions is at least 20 points more accurate than the least-confident third

Given the notebook's confidence report, which ranks test-set predictions by the model's softmax confidence and splits them into thirds, accuracy on the most-confident third (`accuracy_most_confident_third`) is at least 0.85, and at least 20 points higher than accuracy on the least-confident third (`accuracy_least_confident_third`).

**Why this target:** High-confidence predictions are typically used for automated user-facing features like auto-tagging or instant routing. If the model's confidence doesn't actually track correctness — if the most- and least-confident thirds score about the same — then confidence is noise and can't be used to gate automated behavior, which is exactly what this gap tests for.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
