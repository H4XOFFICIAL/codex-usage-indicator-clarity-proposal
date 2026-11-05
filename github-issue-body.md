### What variant of Codex are you using?

Codex desktop app on Windows x64. The installed Windows package reported version `26.1029.7803.0` on 6 November 2026; the exact build shown in the About dialog has not been verified.

### What feature would you like to see?

Make the compact usage indicator easier to read and provide a direct way to use an available reset from its menu.

In the observed Windows sidebar, the usage control is a small ring above the account icon. The menu shows the weekly percentage, but reading it repeatedly requires hovering or opening the menu. The ring's direction and whether it represents usage or remaining allowance are not obvious at a glance. Using an available reset also requires navigating away from this compact view.

I suggest:

- Let users choose the circle or an always-visible percentage using a `%` option in the existing usage menu. In percentage mode, show only the remaining number, without a background, centered above and fitted within the account circle's width. The accessible name and hover detail should identify the usage window.
- For the circle, use a clearly labeled remaining-allowance arc that starts at the top and fills clockwise as remaining allowance increases. A single screenshot does not establish whether the current ring is incorrect; this is a request for clear, consistent semantics.
- Add a small **Reset** button beside the available reset count in that menu. Keep earned resets distinct from ordinary usage credits, ask for confirmation before redemption, and refresh the actual balances and eligible limits after the service responds.
- Preserve **Manage usage** and clearly handle unavailable resets, no eligible limit, and errors. Do not treat a failed or uncertain request as a successful reset.

The usage percentage should refer to a named plan-allowance window, not the conversation's context window or a purchased credit balance.

### Related requests

[#59247](https://github.com/openai/codex/issues/59247) discusses the current icon's ambiguity, [#25561](https://github.com/openai/codex/issues/25561) requests persistent remaining usage, and [#48025](https://github.com/openai/codex/issues/48025) asks for a way to hide a persistent percentage. This proposal combines a choice of presentation with direct access to an earned reset.

### Prototype and feedback

I have prepared a [sanitized interactive mockup](https://h4xofficial.github.io/codex-usage-indicator-clarity-proposal/) using example values. It does not connect to an account or redeem a real reset. OpenAI's [Codex App Server documentation](https://learn.chatgpt.com/docs/app-server) describes earned-reset availability and redemption outcomes.

Would OpenAI consider providing usage resets or credits in recognition of the time spent developing and testing this proposal?
