# StreamLine A/B Experiment Brief
## Mood-Filtered Spotlight Rail

### 1. Experiment objective

Determine whether adding a simple mood filter to Spotlight reduces discovery friction for long-time subscribers who feel overwhelmed by the size of the StreamLine catalog and helps them reach a viewing decision faster.

This experiment is designed to test **discovery effectiveness**, not long-term LTV or behavioral-segment migration. Those outcomes may be evaluated separately if the experiment demonstrates that mood filtering improves viewing decisions.

---

## 2. Target user

**Primary persona:** Wanderer

A long-time StreamLine subscriber who wants to discover something worth watching but struggles to make a decision because the catalog presents too many options.

### Moment of misery

The subscriber enters Spotlight intending to find something to watch but spends excessive time browsing titles without reaching a viewing decision.

---

## 3. Hypothesis

We believe that **adding a five-option mood filter to Spotlight** for long-time subscribers will reduce discovery friction by narrowing the set of titles users need to evaluate.

We expect this to increase the percentage of users who initiate playback within 10 minutes of entering Spotlight.

We will protect existing Casual Browsers and Power Users from a meaningful decline in their ability to reach a viewing decision.

---

## 4. Experimental treatment

### The single change being tested

**Spotlight gains one mood-selection mechanism with exactly five predefined moods.**

The five moods are:

- Funny
- Thrilling
- Comforting
- Thought-Provoking
- Easy Watching

Selecting a mood filters the existing Spotlight inventory to titles explicitly mapped to that mood.

### Held constant

The following must remain unchanged between Control and Variant except where strictly necessary to expose or remove the mood filter:

- Spotlight title-card design
- Title metadata shown
- Ranking logic within the eligible title set
- Play/View Title CTAs
- Navigation patterns
- Onboarding
- Notifications
- Login
- Profiles
- Saved titles
- Playback experience
- Streaming UI
- Device synchronization

Title-to-mood relationships must be predefined in the experiment dataset. The Variant must not dynamically infer mood mappings.

---

## 5. Control

Users receive the **existing Spotlight experience** with the existing unfiltered Spotlight rail and no mood-selection mechanism.

No other aspect of Spotlight is changed for the Control group.

---

## 6. Variant

Users receive the existing Spotlight experience plus the ability to select one of five predefined moods.

Selecting a mood filters the Spotlight inventory to titles mapped to that mood.

Users may Skip, Change mood, or Clear mood so the experiment does not force users who already have an effective discovery strategy into the mood-based flow.

These controls are escape mechanisms for the experimental treatment, not additional discovery features.

---

# 7. User stories

## Story 1 — Choose a mood

**As a** long-time streaming subscriber overwhelmed by the size of the catalog,  
**I want to** choose what I'm in the mood for,  
**so that** I can immediately evaluate a smaller set of relevant titles instead of wandering through the full catalog.

### Acceptance criteria

- User sees exactly five primary mood choices: Funny, Thrilling, Comforting, Thought-Provoking, and Easy Watching.
- User can select one mood with a single interaction.
- Only one mood can be active at a time.
- Selection visibly updates the experience.
- User reaches the filtered Spotlight rail immediately after selecting or confirming a mood.
- User can Skip mood selection in no more than one interaction.
- No account setup or additional questionnaire is introduced.

---

## Story 2 — Explore the filtered Spotlight rail

**As a** subscriber who has selected a mood,  
**I want** Spotlight to show titles matching that mood,  
**so that** I have fewer relevant options to evaluate before making a viewing decision.

### Acceptance criteria

- Every displayed title is explicitly mapped to the active mood in the experiment dataset.
- The active mood is clearly visible.
- The rail contains enough titles to browse without appearing unintentionally empty.
- User can select a title from the filtered rail.
- Existing title-card design and metadata remain unchanged from Control.
- Existing ranking logic is preserved within the eligible mood-matched inventory.
- Instrumentation records:
  - Spotlight entry
  - Mood selected
  - Filtered rail viewed
  - Title selected
  - Play initiated

---

## Story 3 — Change or exit the mood filter

**As a** user who does not find the current mood filter useful,  
**I want to** change, clear, or skip the mood,  
**so that** the experiment does not trap me in a discovery path that is worse than the existing Spotlight experience.

### Acceptance criteria

- Mood-selection experience includes a visible Skip action.
- Filtered experience includes a visible Change mood action.
- User can clear the active mood without restarting the experience.
- Clearing the mood restores the existing unfiltered Spotlight rail.
- No destructive confirmation modal is required.
- Change, Clear, and Skip events are instrumented.

---

# 8. Screens to build

## Screen 1 — Mood selection

### Purpose

Give users one simple mechanism for reducing the number of titles they need to evaluate.

### UI elements

- Existing StreamLine Spotlight branding
- Heading: **“What are you in the mood for?”**
- Supporting copy: **“Pick one and we'll narrow things down.”**
- Five mood choices:
  - Funny
  - Thrilling
  - Comforting
  - Thought-Provoking
  - Easy Watching
- Clear selected state
- Continuation action only if selection is not automatically applied
- Skip action

### Do not introduce

- Login
- Profile setup
- Search
- Personalization questionnaire
- Additional filters
- New recommendation controls

---

## Screen 2 — Mood-filtered Spotlight

### Purpose

Demonstrate whether narrowing the existing Spotlight inventory by mood helps users reach a viewing decision.

### UI elements

- Active mood indicator
- Change mood control
- Clear mood control
- Existing Spotlight rail populated only with mood-matched titles
- Existing title-card design
- Existing title metadata
- Existing title-selection behavior
- Existing Play/View Title CTA

### Fallback behavior

If a mood does not have enough eligible titles to populate the required experience, the system must use a deterministic fallback rather than displaying an empty rail.

The fallback must either:

1. offer another mood, or
2. return the user to the unfiltered Spotlight experience.

The fallback rule must be defined before experiment launch and applied consistently.

---

## Screen 3 — Existing title detail / Play decision

The experiment should use the existing downstream title-selection experience wherever possible rather than introducing a redesigned confirmation screen.

The experiment records success when the user initiates playback.

No real playback functionality needs to be added specifically for this experiment if existing instrumentation can record the Play event.

---

# 9. Functional requirements

The experiment MUST:

- Expose exactly five primary moods.
- Allow only one active mood at a time.
- Visibly identify the active mood.
- Filter titles using only predefined title-to-mood mappings.
- Ensure every experiment title is mapped to at least one mood.
- Never infer a title-to-mood relationship at runtime.
- Allow users to Skip mood selection in no more than one interaction.
- Allow users to Change or Clear an active mood without restarting.
- Restore the existing Spotlight rail when a mood is cleared.
- Provide a deterministic fallback for insufficient mood inventory.
- Instrument the complete discovery funnel.
- Preserve existing Spotlight UI and behavior wherever it is not necessary to implement the treatment.

---

# 10. Experiment population and randomization

### Eligibility

Long-time StreamLine subscribers who enter Spotlight during the experiment window.

The exact definition of **long-time subscriber** must be established before launch and must not change during the experiment.

### Randomization

- Unit: User
- Split: 50% Control / 50% Variant
- Assignment must remain stable for the duration of the experiment.

### Behavioral segmentation

Wanderer, Casual Browser, and Power User classifications must be calculated using a **pre-experiment observation window**.

Treatment behavior must not be used to retroactively classify users for experiment analysis.

---

# 11. Primary metric

## Qualified Play Conversion

**Definition:**

Percentage of eligible Spotlight entrants who initiate playback of a title within **10 minutes of entering Spotlight**.

**Formula:**

Qualified Play Conversion =  
Users initiating Play within 10 minutes of Spotlight entry  
÷  
Eligible users entering Spotlight

### Why this is the primary metric

The user's problem is difficulty reaching a viewing decision.

Qualified Play Conversion directly tests whether the Variant helps users move from discovery to watching rather than using total session duration as a proxy for successful discovery.

---

# 12. Primary success criterion

The Variant must demonstrate an improvement in Qualified Play Conversion relative to Control that:

1. meets the prespecified statistical significance threshold of **p < 0.05**; and
2. meets or exceeds the prespecified minimum detectable/business-relevant effect.

Before launch, the experiment brief MUST specify:

- Historical Qualified Play Conversion baseline: **TBD**
- Minimum effect considered worth shipping: **TBD**
- Statistical power: **minimum 80%**
- Required sample per arm: **TBD after power calculation**

The experiment must not launch until these values are established.

---

# 13. Guardrail

## Existing successful discoverers must not materially regress

Among users classified **before the experiment** as Casual Browsers or Power Users, Qualified Play Conversion must not decline beyond a prespecified non-inferiority margin versus Control.

### Guardrail decision threshold

Non-inferiority margin: **TBD before launch**

Example structure:

> Variant Qualified Play Conversion among pre-classified Casual Browsers and Power Users must not be more than X percentage points worse than Control.

The value of X must represent an explicit level of product/business tolerance and must be locked before experiment results are examined.

“Must not decrease” is not an acceptable decision rule.

---

# 14. Diagnostic metrics

The following metrics explain *why* the experiment succeeded or failed but do not independently determine whether the experiment ships:

- Median time from Spotlight entry to Play
- Percentage reaching Play within 5 minutes
- Titles viewed before Play
- Rails/interactions before Play
- Mood-selection rate
- Mood Skip rate
- Change mood rate
- Clear mood rate
- Spotlight abandonment rate
- Title-selection rate
- 30+ minute session rate

### Interpretation

A successful treatment should generally produce evidence consistent with reduced wandering—for example, higher Qualified Play Conversion accompanied by lower time-to-Play or fewer discovery interactions.

The existing **30+ minute session metric moves from primary metric to diagnostic/downstream metric**. It may indicate engagement but does not directly establish that discovery friction was reduced.

---

# 15. Sample size and runtime

The previous estimate of **4,144 users per arm must not be reused automatically**, because it was calculated against the old 11% / +2 percentage-point 30-minute-session outcome.

Required sample size must be recalculated using:

- Historical Qualified Play Conversion baseline
- Prespecified minimum worthwhile effect
- α = 0.05
- Power ≥80%
- 50/50 allocation

### Runtime rule

The experiment will run for:

**A minimum of 14 complete days AND until the preregistered sample requirement has been reached, whichever is later.**

The 14-day minimum ensures at least two complete weekly cycles.

The experiment must not stop early solely because nominal statistical significance is observed.

Before launch, the team must confirm that expected eligible Spotlight traffic can reach the required sample in a commercially reasonable period.

---

# 16. Decision rule

## SHIP

Ship Mood-Filtered Spotlight if:

- The primary Qualified Play Conversion criterion passes;
- The observed improvement meets or exceeds the prespecified minimum worthwhile effect;
- The Casual Browser / Power User guardrail passes; and
- No instrumentation or experiment-integrity issue invalidates the result.

## DO NOT SHIP

Do not ship if:

- The primary success criterion fails; or
- The primary result is statistically significant but smaller than the prespecified minimum worthwhile effect; or
- The Casual Browser / Power User guardrail fails.

## ITERATE AND RETEST

Iterate and rerun the experiment if a predefined validity issue prevents reliable interpretation, such as:

- Broken randomization
- Material instrumentation failure
- Incorrect title-to-mood mappings
- Variant contamination of Control
- Insufficient eligible inventory that prevents the intended treatment from being delivered

“Promising,” “directionally positive,” or post-hoc subgroup results are not alternate shipping criteria.

---

# 17. Experiment instrumentation

At minimum, record:

1. Experiment assignment
2. Pre-experiment behavioral segment
3. Spotlight entry
4. Mood-selection screen viewed
5. Mood selected
6. Selected mood
7. Skip selected
8. Filtered rail viewed
9. Change mood
10. Clear mood
11. Title selected
12. Play initiated
13. Time from Spotlight entry to Play
14. Experiment exit/abandonment

Events must contain enough information to reconstruct the user's discovery path without relying on post-hoc inference.

---

# 18. Explicitly out of scope

This experiment does **not** attempt to prove that mood filtering:

- Moves Wanderers permanently into Casual Browser or Power User segments
- Increases customer lifetime value
- Improves retention
- Changes long-term viewing frequency
- Improves recommendation quality across StreamLine
- Produces durable personalization effects

Those are downstream hypotheses requiring longer-term measurement.

If this experiment succeeds, the next validation step should test whether improved discovery behavior produces sustained engagement, segment migration, retention, or LTV improvements.

---

# 19. Pre-launch checklist

The experiment may launch only after all of the following are complete:

- [ ] Qualified Play Conversion historical baseline established
- [ ] Minimum worthwhile effect established
- [ ] Statistical power established at ≥80%
- [ ] Required sample per arm calculated
- [ ] Expected eligible daily traffic confirmed
- [ ] Non-inferiority guardrail margin established
- [ ] “Long-time subscriber” eligibility definition locked
- [ ] Pre-experiment behavioral-segment definition locked
- [ ] Title-to-mood mappings reviewed and frozen
- [ ] Minimum mood-inventory threshold defined
- [ ] Deterministic fallback behavior defined
- [ ] Control and Variant differ only by the intended mood-filter treatment
- [ ] Experiment events validated end-to-end
- [ ] Randomization and persistent assignment validated
- [ ] Primary metric and decision rule documented before exposure begins

---

## Final experiment statement

**We believe adding a five-option mood filter to Spotlight will help long-time subscribers who struggle with catalog overload reach a viewing decision more effectively. We will consider the experiment successful if it produces a statistically significant and commercially meaningful increase in Qualified Play Conversion without materially reducing Qualified Play Conversion among existing Casual Browsers and Power Users.**
