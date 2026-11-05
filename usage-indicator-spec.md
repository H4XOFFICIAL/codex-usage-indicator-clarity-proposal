# Usage Indicator Clarity and Reset Access

## Problem

In the observed compact sidebar, the usage control presents a circular indicator without an always-visible number. Its direction and meaning are not self-evident. The numeric weekly remaining value requires opening or hovering over the control, and using an available usage reset requires navigating elsewhere.

The supplied still image is not sufficient to prove that the ring is implemented incorrectly. Confirm the app version and compare the indicator at multiple authoritative values before filing it as a defect.

## Proposed Experience

1. **Choose the compact display.** Offer circle and `%` choices in the existing usage menu. Preserve the choice across restarts and keep it accessible in collapsed and expanded sidebars. In number mode, show only the percentage, centered above the account avatar, without a background. Fit the text within the avatar's width for values from `0%` to `100%`. Identify the allowance window and remaining value through the control's hover and accessible labels.
2. **Make the circle unambiguous.** For a remaining-allowance ring, start at twelve o'clock and fill clockwise as the remaining value increases. A full allowance is a full ring; an exhausted allowance is an empty track. Label the value and window on hover, keyboard focus, and in the accessible name. As allowance is consumed, the clockwise segment naturally shortens.
3. **Put resets in the usage menu.** Show a compact `Reset` action beside the available reset count when an earned reset is supported. Show reset availability separately from ordinary usage credits. On activation, confirm that an earned reset will be consumed, then show the actual service result. The action must not imply that every limit is eligible or that resets are unlimited.
4. **Keep the current view useful.** Retain the existing usage details and management path. Do not conflate plan allowance, reset credits, purchased usage credits, and context-window usage.

## States

- **Available:** show the official reset count and enable the action when a reset is supported and available. If the service has not yet established whether a window is eligible, allow the attempt and handle its result explicitly.
- **None:** show that no earned resets are available; do not imply that purchasing ordinary credits creates a reset.
- **Unknown or unavailable:** do not assume a zero balance or permit an unverified redemption; give an appropriate retry or management path.
- **Confirming:** identify the reset being consumed and provide a cancel action.
- **Success:** refresh the official allowance and reset balances. Do not infer that all windows became full.
- **No eligible limit, failure, or ambiguous response:** preserve the existing values, explain the result, and avoid duplicate redemption on retry.

## Acceptance Criteria

- Users can choose circle or numeric percentage without opening a separate settings journey, and their choice persists.
- The numeric display remains visible without hover, is centered over the account circle, fits within its width, and has no background. Hover and accessible labels identify its allowance window.
- A clockwise ring represents the same official remaining value as the numeric view at 0%, 50%, and 100%.
- A keyboard or screen-reader user can identify the window and remaining value and open the same menu.
- Eligible users can initiate a reset directly from the usage menu, understand that it consumes an earned reset, and cancel before redemption.
- Unavailable or failed states never claim success or fabricate an updated allowance.
- The prototype uses invented values and performs no real redemption.

## Relevant Requests

[#59247](https://github.com/openai/codex/issues/59247) discusses ambiguity of the usage icon. [#25561](https://github.com/openai/codex/issues/25561) requests a persistent remaining limit, while [#48025](https://github.com/openai/codex/issues/48025) asks to hide a persistent percentage. This proposal supports both preferences and adds the direct reset path.

OpenAI documents earned reset redemption and refresh of authoritative balances in the [Codex App Server documentation](https://learn.chatgpt.com/docs/app-server).
