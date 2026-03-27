# Self-Review Writer

Write your self-assessment for your company's review tool. Produces project impact descriptions, competency self-assessments (current level / next level), principles, and growth plan — all within character limits, fact-checked, strategically calibrated.

## Usage

```
/self-review [cycle]
```

Default cycle: current review period.

## Context: Review System

- **Three evaluation axes**: Impact (Volume/Quality/Efficiency/Complexity), Competencies (current level / next level per competency), Principles (your company's defined principles)
- **Rating scale**: Below / Meet / Above for Impact and Principles. Yes/No/Don't Know for competency criteria.
- **Who reads this**: Manager (may have limited context), Coach, Calibration panel (senior managers + People Partners who don't know you)
- **Your self-assessment is the anchor** — especially when the manager is new. If you say Meet, they have no reason to push Above.

## Workflow

### 1. Load Context

Read in order:
1. `brain/North Star.md` — current goals and focus
2. `perf/<cycle>/Review Brief.md` — the full private review brief
3. `perf/<cycle>/Review Brief - Manager.md` — what the manager has seen
4. Previous cycle review — baselines
5. Quarterly brag notes covering the period
6. All competency notes in `perf/competencies/`
7. `perf/Performance Framework.md` — evaluation structure (if exists)
8. Key work notes for submitted projects

### 2. Draft Projects

For each submitted project (1000 chars, no dashes):
- Open with your role and scope
- Hit all four Impact dimensions without naming them: what was delivered (Volume), how good it was (Quality), how the process was managed (Efficiency), whether scope expanded (Complexity)
- Include specific evidence: numbers should be factual (PR counts, team size, timeline)
- End with outcome or significance

Rate each project Meet or Above. Decide all ratings at the end together — calibrate the full picture before committing.

### 3. Draft Competencies

For each competency, decide current level (Yes/No) and next level (Yes/No):
- Read the level criteria from the competency note
- Check each sub-criterion: is there concrete evidence?
- If saying Yes to next level, every sub-criterion should be defensible — missing the primary criterion undermines credibility

Draft 1000-char text per YES answer:
- **Competency texts are NOT project descriptions** — the project section already covers WHAT. Competency texts cover HOW you applied the skill.
- Lead with behaviors and decisions, not deliverables
- Reference the previous cycle baseline: "Previously Meet, this period X" shows trajectory
- Calibrate jargon per audience: technical for Architecture/Functional Expertise, behavioral for Communication/Planning
- No overlap between current level and next level texts for the same competency — use different evidence or different framing

### 4. Draft Principles

For each principle (1000 chars):
- Reference the previous cycle baseline and any specific growth feedback
- Lead with the strongest evidence
- If the rating changed from last cycle, make the growth explicit

### 5. Strategic Calibration

Before finalizing, review the full picture:

**Impact**: Are the ratings defensible? Is there one genuine Meet to show calibration, or are all Above justified?

**Competencies**:
- Are next-level YES answers defensible on EVERY sub-criterion?
- Would you be comfortable if a calibration reviewer challenged any specific answer?
- Does claiming YES here protect or undermine the credibility of other next-level claims?

**Principles**: Does the pattern from last cycle to this cycle show growth?

**Audience check**: Will the manager (who may be new) have enough context to defend these ratings in calibration, or does the written evidence need to do the heavy lifting?

### 6. Quality Checks

- [ ] All sections under 1000 chars (use `.claude/scripts/charcount.sh <file> "<section>" [subsection]`)
- [ ] No dashes (em-dashes, en-dashes) — some review tools count these differently
- [ ] Every factual claim backed by vault evidence
- [ ] No fabricated decisions ("chose X over Y" when Y was never considered)
- [ ] No self-undermining language in next-level YES texts ("not yet at yearly scope")
- [ ] Dates verified — check day of week before claiming "weekend work"
- [ ] No references to specific people's performance issues — don't volunteer information about others' struggles
- [ ] Growth baselines stated for competencies and principles
- [ ] Technical jargon calibrated per audience

### 7. Fact-Check Pass

Enter plan mode. For every claim:
- Is it in the vault? Which source?
- Is it first-hand or inferred?
- Could a reviewer challenge it with "what's your evidence?"
- If the claim names a file, function, or flag — does it still exist?

Flag and fix anything that doesn't pass.

### 8. Save

Save draft to `thinking/review-drafts.md` for copy-pasting.
After submission, promote to `perf/<cycle>/Self-Review.md`.

## Lessons Learned

These come from past review cycles and should be applied going forward:

1. **Strategic Meet only works when the assessor has independent context.** With a new manager, your self-assessment IS the anchor. Don't undersell.
2. **Charcount early and often.** Use the script after every draft, not after pasting into the review tool.
3. **The "no dashes" rule exists** because some review tools may count special characters differently.
4. **Peer reviews feed into your competency ratings.** What peers write about you is visible to the manager. What you write about peers builds your reputation as a thoughtful evaluator.
5. **Fact-check before submitting.** Plan mode for verification has caught fabricated architectural decisions, references that shouldn't be in a review, and date claims where the days of the week were wrong.
