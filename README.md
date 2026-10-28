# TakeMeter

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, the
> notebook, the baseline, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> head -5 data/practice_labels.csv     # the shape your labels.csv needs
> ```
>
> Then open `takemeter.ipynb` **in this folder** — in VS Code, or with
> `jupyter notebook` if you prefer. Pick the kernel: the `.venv` inside this
> project. Run section 1, which reports the hardware you'll be training on.
> Everything else waits until you have data.
>
> Nothing to upload, nothing to connect, no accounts and no keys. The notebook
> runs on your machine and writes next to your code.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     Unit 5 asks for the first five sections. Unit 6 adds the five below them.

     Everything is pasted as TEXT. No screenshots, no images.

     ⚠️ The confusion matrix especially. The notebook prints one as a markdown
     table, ready to copy. A screenshot of a matrix earns nothing. Paste the
     table.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 5 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Your community, and what your classifier sorts posts into. Three or four
     sentences. -->

This project sorts posts from r/financialindependence, a community for people
pursuing financial independence and early retirement (FIRE). Every post falls
into one of three buckets: a **milestone** (someone sharing progress on their
own FIRE journey, often following up on an earlier post), a **plan** (someone
proposing or refining a forward-looking financial strategy), or a **query**
(someone asking a direct question and looking for an answer). The classifier
reads a post and predicts which of the three it is, so posts could eventually
be sorted or routed by what kind of post they are.

---

## Label Taxonomy

<!-- Each label: a one-sentence definition and two real examples from your
     reading. Then your decision rule for the hardest boundary.

     The decision rule is worth a point on its own and it's the thing most
     people leave out. Every taxonomy has a hardest boundary. Name yours. -->

### `milestone`

**Definition:** A post reporting on the person's own ongoing progress since an earlier post they made, usually referencing or linking back to it.

**Example 1:**
> 3 years into FI/RE update
By now it's been a little over three years since I've stopped working. The previous posts I shared about my experience were after the first six months and around the one year mark, and it's been interesting to reread them to track how my experience with early retirement has evolved. A lot has happened since — both in the world and in my life — so I thought I'd share an update for anyone interested.

**Example 2:**
> Year 2 Update After $1M: Learning to Live
Hello! I’ve been back and forth mentally about making this post; I think it’s a good reflection of me moving past my “financial trauma” by not being so obsessed with the financial number as I have been in the past. I like these posts as sort of voicing out my personal journey for others to resonate or learn from.

### `plan`

**Definition:** A post proposing or refining a forward-looking financial strategy, often asking for feedback on choices not yet made.

**Example 1:**
> My 5-Year FI Plan: What Am I Missing?
Hi folks! I'm aiming to reach financial independence by age 32 (in 5 years) and am refining my contribution strategy and early withdrawal plan. Would love feedback—especially if my logic checks out and any other strategies or accounts that I am not taking advantage of.

**Example 2:**
> Making your FIRE Plan “near” bulletproof
GM All
Hoping to connect and better understand your strategies in ensuring your portfolio is as close to resilient & bulletproof as possible. It seems many are quick to list their balances, but not so much how they diversified to weather SORR. Let me know where you’re at!

### `query`

**Definition:** A post seeking direct technical or procedural answers.

**Example 1:**
> Salary Increased - No Longer Roth Eligible… but Scared of the Backdoor Roth Process 😅 Advice?
Hi everyone!
I had a salary increase this year, which is great… until I realized I no longer qualify to contribute directly to a Roth IRA. My initial reaction was, “Cool, I’ll just do the backdoor!”
But then I learned about the pro-rata rule (fun times), and now things feel a little more complicated.
I have an old Traditional IRA (~$340K) from a 401k rollover years ago. From what I’ve been reading, the cleanest way to do a backdoor Roth is to roll that IRA into my current 401k plan. That would “zero out” the IRA and let me do a clean conversion.
But honestly… Rolling over $340K feels intimidating. I know it’s all just ETFs and nothing is actually being “sold” in a taxable sense inside these accounts, but emotionally it still feels like a huge move.
Part of me is thinking: Should I even bother with the backdoor Roth at all? Or should I just skip the drama and continue beefing up my taxable brokerage instead?
Has anyone here:
Rolled a large IRA into a 401k?
Am I overthinking this process?
Chosen to not do backdoor Roth and just invest in taxable instead?
I’m trying to decide if the tax-free growth is worth the extra steps (and the anxiety that comes with moving such a big chunk of money).
Would love to hear your experiences or advice!

**Example 2:**
> Maxing Tax-Advantaged Accounts Properly (Missing Anything?)
Hey all, I'd like to ensure I am maxing our all of my tax advantaged accounts to the best of my knowledge. Here are the details
Company 1: 120k, 6% match, only allows trad/roth 401k contributions
Company 2: 180k, 6% company contribution of salary end of year, allows after-tax (non-roth) contributions up to 15% of pay + in-plan conversions
What Id like to do in 2026 (I understand the limits next year may slightly change):
Contribute the max 24.5k to Company 1 401k (Deferral Limit)
Contribute the max 15% to Company 2 after-tax and immediately convert to Roth 401k (Mega Back Door Roth)
Contribute the max ~7k-7,500 to Traditional IRA and convert via Back Door Roth
Max HSA contribution from only 1 company
My understanding from reading online is that the 24.5k elective deferral is across all accounts. However, the ~70k total contribution is for each company. Therefore, as long as my 15% contribution + 6% company contribution for company 2 is below that, which it will be, then I should be good to go.
Is there anything I am misunderstanding?
Is there anything I am not optimizing in terms of tax-adv accounts? Anything else I should be doing?


### The hardest boundary

**Which two labels:** update vs plan

**The decision rule I used every time:**
<!-- e.g. "If the post names a specific checkable fact, it's `analysis`, even
     if the tone is heated." -->

If the post references the author's own earlier post (linked or just described), it's 'update', even if it also lays out a forward plan.

---

## The Dataset

<!-- Where you collected from, how you labelled, your counts, and three hard
     cases. -->

**Where the posts came from:**

**How I labelled them:** <!-- Cold first? Pre-labelled with AI and corrected?
Say so plainly — the disclosure is required, not penalised. -->

**Counts per label:**

| Label | Count | Share |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
| **Total** |  | 100% |

**Three hard cases**

<!-- Any post that made you pause: what it was, which two labels it could have
     been, and what you chose. These are worth more than the easy 190. -->

**1.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**2.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

**3.**
> *The post:*
>
> *Could have been:*
>
> *I chose, because:*

---

## The Training Run

<!-- Your starting model, your settings, and anything you changed and why. -->

**Base model:**

**Settings:** <!-- epochs, learning rate, batch size, seed -->

**Anything I changed from the defaults, and why:**

**Split sizes:** <!-- train / val / test, and per-label counts in the test
split. If a label had fewer than about 8 in test, say so — it explains a lot
of next unit's variance. -->



---

## How I Used AI

<!-- Two specific moments — what you asked, what came back, what you changed.

     ⚠️ Plus disclosure of any pre-labelling. If you had a model pre-label a
     batch and then read and corrected every one, say that. It's an allowed
     workflow and disclosing it costs you nothing. Not disclosing it is the
     problem. -->

**Moment 1**

- *What I asked for:* I had a `tip` label with 23 posts that I was unsure about, so I asked it to go through each of those 23 posts and decide, against my actual `milestone`/`plan`/`query` definitions, whether it fit one of the three existing labels or should just be deleted.
- *What came back:* It read all 23 posts and returned a per-post call with a reason tied to my definitions — 4 fit an existing label (e.g. a post explicitly following up on the author's own earlier post matched `milestone`; a post directly asking the community a question matched `query`), and the other 19 were general advice, news, or reflection posts that didn't fit any of my three definitions.
- *What I changed:* I checked its reasoning against my own definitions rather than taking the calls at face value, and agreed with all 4 relabels and all 19 deletions — none needed overriding, but I would not have accepted a relabel that didn't point to a specific line in my definition.

**Moment 2**

- *What I asked for:*
- *What came back:*
- *What I changed:*

**Pre-labelling disclosure:**

<!-- ═══════════════════════ UNIT 6 — THE TEST ═══════════════════════

     Don't fill these in during unit 5.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Baseline vs. Trained

<!-- Both models on the same posts. `python baseline.py --trained results.json`
     prints this table for you. -->

| Measure | Baseline | Trained | Difference |
|---|---|---|---|
| Overall accuracy |  |  |  |
| Macro F1 |  |  |  |
| F1 — `label_one` |  |  |  |
| F1 — `label_two` |  |  |  |

**What I predicted before I looked:**
<!-- Milestone 1 asks you to write this BEFORE seeing the trained numbers. A
     prediction made afterwards isn't one. -->

**What the gap actually means:**
<!-- If the baseline matched your trained model, your fine-tuning added
     nothing — and that is a real finding, not a failure. Say it plainly. -->



---

## Run Log — Before

<!-- Five criteria across three seeds. The notebook's section 6 prints the
     spread table; the Target and Verdict columns are yours. -->

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

### Confusion matrix

<!-- ⚠️ TYPED AS A MARKDOWN TABLE. The notebook prints one ready to paste.
     An image of a matrix earns nothing. -->

| true \ predicted |  |  |  |
|---|---|---|---|
| **** |  |  |  |
| **** |  |  |  |
| **** |  |  |  |

**My biggest off-diagonal number, and what it means:**
<!-- Not "the model made mistakes" — WHICH boundary it didn't learn, and which
     direction. "7 real analysis posts were called hot_take and only 3 went the
     other way" is a direction, not just an error rate. -->



---

## Verdicts and Diagnoses

<!-- MET or MISSED against LAST UNIT's target. The target has to hold across
     all three seeds, not turn up sometimes. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**

<!-- For each miss: the cause, and how you know. The four common causes are:
     too few examples for a label, a boundary you applied inconsistently, a
     genuinely hard label pair, and a task the model can't reach from this
     much data.

     ⚠️ Use your agreement report as evidence. It is the only instrument you
     have that can tell a LABELLING problem from a MODEL problem, and this
     section is graded on whether you used it that way. -->



---

## Agreement Report

<!-- Your rate against the staff set, and every disagreement adjudicated.

     Remember you labelled these 30 under the STAFF taxonomy in
     data/staff_taxonomy.md, not your own — so every argument below is made
     from those definitions and those decision rules. -->

**Agreement rate:** ___ / 30 = ___%

<!-- Nobody grades this number. A 60% who argues every disagreement from the
     stated rules beats a 95% who wrote "staff was right" nine times. Several
     of the 30 were chosen because they're genuinely ambiguous — you should be
     winning some of these. -->

**Disagreements**

<!-- Three lines each: the post, both labels, and who you think is right and
     why — grounded in the staff definitions you were both applying.

     Then sort each into one of three piles:
       (a) the rule covered it and I applied it loosely → a consistency problem
       (b) the rule genuinely doesn't say               → a gap in the definitions
       (c) the rule is ambiguous here and my reading is defensible → argue it.
           This is a legitimate win.

     Pile (a) is the one that matters most for your diagnosis: if you applied a
     written rule two different ways on 30 posts, that is direct evidence about
     what you did across your own 200. -->

**1.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**2.**
> *The post:*
>
> *Staff said / I said:*
>
> *My call, and why:*
>
> *Which pile:*

**What the pattern in my disagreements tells me:**



---

## The Improvement

**What I changed:**

**Which diagnosis pointed at it:**

### Run Log — After

| Criterion | Target | Seed 42 | Seed 7 | Seed 2024 | Verdict |
|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |
| 2.  |  |  |  |  |  |
| 3.  |  |  |  |  |  |
| 4.  |  |  |  |  |  |
| 5.  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it didn't, say so. Relabelling that didn't help is a genuinely
     interesting result and earns full credit. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped. -->



**The gap between what I meant my labels to capture and what the model
learned:**
<!-- Two sentences. Your confusion matrix is the evidence. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 5

       [ ] criteria.md has five numbered criteria, each naming a NUMBER
       [ ] Each has a reason underneath tied to your data or taxonomy
       [ ] labels.csv: at least 150 rows, text/label/note, ONE file not split
       [ ] No label above 70%
       [ ] All five unit 5 sections have real content
       [ ] Label Taxonomy includes the decision rule for your hardest boundary
       [ ] The Dataset includes three hard cases
       [ ] results.json and test_split.csv committed (the notebook does this)
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN

     SUBMISSION CHECKLIST — unit 6

       [ ] Baseline vs. Trained table, with your prediction written beforehand
       [ ] Run Log — Before, five criteria across three seeds
       [ ] Confusion matrix TYPED AS A MARKDOWN TABLE
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, using the agreement report as evidence
       [ ] Agreement Report with every disagreement adjudicated
       [ ] One improvement, with Run Log — After
       [ ] What's Still Broken
       [ ] results_three_seeds_before.json, results_three_seeds_after.json,
           baseline_results.json and
           agreement_results.json committed
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**
