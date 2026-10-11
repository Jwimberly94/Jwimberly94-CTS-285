# DataMan Product Backlog

## Sources

This backlog uses these files from my repository:

- `docs/requirements.md`
- `docs/decisions/m3-backlog-triage-record.md`
- `docs/decisions/m3-product-owner-decision-record.md`

I revised `docs/requirements.md` after Module 2, and this backlog uses the revised version.

## Priority Order

1. US-01
2. US-02
3. US-03
4. US-04
5. US-05
6. US-06
7. US-07
8. US-08
9. US-09
10. US-10
11. US-11
12. US-12

## Stories

### US-01 — Enter a problem and answer and get feedback

**Requirement ID:** FR-01

**User Story:** As a learner, I want to enter a math problem and my answer and be told whether my answer is correct so that I know whether I understood the problem.

**Acceptance Criteria:**

- Given a learner is practicing, when they enter a problem and an answer and submit them, then the system accepts the submission.
- Given a learner submits a correct answer, when the system responds, then the learner sees feedback stating the answer is correct.
- Given a learner submits an incorrect answer, when the system responds, then the learner sees feedback stating the answer is incorrect.
- Given a learner submits several answers in a row, when each one is submitted, then feedback appears after every submission.

**Relative Effort:** M — Larger than the single-behavior feedback stories (US-02, US-03) because it covers both entering and checking, and the limits on problem size and answer values are still open (OQ-05).

**Dependency / Constraint:** None. Limits on problem and answer values are unresolved (OQ-05).

**Priority:** 1

**Readiness:** Move Forward

**Priority Rationale:** This is the core Answer Checker behavior (E-08), so it has the highest value. Nearly every other story builds on it, so delaying it blocks the rest of the backlog. It has no dependencies and its behavior is clear, which makes it a low-risk first commitment.

---

### US-02 — See attempts remaining after a wrong answer

**Requirement ID:** FR-02

**User Story:** As a learner, I want to see how many attempts I have left after a wrong answer so that I am not surprised when the correct answer is shown.

**Acceptance Criteria:**

- Given a learner is working on a problem, when they submit a 1st incorrect answer, then they see that 2 attempts remain.
- Given a learner has made 1 incorrect attempt, when they submit a 2nd incorrect answer, then they see that 1 attempt remains.
- Given the remaining attempts are shown, when the learner reads the message, then the correct answer has not yet been revealed.
- Given a learner has just submitted an incorrect answer, when an observer asks whether they are about to run out of attempts, then the learner can answer correctly.

**Relative Effort:** S — One clearly defined behavior that adds a count to feedback already built in US-01.

**Dependency / Constraint:** US-01. Uses the three-attempt baseline from FR-03; the manual describes two tries (E-08), so the baseline should be confirmed.

**Priority:** 2

**Readiness:** Move Forward

**Priority Rationale:** Learner disengagement follows repeated wrong answers (E-05), and a learner could not tell they were about to run out of attempts (E-06). That gives this story high value for small effort, and it only depends on US-01.

---

### US-03 — Reveal the correct answer after all attempts are used

**Requirement ID:** FR-03

**User Story:** As a learner, I want the correct answer shown after I have used all my attempts so that I can learn the right answer and move on.

**Acceptance Criteria:**

- Given a learner has made 2 incorrect attempts on a problem, when they submit a 3rd incorrect answer, then the correct answer is displayed.
- Given a learner has made fewer than 3 incorrect attempts, when the system responds, then the correct answer is not displayed.
- Given the correct answer is displayed, when the learner reads the message, then it states that the answer is shown because all attempts were used.
- Given a learner submits a correct answer on any attempt, when the system responds, then the problem ends without a reveal.

**Relative Effort:** S — One behavior that builds on the attempt count from US-02.

**Dependency / Constraint:** US-01 and US-02. Constraint: the three-attempt limit is the course baseline while the manual states two tries (E-08), so it should be confirmed before design.

**Priority:** 3

**Readiness:** Move Forward

**Priority Rationale:** The reveal is documented, intentional behavior and the evidence did not support removing it (E-07). It completes the feedback loop started by US-01 and US-02 at small effort, so it follows them directly.

---

### US-04 — Reach feedback with the keyboard

**Requirement ID:** NFR-01

**User Story:** As a learner who navigates with a keyboard, I want to reach and read the feedback after a wrong answer without a mouse so that I can keep practicing independently.

**Acceptance Criteria:**

- Given a learner is using only a keyboard, when they enter an answer and submit it, then the submission completes without a mouse.
- Given a learner has submitted an incorrect answer, when they navigate with the keyboard, then they can reach and read the feedback and the remaining attempts.
- Given the full answer-and-feedback flow, when it is tested with only a keyboard, then no step requires a mouse or touch input.

**Relative Effort:** S — A single well-defined quality check applied to behavior already built in US-01 and US-02.

**Dependency / Constraint:** US-01 and US-02, so that there is feedback to reach. Constraint: it must be part of acceptance for the feedback stories, not added afterward.

**Priority:** 4

**Readiness:** Move Forward

**Priority Rationale:** Accessibility is a stated quality constraint (NFR-01). The Product Owner exercise showed that a keyboard-access problem found late becomes release-critical, so it is cheaper and lower-risk to plan it in with the feedback stories. It is ranked right after the core feedback loop because it needs that loop to exist first.

---

### US-05 — Understand feedback without relying on color

**Requirement ID:** NFR-02

**User Story:** As a learner who may not distinguish colors, I want feedback to make sense without relying on color so that I can tell whether I was right or wrong.

**Acceptance Criteria:**

- Given feedback is shown after an answer, when the learner views it, then it includes text or another non-color cue that states the result.
- Given correct and incorrect feedback, when each is viewed in grayscale, then a person can still tell them apart.
- Given color is used in feedback, when the feedback is checked, then the meaning is also conveyed in a way that does not depend on color.

**Relative Effort:** S — A single quality check applied to the existing feedback.

**Dependency / Constraint:** US-01 and US-02. Applies to any later color use (A-02 is an unvalidated design idea and is not in scope).

**Priority:** 5

**Readiness:** Move Forward

**Priority Rationale:** It is a stated accessibility constraint (NFR-02) that is small and ready. It is cheapest to meet while feedback is first built, so it is ranked with the other ready stories ahead of work that still needs refinement.

---

### US-06 — Use DataMan in a standard browser

**Requirement ID:** NFR-03

**User Story:** As a learner, I want to use DataMan in a standard web browser without installing anything so that I can practice on whatever device I have.

**Acceptance Criteria:**

- Given a learner has a standard web browser, when they open DataMan, then they can use it without installing additional software.
- Given a browser and device on the supported list, when a learner completes the core answer-and-feedback flow, then it works as described in US-01 to US-03.
- Given the team has decided which browsers and devices are in scope, when the backlog or requirements are read, then that list is written down.

**Relative Effort:** M — Affects every other story, and the amount of testing depends on a supported-device list that does not exist yet.

**Dependency / Constraint:** OQ-03 (which devices, browsers, and network conditions are in scope). The story cannot be fully tested until that list exists.

**Priority:** 6

**Readiness:** Refine

**Priority Rationale:** Stakeholders define "modern" as working reliably in a browser (E-01) and learners use several kinds of devices (E-04), so the value is high. It is ranked below the ready stories because its scope depends on OQ-03. Answering OQ-03 early reduces risk for the whole backlog.

---

### US-07 — Start practicing without a printed manual

**Requirement ID:** NFR-04

**User Story:** As a first-time learner, I want to start a practice session without a printed manual so that I can begin on my own.

**Acceptance Criteria:**

- Given a first-time learner and no printed manual, when they are asked to start a practice session in a simple usability observation, then they start without consulting a manual.
- Given a usability observation, when a learner needs help to start, then the observer records it.
- Given the team has decided on a target for how quickly a learner should be able to start (OQ-07), when observation results are compared with it, then the result shows whether the target is met.

**Relative Effort:** M — Needs a usability observation and a target that is not yet defined.

**Dependency / Constraint:** US-01, so that there is a session to start. OQ-07 (no measurable threshold for "unnecessary screens" or for how quickly a learner should start).

**Priority:** 7

**Readiness:** Refine

**Priority Rationale:** Stakeholders want DataMan understandable without a manual (E-01) and the original device was designed for easy use by small children (E-11), so the value is high. Without a measurable target it is not testable, so it ranks below the stories that are ready now.

---

### US-08 — See my score at the end of a set

**Requirement ID:** FR-04

**User Story:** As a learner, I want to see how many answers I got right out of the problems I tried when I finish a set so that I can see how I did.

**Acceptance Criteria:**

- Given a learner has completed a set of problems, when the set ends, then the learner sees the number of correct answers.
- Given a learner has completed a set of problems, when the set ends, then the learner also sees the number of problems tried.
- Given a completed set, when the score is shown, then the numbers match the answers the learner submitted in that set.

**Relative Effort:** S — A small behavior once the size of a set is known.

**Dependency / Constraint:** US-01. OQ-05 (the size of a "set" is unresolved).

**Priority:** 8

**Readiness:** Refine

**Priority Rationale:** Score feedback is documented behavior (E-09, E-10) and is small, but "set" is not defined, so it cannot be tested as written. It follows the core feedback loop and the OQ-05 decision.

---

### US-09 — Enter a set of problems to practice later

**Requirement ID:** FR-05

**User Story:** As a parent, teacher, or learner, I want to enter a set of problems for the learner to practice later so that the learner can work on their specific trouble problems.

**Acceptance Criteria:**

- Given a parent, teacher, or learner wants to prepare practice, when they enter a set of problems, then the set is accepted.
- Given a set has been entered, when the learner later starts practicing, then the learner can practice that set.
- Given a maximum set size has been decided (OQ-05), when someone enters more problems than the maximum, then the system tells them clearly.

**Relative Effort:** M — Involves entering, storing, and later using a set, and its limits are undecided.

**Dependency / Constraint:** US-01. OQ-05 (maximum set size). Whether entered sets must carry over between sessions overlaps with OQ-01.

**Priority:** 9

**Readiness:** Refine

**Priority Rationale:** This Memory Bank capability (E-10) supports targeted practice and has clear value, but it is not needed for the basic practice loop and its limits are unresolved.

---

### US-10 — Keep a record of what a learner practiced

**Requirement ID:** FR-06

**User Story:** As a parent or teacher, I want the problems a learner has practiced to be kept for later sessions so that I can understand what the learner worked on.

**Acceptance Criteria:**

- Given a learner has practiced problems, when they return in a later session, then a record of those problems is still available.
- Given a retained record, when it is read, then it identifies which learner practiced the problems (method per OQ-01).
- Given a retained record, when it is read, then it shows the problems practiced and does not claim to measure progress (OQ-04).

**Relative Effort:** L — Depends on several unresolved decisions and unlocks other stories.

**Dependency / Constraint:** OQ-01 (login or another way to link data to a learner) and OQ-08 (how long data is kept and who may see it). Unlocks US-11 and US-12.

**Priority:** 10

**Readiness:** Refine

**Priority Rationale:** This is a new stakeholder need with no precedent in the manual (E-02, E-12) and it unlocks two other stories, so its value is high. It is not ready, so it is ranked after the stories that can move forward and should be refined once OQ-01 and OQ-08 are answered.

---

### US-11 — Get my completed work back after an interrupted session

**Requirement ID:** FR-08

**User Story:** As a learner, I want my previously completed work to be available again if my session ended before I signed out so that an interruption does not lose my work.

**Acceptance Criteria:**

- Given a session ended before an intentional sign-out, when the learner returns, then their previously completed work is available.
- Given work was completed before the interruption, when the learner returns, then none of it is lost.
- Given the learner has returned, when they continue, then they can keep practicing.

**Relative Effort:** L — Depends on the identity and retention decisions and cannot be sized well until they are made.

**Dependency / Constraint:** OQ-01 (how a returning learner is recognized) and the retention approach from US-10.

**Priority:** 11

**Readiness:** Refine

**Priority Rationale:** Sessions may be interrupted on shared or school devices (E-04), so lost work would affect learners directly. It cannot move until US-10 and OQ-01 are resolved, so it follows US-10.

---

### US-12 — View what a learner has practiced

**Requirement ID:** FR-07

**User Story:** As a parent or teacher, I want to view the record of what a learner has practiced so that I can see what they worked on.

**Acceptance Criteria:**

- Given a retained practice record exists, when a parent or teacher opens it, then they see the problems the learner practiced.
- Given someone who is not authorized, when they try to open a learner's record, then it is not shown (rules per OQ-08).
- Given the form of the view is decided (OQ-02), when it is built, then it presents the record in that form.

**Relative Effort:** L — Depends on US-10 and on decisions about the form of the view, progress, and access.

**Dependency / Constraint:** US-10, OQ-02 (form of the view), OQ-04 (what counts as progress), and OQ-08 (who may view data).

**Priority:** 12

**Readiness:** Defer

**Priority Rationale:** Stakeholders want visibility (E-02), but they have not agreed on a reporting approach, and the dashboard idea (A-01) is an assumption. Committing now would risk rework, so it is deferred until US-10 exists and the open questions are answered.

---

## Open Questions Carried Forward

- **OQ-01:** Waits on US-10 and US-11; also affects US-09. No story assumes a login.
- **OQ-02:** US-12 waits on the form of the parent/teacher view.
- **OQ-03:** US-06 waits on the supported devices, browsers, and network conditions.
- **OQ-04:** US-10 and US-12 wait on what counts as progress. No story claims to measure progress.
- **OQ-05:** US-01 (limits), US-08, and US-09 wait on set size and the original limits.
- **OQ-06:** No story exists because no stakeholder evidence says the other DataMan activities must be included.
- **OQ-07:** US-07 waits on a measurable target for starting a session.
- **OQ-08:** US-10 and US-12 wait on data retention and who may view it.
- **A-01, A-02, A-03:** Not turned into stories. They are an assumption and proposed solutions, not validated requirements. The needs behind them are covered by US-10, US-11, US-12, and US-07.

## Revisions After Triage and Release Planning

- **US-04 and US-05 — moved up and written as their own stories — Product Owner decision record.** The exercise showed that a keyboard-access failure became release-critical when found late. Accessibility is planned in with the first feedback stories instead of being left for the end.
- **US-01 to US-05 — grouped as the first release — Product Owner decision record.** Only ready, high-value work with no unresolved dependencies is ranked first. Nothing cosmetic is added to fill space (for example, the colored-button idea in A-02 is excluded).
- **US-10, US-11, US-12 — marked Refine or Defer — Product Owner decision record.** These are high value but not ready, depend on unresolved work, and are large. Like the AI recommendations and parent dashboard items in the exercise, they are kept visible but not committed.
- **US-06 — ranked above other refinement work — Product Owner decision record.** Answering OQ-03 early reduces risk for the whole backlog.
- **US-10 — ranked before US-11 and US-12 — Product Owner decision record.** It unlocks two other stories, as the transfer prompt asked me to consider.
