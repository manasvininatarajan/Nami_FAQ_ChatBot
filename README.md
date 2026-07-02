# Nami_FAQ_ChatBot

A simple FAQ chat widget for [naminycmetro.org](https://naminycmetro.org) that makes it easier for visitors to navigate the site and find information quickly — things like Helpline hours, classes, support groups, volunteering, and donating — without having to dig through multiple pages.

This is a self-directed demo project, not an official NAMI-NYC product.

## What it does

- Answers common questions about NAMI-NYC's programs in plain language, using bullet points for anything with multiple steps or options
- Asks a quick clarifying follow-up when a question is broad, so it can point people to the right specific program instead of listing everything
- Keeps a small set of safety guardrails given the subject matter:
  - A crisis resource bar (988 / 911) is always visible at the top of the chat window
  - Crisis language (English, Spanish, and Chinese) is detected client-side and immediately shown crisis resources, independent of the AI response
  - A visible notice explains that chats are processed by a third-party AI service, with a link to NAMI-NYC's privacy policy
  - The assistant only answers from a fixed knowledge base pulled from the real site — it's instructed to say "I don't know, contact the Helpline" rather than guess

## What it is not

- Not a crisis line, therapist, or substitute for NAMI-NYC's Helpline
- Not an official, deployed NAMI-NYC tool — this is a portfolio/demo build
- Not multilingual for general FAQ (crisis detection covers English/Spanish/Chinese; everyday Q&A is currently English only)

## How it works

Single self-contained HTML file — no build step, no dependencies. It calls the Anthropic API directly from the browser. Inside Claude.ai's artifact preview this works out of the box. For a real deployment, the fetch call would need to point at a small backend endpoint holding an API key server-side (flagged in the code as `TODO(host)`) — an API key should never live in client-side code.

## Try it

Open https://manasvininatarajan.github.io/Nami_FAQ_ChatBot/ in a browser (or view it as a Claude.ai artifact) and click the chat bubble in the bottom-right corner.

## Known limitations

- Crisis detection uses keyword matching, which is fast and dependable for defense-in-depth but will still miss indirect phrasing
- The knowledge base is hardcoded in the file — updating it currently requires editing source, not a CMS
- No rate limiting or usage monitoring — not production-hardened
