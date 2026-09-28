# DataMan Requirements Register

## Project Context

The goal of this project is to modernize DataMan, a 1977 handheld math practice device, so it works reliably in a browser, can be understood without a printed manual, and gives learners clear feedback while they practice. The primary users are students practicing independently, often with a teacher or parent nearby. Parents and teachers are secondary stakeholders who want to understand what the learner practiced and whether progress is occurring.

## Evidence Notes

| ID | Evidence | Source |
|----|----------|--------|
| E-01 | Stakeholders say "modern" means working reliably in a browser, being understandable without a printed manual, and avoiding unnecessary screens. They did not specify a visual style or framework. | M2 Elicitation Decision Record, Investigation Path Q1 |
| E-02 | Parents and teachers want to understand what the learner practiced and whether progress is occurring. Stakeholders have not agreed on a detailed reporting dashboard. | M2 Elicitation Decision Record, Investigation Path Q2 |
| E-03 | The primary learner is a student practicing independently, often with a teacher or parent nearby. Exact device and access conditions are not yet confirmed. | M2 Elicitation Decision Record, Investigation Path Q3 |
| E-04 | Students may use school Chromebooks, phones, tablets, and home computers, and sessions may be interrupted before an intentional sign-out. | M2 Elicitation Decision Record, Complication |
| E-05 | Ms. Alvarez reported that learner disengagement follows repeated wrong answers, not the start of a session. | DataMan Elicitation Case, Interview |
| E-06 | A learner was surprised when the device revealed the answer and could not tell whether they were wrong or had run out of attempts. | DataMan Elicitation Case, Observation |
| E-07 | The manual establishes the three-attempt behavior as intentional and documents no warning before the reveal. | DataMan Elicitation Case, Document Analysis |
| E-08 | The learner enters both a problem and an answer, and DataMan indicates right or wrong. The manual states: "If after two tries the answer entered is still wrong, DataMan will display the problem with the correct result." | DataMan Manual, Answer Checker (Operating Notes) |
| E-09 | The manual states: "After 10 problems, two numbers are displayed" (number of right answers and number of problems tried), followed by a light show. | DataMan Manual, Answer Checker (Operating Notes) |
| E-10 | The manual states that "parents, teachers, or friends can put up to 10 problems into DataMan's memory for children to work." DataMan keeps score and gives two tries per problem. | DataMan Manual, Memory Bank (Operating Notes) |
| E-11 | The manual describes DataMan as "expressly designed for easy, rewarding, and enjoyable use, even by small children," and the story pages let a child learn the activities without an adult. | DataMan Manual, Hints for Parents and Teachers; A Word to Parents (Story) |
| E-12 | The manual describes only stored practice *problems*. It documents no record of what a learner practiced or of progress over time, and it says nothing about what is kept after power-off. | DataMan Manual, Memory Bank (Operating Notes); Power Saver Feature |

## Functional Requirements

**FR-01:** The system must allow a learner to enter a math problem and an answer and receive feedback on whether the answer is correct.
*Source/Rationale:* E-08. This is the core Answer Checker behavior of the original DataMan.

**FR-02:** The system must show the learner how many attempts remain on the current problem after each incorrect answer, before the correct answer is revealed.
*Source/Rationale:* E-05, E-06, E-07. Learners could not tell they were about to run out of attempts, and the manual documents no warning.

**FR-03:** The system must reveal the correct answer after a learner has made three incorrect attempts on a problem.
*Source/Rationale:* E-07, E-08. The reveal is documented, intentional behavior, and the elicitation evidence did not support removing it. The three-attempt limit follows the DataMan Elicitation Case used in this course; the manual's Answer Checker section describes two tries, and the course case is treated as the project baseline.

**FR-04:** The system must show the learner a score, made up of the number of correct answers and the number of problems tried, when a set of problems is completed.
*Source/Rationale:* E-09, E-10. Score feedback is documented behavior in Answer Checker and Memory Bank. The size of a "set" is unresolved (see OQ-05).

**FR-05:** The system must allow a parent, teacher, or learner to enter a set of problems for the learner to practice later.
*Source/Rationale:* E-10. This is the Memory Bank capability, which supports practicing a child's specific trouble problems. The maximum set size is unresolved (see OQ-05).

**FR-06:** The system must retain a record of the problems a learner has practiced so that the record is available in later sessions.
*Source/Rationale:* E-02, E-12. Adults want to understand what the learner practiced. The original manual has no such record, so this is a new stakeholder need.

**FR-07:** The system must allow a parent or teacher to view the retained record of what a learner has practiced.
*Source/Rationale:* E-02. Adults need visibility into learner activity. The format of this view is not yet decided (see OQ-02).

**FR-08:** The system must make a learner's previously completed work available again when the learner returns to a practice session that ended before an intentional sign-out.
*Source/Rationale:* E-04. Sessions may be interrupted, and completed work should not be lost.

## Non-Functional Requirements

**NFR-01:** Feedback shown after an incorrect answer must be available through keyboard navigation.
*Source/Rationale:* DataMan Elicitation Case, Requirements Surfaced (interaction and accessibility quality constraint).

**NFR-02:** Feedback shown after an incorrect answer must not rely on color alone to convey its meaning.
*Source/Rationale:* DataMan Elicitation Case, Requirements Surfaced (accessibility quality constraint).

**NFR-03:** The system must run in a standard web browser without requiring installation of additional software.
*Source/Rationale:* E-01, E-04. Stakeholders define "modern" as working reliably in a browser, and learners use a variety of devices. Which browsers and devices are in scope is still open (see OQ-03).

**NFR-04:** A first-time learner must be able to start a practice session without consulting a printed manual.
*Source/Rationale:* E-01, E-11. Stakeholders want the experience to be understandable without a printed manual, consistent with the original design goal of easy use by small children. This can be checked later with a simple usability observation.

## Open Questions / Assumptions

These items are not supported well enough to be confirmed requirements.

| # | Item | Type | Why it is unresolved |
|---|------|------|----------------------|
| OQ-01 | Should learners log in, or is another way to associate saved data with a learner acceptable? | Open question | The decision record calls for checking whether a login is viable. This affects FR-06 and FR-08 and must be balanced against accessibility and performance. |
| OQ-02 | What form should the parent/teacher view take (dashboard, printable summary, or something else)? | Open question | Stakeholders have not agreed on a detailed reporting approach (E-02). |
| OQ-03 | Which devices, browsers, and network conditions must be supported? | Open question | Chromebooks, phones, tablets, and home computers are mentioned, but access conditions are not confirmed (E-03, E-04). |
| OQ-04 | What counts as "progress," and how should it be shown? | Open question | Adults want to see progress if it is occurring, but no definition or measure has been given. |
| OQ-05 | Should the modern version keep the original limits (for example, 10 stored problems, 10 problems per score, one- or two-digit problem numbers, no negative answers)? | Open question | These limits come from the 1977 hardware and are documented, but no stakeholder has said whether they should carry forward. |
| OQ-06 | Which of DataMan's other activities (Electro Flash, Number Guesser, Wipe Out, Force Out, Missing Number) are in scope for modernization? | Open question | The manual describes them, but no stakeholder evidence says they must be included. Where the manual's story and operating notes disagree (for example, Wipe Out after two misses, difficulty levels), the correct behavior is also unconfirmed. |
| OQ-07 | What does "unnecessary screens" mean, and is there a target for how quickly a learner can start practicing? | Open question | Stakeholders raised the concern but gave no measurable threshold (E-01). |
| OQ-08 | How long should saved practice data be kept, and who may view it? | Open question | Not addressed in any evidence collected so far. |
| A-01 | Stakeholders want an easily digestible dashboard with quick or intuitive navigation. | Assumption | Inferred from stakeholder interest in progress, not stated by stakeholders. |
| A-02 | Colored buttons would make starting a game easier to understand. | Proposed solution | This is a design idea, not evidence. The underlying need is captured in NFR-04. Any color use must also satisfy NFR-02. |
| A-03 | A "memory bank" or similar storage mechanism should be used to save progress. | Proposed solution | This is an implementation choice. The underlying needs are captured in FR-06 and FR-08. Note that the original Memory Bank stores practice problems, not progress. |
