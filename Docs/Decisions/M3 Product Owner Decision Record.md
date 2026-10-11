# M3 Product Owner Decision Record

## Scenario
StudyTrack release planning under constrained capacity.

## Round 1 — Capacity 13
- ST-01: Create a study task (3 pts)
- ST-02: Mark a study task complete (2 pts)
- ST-03: Recover a missed task (3 pts)
- ST-04: Keyboard-accessible task entry (2 pts)

**Why this release slice was defensible:**
All the items are high value and ready to go, and their dependencies are covered by ST-01, which is already included. Nothing is blocked or needs more work before starting.
This slice covers both planning (ST-01, ST-04) and recovery (ST-02, ST-03) without adding too many features at once.
It leaves 3 points unused, and I think that's fine. The only item that fits is ST-06, which is mostly cosmetic and doesn't really help with the main goal. I'd rather leave those points open than add something that doesn't bring much value.

**One intentional deferral and why:**
Deferred Item: ST-07 AI Study Recommendations

I would hold off on ST-07 for now because there are still too many things we don't know. The data and rules for making recommendations haven't been figured out yet, and the study-history data it needs isn't available. Trying to do this now could cause more work and delay the project.

Since it's not a must-have feature for basic planning and recovery, I think we should focus on getting the main features done first. Once we have the data we need, we can come back to ST-07 and work on it for a future release.

## Complication
Capacity dropped from 13 to 10 points. Keyboard accessibility testing revealed that task entry cannot reliably be completed with keyboard navigation, so ST-04 became release-critical.

## Revised Release Slice — Capacity 10
- ST-01: Create a study task (3 pts)
- ST-02: Mark a study task complete (2 pts)
- ST-03: Recover a missed task (3 pts)
- ST-04: Keyboard-accessible task entry (2 pts)

### Removed after complication
- None

### Added after complication
- None

**What changed and why:**
**What changed in my plan, and why**

My selected items stayed the same because they already add up to 10 points. The developer reassignment used up the extra 3 points I had left over, so I didn't have to remove anything.

ST-04 is now a must-have because keyboard users are having trouble completing task entry. Since this issue has to be fixed before release, I need to make sure it stays in the plan.

I also didn't add any extra features. ST-05 would put me over the limit, and ST-06 is mostly cosmetic. ST-07 and ST-08 still need more work before they're ready. I think it's better to stick with the main features and make sure everything works before adding more.

**Tradeoff accepted:**
- **No extra room for problems.** I'm using all 10 points, so if something takes longer than expected or bugs come up, it could delay the release. I accepted this because all four items are important and ready to go. Removing any of them would take away from the main goal of planning and recovering missed tasks.
- **Some features will have to wait.** ST-05 (weekly progress summary) and ST-06 (custom color themes) can be added in a future release. Students will have the main features they need first, but they won't have the extra progress information or customization yet.

## Transfer to DataMan
Before finalizing your DataMan backlog, review whether any item is high value but not ready, depends on unresolved work, consumes disproportionate effort, or should move because it reduces risk or unlocks other work.
