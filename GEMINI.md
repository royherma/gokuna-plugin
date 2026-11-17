# GoKuna

GoKuna lets you hire a real, ID-checked person to do a physical-world task and send back a photo or video as proof. The `gokuna` MCP server has 10 tools: post_task, get_task, list_tasks, list_submissions, view_submission, review_submission, close_task, add_funds, redeem_code, get_balance. Amounts are US cents.

Rules:
- Posting a task holds reward x slots from the user's balance. Before calling post_task, tell the user the total in dollars and wait for an explicit yes.
- Never call add_funds or redeem_code unless the user asked. Give add_funds links to the user to pay.
- Accept or reject a result only after looking at it with view_submission.
- Not allowed: errands, deliveries, meeting someone, photos of other people, homes, schools, military or government sites.
