---
tags:
    - DOME
    - Data
    - Optimisation
    - Model
    - Evaluation
---

# 1. The DOME Recommendations

**Four pillars, 21 fields — a structured way to describe a supervised ML method so others can judge it.**

---

!!! overview "Overview"

    **Questions:**

    - What does DOME stand for, and where did it come from?
    - What exactly do the 21 fields ask for?
    - What is the difference between a DOME *requirement* and a DOME *recommendation*?
    - How do I use DOME as an author, a reviewer, or a reader?

    **Learning Objectives**

    By the end of this chapter, you will be able to:

    1. Name the four DOME pillars and what each one governs
    2. Locate the DOME fields a given paper does and does not report
    3. Explain why a specific field matters — for example, why redundancy between data splits invalidates a performance claim
    4. Use DOME as a checklist when reviewing someone else's ML paper

    **Time:** 15 minutes

    **Prerequisite:** Familiarity with supervised ML terminology (training/test splits, overfitting, cross-validation)

---

## What DOME is

**DOME** — **D**ata, **O**ptimisation, **M**odel, **E**valuation — is a set of
community recommendations for reporting supervised machine learning applied to
biological problems. It was developed by the
[ELIXIR Machine Learning Focus Group](https://elixir-europe.org/focus-groups/machine-learning)
(2019–2025) and published in *Nature Methods* in 2021 [@walsh2021dome]. That
focus group concluded in September 2025; its work continues in the ELIXIR
[AI Ecosystem Focus Group](https://elixir-europe.org/focus-groups/ai-ecosystem).

DOME is deliberately **not** a methodological prescription. It does not tell you
which algorithm to use or what counts as good performance. It asks you to
*state* what you did, in a structured form, so that a reader can decide for
themselves whether the result is credible.

!!! tip "The one-sentence version"
    DOME turns "the methods section was unclear" into a specific, checkable list
    of things that were or were not reported.

### Requirements vs recommendations

Each of the 21 fields carries one of two labels:

- <span class="badge-req">Requirement</span> — a critical step, considered
  **essential** for transparent and reproducible ML. If it is missing, a reader
  genuinely cannot assess the work.
- <span class="badge-rec">Recommendation</span> — a highly advised best practice
  that further improves the quality and rigour of the reporting.

Of the 21 fields, **11 are requirements** and **10 are recommendations**.

---

## The four pillars

=== "Data (4 fields)"

    *Guiding principles for ensuring the integrity, provenance and utility of the data used for training and evaluation.*

    #### 1.1 Provenance <span class="badge-req">Requirement</span>

    - What is the source of the data (database, publication, direct experiment)?
    - If data are in classes, how many data points are available in each class — for example, total for the positive (N~pos~) and negative (N~neg~) cases?
    - If regression, how many real value points are there?
    - Has the dataset been previously used by other papers and/or is it recognised by the community?

    !!! info "Why it matters"
        Knowing the origin and composition of data is fundamental to assessing its quality, representativeness and potential biases.

    #### 1.2 Data splits <span class="badge-req">Requirement</span>

    - How many data points are in the training and test sets?
    - Was a separate validation set used, and if yes, how large was it?
    - Are the distributions of data types in the training and test sets different?
    - Are the distributions of data types in both training and test sets plotted?

    !!! info "Why it matters"
        Clear documentation of data splits ensures that performance metrics are calculated on appropriate, distinct subsets of data.

    #### 1.3 Redundancy between data splits <span class="badge-req">Requirement</span>

    - How were the sets split?
    - Are the training and test sets independent?
    - How was this enforced (for example, redundancy reduction to less than X% pairwise identity)?
    - How does the distribution compare to previously published ML datasets?

    !!! info "Why it matters"
        Data leakage between training and test sets leads to over-optimistic performance estimates that fail to generalise to new data.

    #### 1.4 Availability of data <span class="badge-req">Requirement</span>

    - Are the data, including the data splits used, released in a public forum?
    - If yes, where (for example, supporting material, URL) and how (licence)?

    !!! info "Why it matters"
        Public access to data allows other researchers to verify results, reproduce experiments and benchmark new methods fairly.

=== "Optimisation (8 fields)"

    *Guiding principles for the transparent and robust training of the model.*

    #### 2.1 Algorithm <span class="badge-req">Requirement</span>

    - What is the ML algorithm class used?
    - Is the ML algorithm new? If yes, why was it chosen over better known alternatives?

    !!! info "Why it matters"
        Justifying the algorithm choice helps the community understand the rationale and suitability of the method for the specific problem.

    #### 2.2 Meta-predictions <span class="badge-req">Requirement</span>

    - Does the model use data from other ML algorithms as input? If yes, which ones?
    - Is it clear that training data of initial predictors and meta-predictor are independent of test data for the meta-predictor?

    !!! info "Why it matters"
        Improper handling of meta-predictions can introduce hidden data leakage, invalidating performance claims.

    #### 2.3 Data encoding <span class="badge-rec">Recommendation</span>

    - How were the data encoded and preprocessed for the ML algorithm?

    !!! info "Why it matters"
        Preprocessing steps can significantly impact model performance and must be documented for reproducibility.

    #### 2.4 Parameters <span class="badge-rec">Recommendation</span>

    - How many parameters (*p*) are used in the model?
    - How was *p* selected?

    !!! info "Why it matters"
        The number of parameters relates to model complexity and the risk of overfitting, especially with limited data.

    #### 2.5 Features <span class="badge-rec">Recommendation</span>

    - How many features (*f*) are used as input?
    - Was feature selection performed? If yes, was it performed using the training set only?

    !!! info "Why it matters"
        Feature selection must be isolated from the test set to prevent leakage and ensure unbiased evaluation.

    #### 2.6 Fitting <span class="badge-rec">Recommendation</span>

    - Is *p* much larger than the number of training points and/or is *f* large (for example, in classification is *p* ≫ (N~pos~+N~neg~) and/or *f* > 100)? If yes, how was overfitting ruled out?
    - Conversely, if the number of training points is much larger than *p* and/or *f* is small, is the model expressive enough?

    !!! info "Why it matters"
        Balancing model complexity with data availability is crucial to avoid models that memorise noise or fail to capture the signal.

    #### 2.7 Regularisation <span class="badge-req">Requirement</span>

    - Were any overfitting prevention techniques used (for example, early stopping using a validation set)? If yes, which ones?

    !!! info "Why it matters"
        Regularisation techniques are essential for creating robust models that generalise well to unseen data.

    #### 2.8 Availability of configuration <span class="badge-rec">Recommendation</span>

    - Are the hyperparameter configurations, optimisation schedule, model files and optimisation parameters reported?
    - If yes, where (for example, URL) and how (licence)?

    !!! info "Why it matters"
        Full transparency of the training configuration allows others to replicate the training process exactly.

=== "Model (4 fields)"

    *Guiding principles for the description and dissemination of the final model.*

    #### 3.1 Interpretability <span class="badge-rec">Recommendation</span>

    - Is the model black box or interpretable?
    - If the model is interpretable, can you give clear examples of this?

    !!! info "Why it matters"
        Interpretability builds trust in the model's predictions and can provide scientific insights into the underlying biology.

    #### 3.2 Output <span class="badge-req">Requirement</span>

    - Is the model classification or regression?

    !!! info "Why it matters"
        Clearly defining the output type sets the context for appropriate evaluation metrics and usage.

    #### 3.3 Execution time <span class="badge-rec">Recommendation</span>

    - How much time does a single representative prediction require on a standard machine (for example, seconds on a desktop PC or high-performance computing cluster)?

    !!! info "Why it matters"
        Practical utility depends on computational efficiency; users need to know the resource requirements.

    #### 3.4 Availability of software <span class="badge-req">Requirement</span>

    - Is the source code released?
    - Is a method to run the algorithm — such as executable, web server, virtual machine or container instance — released?
    - If yes, where (for example, URL) and how (licence)?

    !!! info "Why it matters"
        Accessible software is the primary way for the community to use and benefit from the developed model.

=== "Evaluation (5 fields)"

    *Guiding principles for the fair and comprehensive assessment of model performance.*

    #### 4.1 Evaluation method <span class="badge-req">Requirement</span>

    - How was the method evaluated (for example, cross-validation, independent dataset, novel experiments)?

    !!! info "Why it matters"
        The evaluation strategy determines the reliability of the performance estimates and their applicability to real-world scenarios.

    #### 4.2 Performance measures <span class="badge-req">Requirement</span>

    - Which performance metrics are reported?
    - Is this set representative (for example, compared to the literature)?

    !!! info "Why it matters"
        Selecting appropriate metrics prevents misleading conclusions, especially with imbalanced datasets.

    #### 4.3 Comparison <span class="badge-req">Requirement</span>

    - Was a comparison to publicly available methods performed on benchmark datasets?
    - Was a comparison to simpler baselines performed?

    !!! info "Why it matters"
        Comparisons contextualise performance, showing whether the new method offers a genuine improvement over existing solutions.

    #### 4.4 Confidence <span class="badge-rec">Recommendation</span>

    - Do the performance metrics have confidence intervals?
    - Are the results statistically significant to claim that the method is superior to others and baselines?

    !!! info "Why it matters"
        Statistical significance tests and confidence intervals distinguish true improvements from random variations.

    #### 4.5 Availability of evaluation <span class="badge-rec">Recommendation</span>

    - Are the raw evaluation files (for example, assignments for comparison and baselines, statistical code, confusion matrices) available?
    - If yes, where (for example, URL) and how (licence)?

    !!! info "Why it matters"
        Sharing raw evaluation data enables deep verification and facilitates future meta-analyses.

---

## Using DOME in practice

=== "As an author"

    Fill in the 21 fields **while you write the methods section**, not after. Fields
    you cannot answer are usually a signal that something needs to be recorded,
    released or re-run — not just re-worded. Deposit the finished report in the
    [DOME Registry](chapter_02_registry.md) and cite it in your submission.

=== "As a reviewer or editor"

    Use the 11 requirements as your first pass. A paper that cannot state its data
    splits (1.2), rule out redundancy between them (1.3), or name a baseline
    comparison (4.3) has an assessability problem regardless of how good the
    reported numbers are. A DOME Registry link supplied at submission makes this a
    two-minute check rather than a hunt through supplementary files.

=== "As a reader"

    Treat the fields as the questions you were going to ask anyway. Where the paper
    is silent, that silence is now specific and citable.

!!! warning "A gap is not a verdict"
    A missing field means the paper did not *report* something — not that the work
    is wrong. DOME measures transparency, not quality. Keep that distinction
    explicit when you use a DOME report in review; it is the difference between
    useful feedback and an unfair one.

---

## The DOME score

Because the fields are structured, DOME compliance can be counted. The
[DOME Registry](chapter_02_registry.md) computes a **score from 0 to 21** —
one point per completed field — giving a coarse but comparable measure of how
transparently a method has been reported. Chapter 2 covers what that score is
good for, and what it is not.

---

## Sources and further reading

- **The DOME site**: <https://dome-ml.org/>
- **The paper**: Walsh I, Fishman D, Garcia-Gasulla D, et al. *DOME: recommendations for supervised machine learning validation in biology.* Nature Methods 18, 1122–1127 (2021). [doi:10.1038/s41592-021-01205-4](https://doi.org/10.1038/s41592-021-01205-4) [@walsh2021dome]

---

**Next:** [Chapter 2 — The DOME Registry](chapter_02_registry.md)
