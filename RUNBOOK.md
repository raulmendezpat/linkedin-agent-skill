# Weekly run

Used by the scheduled task. Steps:

1. Read `profiles/raul/voice.md`, the last two files in `plans/`, and the
   skills `li-plan`, `li-post`, `li-safe`, `li-human`.
2. Run `/li-plan` with voice.md as input. All output is in English. Themes
   (rotate, no theme twice in a week):
   - AI architecture (agentic systems, LLM integration patterns, AI on AWS/Azure)
   - AI governance (risk, assurance, review boards, policy into practice)
   - Responsible and ethical AI (fairness, transparency, accountability,
     human oversight in public services)
   - Cloud and integration architecture in government
   - Architecture governance and TOGAF
   - Lessons from 25 years across banking and government
3. Draft the 4 posts of the week with `/li-post` (3 hooks each, 1 full draft).
4. Run each draft through `/li-safe`, then
   `python3 -I skills/li-human/humanize.py` and `detect.py`. Only PASS or
   REVIEW drafts ship; FLAGGED ones are rewritten.
5. Write `plans/<monday>.md`: schedule, 4 drafts, li-safe verdicts, human
   scores, 10 people or companies to engage with (from voice.md readers, no
   private individuals invented), and 3 comment prompts.
6. Commit and push the plan file. Nothing is posted to LinkedIn.
