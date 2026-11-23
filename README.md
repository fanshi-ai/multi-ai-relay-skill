# Multi-AI Relay

An Agent Skill for running a multi-AI relay where **one lead agent does the work** and other AIs assist through their logged-in **web versions** — no API keys needed for the assisting models.

## The pattern

- **Fixed seats**: the lead agent executes and verifies; GPT takes the first bat (plans, problem-advisor questions), DeepSeek supervises and red-teams, Gemini arbitrates and locks the final version. The human is the only final decision-maker.
- **Web replies are candidates, never results**: anything a web AI returns is verified locally (live pages, files, frames, scripts) before it is adopted.
- **Fixed handoff format**: every bat returns 结论 / 依据 / 未决 (conclusion / evidence / open questions); the next bat gets the full handoff, not a paraphrase.
- **Role-rotation interrogation rounds**: for quality-critical work, the AIs take turns playing questioner and respondent, must concede what is true, and converge on a locked fix list.
- **Browser discipline**: one dedicated conversation per AI per topic, batch authorization, no credentials ever sent to a web AI.

## Install

```bash
npx skills add <owner>/multi-ai-relay-skill
```

Or copy `SKILL.md` into your agent's skills directory.

## License

MIT. By 繁世AI (Fanshi AI).
