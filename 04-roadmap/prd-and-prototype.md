# Mood-Based Entry Point, Simplified PRD (StreamLine)

**Author:** Me · **Status:** Draft · **Target:** High-Fidelity Prototype · **Persona:** The Wanderer

## 1. The Big Picture
- **Vision:** Help overwhelmed long-time StreamLine subscribers move from “I don't know what to watch” to a relevant, manageable Spotlight rail by choosing how they want to feel rather than searching the full catalog.
- **Press release:** StreamLine Spotlight makes “What should I watch?” easier to answer. Instead of dropping long-time subscribers into an enormous catalog and expecting them to navigate it, Spotlight asks one simple question on entry: “What are you in the mood for?” Users choose from five clear moods—Funny, Thrilling, Comforting, Thought-Provoking, or Easy Watching—and immediately see a focused rail of matching titles.

The experience directly targets Spotlight's Moment of Misery: users leaving the app because content curation is poor. Mood selection reduces the amount of content users must evaluate while preserving an easy Skip option for people who already know how they want to browse. The goal is not to maximize mood interactions; it is to decrease the percentage of Wanderers without materially worsening the experience for Casual Browsers or Power Users.
- **Success metric:** Target: Demonstrate a directional decrease in the percentage of Wanderers among prototype users exposed to the mood experience versus the unfiltered browsing path. Prototype behavioral proxy: ≥70% of participants should reach a relevant title detail/play decision without abandoning or repeatedly browsing the rail.
- **Guardrail:** Mood selection must remain optional. Target: ≥90% of participants who do not want mood filtering can bypass or clear it without assistance, with no critical usability failures. Do not treat increased mood-selection rate as success if it creates additional friction for users who prefer normal browsing

## 2. The Details
### User stories
- Story 1 — Choose a mood
- As a long-time streaming subscriber overwhelmed by the size of the catalog,
- I want to choose what I'm in the mood for,
- so that I can immediately see a smaller set of relevant titles instead of wandering through the full catalog.
- Acceptance criteria
- User sees exactly five primary mood choices: Funny, Thrilling, Comforting, Thought-Provoking, Easy Watching.
- User can select one mood with a single interaction.
- Selection visibly updates the experience.
- User reaches the filtered Spotlight rail immediately after confirming/selecting a mood.
- No account setup or additional questionnaire is required.
- Story 2 — Explore the filtered Spotlight rail
- As a subscriber who has selected a mood,
- I want the Spotlight rail to contain titles matching that mood,
- so that I have fewer, more relevant options to evaluate.
- Acceptance criteria
- Every displayed title is mapped to the active mood in the prototype dataset.
- The active mood is clearly visible above the rail.
- The rail contains enough titles to browse without appearing empty.
- User can select a title from the filtered rail.
- The prototype records the path from mood → rail → title selection.
- Story 3 — Change my mind
- As a Casual Browser or Power User who doesn't want the current mood filter,
- I want to change, clear, or skip my mood,
- so that Spotlight doesn't trap me in a discovery flow that isn't useful.
- Acceptance criteria
- Entry screen includes a visible Skip action.
- Filtered experience includes a visible Change mood action.
- User can clear the mood without restarting the prototype.
- Clearing restores the default Spotlight rail.
- No destructive confirmation modal is required.
### Screens to build
- Screens to Build
- Screen 1 — Entry Point: “What are you in the mood for?”
- Purpose: Narrow the catalog without introducing another complex browsing interface.
- UI elements
- StreamLine Spotlight branding.
- Heading: “What are you in the mood for?”
- Short supporting copy: “Pick one and we'll narrow things down.”
- Five mood selection cards/chips:
- Funny
- Thrilling
- Comforting
- Thought-Provoking
- Easy Watching
- Matching-title count on each mood where useful.
- Clear selected state.
- Primary continuation action if selection is not automatically applied.
- Skip secondary action.
- No login, profile setup, search field, or personalization questionnaire.
- Screen 2 — Feature Core: Mood-Filtered Spotlight Rail
- Purpose: Demonstrate that one simple input can produce a meaningfully smaller, more relevant discovery experience.
- UI elements
- Active mood indicator, e.g. “Thrilling”.
- Change mood control.
- Clear mood control.
- Spotlight rail of mood-matched titles.
- Title cards with:
- Poster/thumbnail
- Title
- Genre
- Runtime
- Short descriptor
- Selected/hover state for title cards.
- Primary View title or Watch action.
- Empty/fallback state when too few titles match.
- No advanced filtering controls on this screen.
- Screen 3 — Success / Confirmation: Title Selected
- Purpose: Validate that mood-based discovery moved the Wanderer toward a viewing decision.
- UI elements
- Selected title artwork.
- Title and short description.
- Active mood context: “Picked from your Thrilling Spotlight.”
- Primary Play CTA.
- Secondary Back to Spotlight action.
- Small Change mood action.
- Prototype success state/event when the user reaches the Play decision.
- No real playback implementation.
### Functional requirements
- Functional Requirements
- The prototype MUST expose exactly five primary moods: Funny, Thrilling, Comforting, Thought-Provoking, and Easy Watching.
- The user MUST be able to select one mood at a time, and the interface must visibly identify the active selection.
- Selecting a mood MUST produce a filtered Spotlight rail containing only titles explicitly mapped to that mood in the prototype dataset.
- Every prototype title MUST be mapped to at least one mood; the UI must never invent or infer a title-to-mood relationship at runtime.
- The user MUST be able to Skip mood selection, reaching the default Spotlight experience in no more than one interaction.
- The user MUST be able to change or clear an active mood from the filtered experience without restarting the prototype.
- A mood with too few matching titles MUST trigger a deterministic fallback state rather than displaying an empty rail; the fallback should offer another mood or return the user to the unfiltered Spotlight rail.
- The prototype MUST represent the critical measurement path: mood selected → filtered rail viewed → title selected → Play decision, enabling evaluation against the target of ≥70% reaching a relevant title decision without abandoning or repeatedly wandering.
### Smart behaviors (Situation → Outcome)
- Smart Behaviors
- Situation	Outcome
- If the user selects a mood	Then mark it as active and show the corresponding filtered Spotlight rail.
- If the user changes from Mood A to Mood B	Then replace the current rail with Mood B's predefined titles and update the active mood indicator.
- If the user chooses Skip	Then bypass mood filtering and show the default Spotlight rail immediately.
- If the user clears an active mood	Then restore the default Spotlight rail without resetting the rest of the prototype.
- If a mood has fewer than the minimum viable number of titles	Then show a controlled fallback explaining that there are limited matches and offer another mood/default Spotlight.
- If the user selects a title	Then navigate to the success/confirmation screen while retaining the selected mood context.
- If the user reaches the Play CTA	Then record/display the prototype's successful decision state; do not attempt real video playback.
- If the user repeatedly changes moods without selecting a title	Then preserve normal navigation; treat this behavior as a Wanderer signal for evaluation rather than adding prompts or forced recommendations.
### Technical constraints
- Technical Constraints
- This is a high-fidelity prototype, not production infrastructure.
- No external APIs.
- No real login or authentication.
- No recommendation engine.
- No LLM calls or AI-generated mood classification.
- No backend or database.
- Use a fixed local dataset of prototype titles and predefined mood mappings.
- Use React useState only for prototype state.
- Do not introduce Redux, Context, persistent storage, server state, or cross-device state.
- Do not build real streaming/playback functionality.
- Do not build analytics infrastructure; prototype events/states only need to be observable for evaluation.

## 3. The Logistics
### Features out
- AI-generated or dynamically inferred moods.
- Automatic detection of the user's mood.
- Full catalog-wide mood browsing.
- Persistent cross-device mood profiles.
### Edge cases & safety guard
- No mood selected
- Continue action remains inactive, or selection immediately advances depending on prototype interaction design.
- Skip remains available.
- User doesn't want mood-based discovery
- Skip must provide immediate access to default Spotlight.
- Do not repeatedly prompt the user to choose a mood.
- User chooses the wrong mood
- Change mood remains visible from the filtered rail.
- Switching requires no restart or confirmation dialog.
- Too few titles match
- Never show a broken or empty rail.
- Display a deterministic limited-results state and allow the user to select another mood or clear the filter.
- User repeatedly changes moods
- Do not block or penalize the behavior.
- Capture it as an evaluation signal because repeated switching may indicate that mood selection is creating rather than reducing wandering.
- Title belongs to multiple moods
- It may appear under each predefined applicable mood.
- Mapping must come from the fixed prototype dataset.
- Safety / hallucination guard
- The prototype must never generate, infer, or fabricate title attributes, mood matches, availability, descriptions, or personalized claims.
- All title information and mood mappings must come from the predefined local dataset.
- If required data is unavailable, display a neutral fallback rather than inventing content.
### Decision log
- Decision 1 — One mood, not combinations
- Decision: Users select only one mood at a time.
- Why: Multi-select creates combinatorial filtering complexity and additional decision-making—the exact cognitive load Spotlight is intended to remove. The prototype needs to validate whether a single emotional intent is sufficient to reduce Wanderers before adding sophistication.
- Decision 2 — Explicit selection, not AI inference
- Decision: Users tell Spotlight their mood; Spotlight does not attempt to predict it.
- Why: Explicit selection makes the causal hypothesis testable, avoids unreliable inference, requires no external AI infrastructure, and keeps engineering effort focused on whether mood-based narrowing improves discovery.
### Evals
- Eval 1 — Mood Matching Accuracy
- Target: 100% deterministic accuracy
- Every title displayed after mood selection must be present in that mood's predefined prototype mapping.
- Pass: 100% of displayed titles match the selected mood dataset.
- Fail: Any title appears because of generated, inferred, or incorrect mapping.
- Eval 2 — Decision Time & Completion
- Target: ≥70% successful decision completion
- At least 70% of test participants should progress:
- Mood selection → filtered rail → title selection → Play decision
- without abandoning the experience or repeatedly browsing/changing moods.
- Secondary observation: compare time-to-decision against the default unfiltered Spotlight path. Mood filtering should reduce, not increase, the work required to reach a title.
- Eval 3 — Guardrail / Safe Escape
- Target: ≥90% successful bypass
- At least 90% of Casual Browser / Power User test participants who do not want mood filtering must successfully Skip, clear, or change the mood without moderator assistance.
- Safety trigger: 0 instances of fabricated title information, invented mood mappings, forced mood selection, or dead-end empty states.

## MoSCoW scope
- **Must:** Present a small set of 4-6 moods on entry; Selecting a mood immediately filters the spotlight rail
- **Should:** Users can change or clear their mood
- **Could:** Allow users to select two moods together
- **Won't (now):** Build a full catalog-wide mood browsing system

---
**Builder hook:** Build a working prototype based on this PRD. Use the User Story as the core flow, Functional Requirements as build constraints, and prioritize speed and clarity over visual complexity.
