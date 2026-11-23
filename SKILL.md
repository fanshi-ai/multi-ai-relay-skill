# Multi-AI relay (Muse leads, web AIs assist)

the user's standing relay: Muse （the lead agent） leads and executes; GPT, DeepSeek and Gemini assist through their logged-in web versions in Muse's cloud browser. No API keys for GPT/Gemini exist — never design a step that needs one. the user is the only final decision-maker.

## Fixed seats (do not re-negotiate per task)

- **Muse （the lead agent）**: lead, all generation/execution, handoffs, local verification, final summary to the user.
- **GPT**: first bat — plans, problem-advisor questions, context and cross-asset continuity review, the user's production system maintenance drafts.
- **DeepSeek**: supervisor / red team — attacks the previous bat's output, strict acceptance, 一票否决 on hard red lines only (readable text, identity drift, wrong colors, missing characters); minor flaws are warnings, not blocks.
- **Gemini**: advisor / arbiter — accuracy and structure review, storyboard breakdowns, final ruling when GPT and DeepSeek disagree.
- **the user**: only final decision. His stated 口径 always outranks any model's suggestion (e.g. never drop a point he ordered kept just because a model advises it).

## Relay order

1. GPT produces the plan or answers the advisor questions.
2. DeepSeek critiques it (挑刺）, with the user's hard constraints restated in the prompt.
3. Gemini arbitrates and locks the final version.
4. Muse executes and verifies locally, then reports the result to the user in one short message.

Skip a bat only when the task is trivial or the user names a different order. Parallel same-question rounds are allowed for copy/cover opinions; label them 并行轮次， never present them as relay conclusions.

## Role-rotation interrogation rounds （轮流互问）

For quality-critical work (upgrading a film, a system, a plan), run interrogation rounds on top of the fixed seats:

- Each round, one AI plays **questioner** （问题顾问）: it does not answer — it asks the sharp questions the current draft must survive, and names what evidence would settle each one.
- Roles rotate every round: GPT questions → DeepSeek answers/defends → Gemini questions the defense → GPT defends… Nobody keeps the same role two rounds in a row; the questioner of round N becomes a respondent in round N+1.
- The next AI receives the full Q&A log so far (questions, answers, conceded points) and must (a) answer the open questions addressed to it, (b) concede what is true instead of defending everything, (c) add its own questions for the next respondent.
- Muse （the lead agent） is also a respondent: when questioned, answer honestly with local evidence (frames, files, measurements), never bluff.
- Stop when questions stop producing new concessions or fixes, or after the round count the user set. Muse then locks the converged list （定版清单） and executes it.
- Log every question and answer in the task's note file (like questions-log.md); the log is the audit trail, the chat only gets the converged list.

## Task table per bat

- Send each bat only: the locked content it must not change, the minimum material it needs, and a compact output requirement.
- Require the fixed three-part handoff: 结论 / 依据 / 未决. The next bat receives the previous bat's full handoff plus the original task, not a paraphrase.
- Restate the user's hard constraints verbatim in every bat (keys available, free-first, hardware, delivery rules) so no bat recommends a paid or impossible route.

## Web replies are candidates, never results

- Anything a web AI returns (star counts, licenses, prices, "facts") is a candidate until Muse verifies it locally: live GitHub page, file readback, frame check, script run.
- Only the verified part is adopted; say plainly what failed verification (e.g. a recommended repo that turns out to have 2 stars).
- Input unchanged → do not re-ask the same bat the same question.

## Browser discipline

- One dedicated conversation per AI per topic; follow-ups stay in it. Start a new conversation only when the topic or factual boundary changes. Record each conversation URL in the task's note file.
- Batch authorization: once the user approves a relay, send all prepared bats without asking again per message.
- Never send credentials, API keys, or unredacted private data to a web AI. Files with keys never leave the machine.
- Images go to Gemini/GPT only as frames or stills; DeepSeek and Gemini cannot watch video or hear audio — verify motion and sound locally, send them keyframes and transcripts. Gemini takes at most 10 attachments per message.
- If a send's status is unclear, check the last message in that tab first; retry once in the same tab, then report the block honestly.

## Reporting

- One short result message to the user per relay: what each bat concluded in one line, what Muse verified, what is still open. No play-by-play.
- Save the full relay record (prompts, replies, verification notes) in the task's workspace note; link it, don't paste it into chat.
