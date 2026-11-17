---
name: review-results
description: Check the photos and videos people sent back for a GoKuna task, accept the good ones (the person gets paid) and reject the bad ones with a reason. Use when the user asks how a GoKuna task is going, wants to see results, or says to approve, pay or reject a submission.
---

# Review GoKuna results

1. `list_submissions` (add `taskId` to narrow it to one task). Each result shows a status and the time it is accepted automatically if nobody answers. Review before that time.
2. `view_submission` for each pending one. Photos come back as an image: check them against the task's instructions, one instruction at a time.
3. Decide with `review_submission`:
   - `accepted` pays the person. Use it only when every instruction is met and the proof is legible.
   - `rejected` needs a `reason` the person can act on ("price tag not readable, retake closer"). The slot reopens for someone else.
4. Reject only for a real miss against the instructions, never for style. Accepting is irreversible money, so when unsure show the user the result and ask.
5. When enough good results are in, `close_task` to stop new people and get back the money for slots nobody took. Report the final count accepted and the amount returned.

Never accept results in bulk without viewing each one.
