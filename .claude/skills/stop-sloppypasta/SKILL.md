---
name: stop-sloppypasta
description: "Check AI-assisted text before the user sends it to other people, using the six Stop Sloppypasta rules (Read, Verify, Distill, Disclose, Share only when requested, Share as a link). Use when the user is about to paste, forward, post, or email something an AI wrote or helped write — a Slack/Teams/WhatsApp message, email, doc comment, research summary, or answer to a colleague's question — or asks 'is this ok to send', 'review before I send', 'make this less AI', 'sloppypasta', or 'should I disclose AI'. Also apply it to your own output when the user says they will forward it. For polishing marketing copy itself, see copy-editing."
metadata:
  source: https://github.com/ahgraber/stopsloppypasta (MIT, Alex Graber)
---

# Stop Sloppypasta

**Sloppypasta** (n.): verbatim LLM output copy-pasted at someone — unread,
unrefined, and unrequested. It is rude because it hands the recipient the work
the sender skipped: reading, checking, and cutting it down. The text was free to
write but still costs the same to read, plus a verification tax, because the
reader cannot tell what the sender checked.

Your job is to turn a draft into something a person would be glad to receive,
or to tell the user honestly that it should not be sent. Answer in the user's
language.

## Inputs to establish first

Ask only for what you cannot infer from the conversation:

1. **The draft** — the text they plan to send.
2. **Where and to whom** — channel (chat thread, email, doc, public post) and
   the recipients.
3. **The ask** — what did the recipient actually request? Paste the question or
   the thread if there is one. "Nobody asked" is a valid answer.
4. **What the user checked** — which facts, numbers, and links they have
   personally confirmed.

## The six rules

Check the draft against each rule and report a verdict per rule
(✅ pass / ⚠️ needs work / ❌ fails) with one line of why.

1. **Read.** Has the user read the whole thing? If they cannot say what it
   claims, they have not. Summarize its claims in 3 bullets and ask the user to
   confirm they agree with each.
2. **Verify.** List every checkable claim: figures, prices, dates, names,
   quotes, laws, links, "studies show". Mark each as *verified by user*,
   *verified by you* (only if you actually checked it with a tool this session
   and can cite the source), or *unverified*. Never mark a claim verified on
   your own say-so. Flag anything likely stale (pricing, versions, policies,
   "latest") — model knowledge is months old. Unverified claims must be checked,
   cut, or explicitly labeled as unverified.
3. **Distill.** Cut to what the recipient needs for *their* question or
   decision. Remove generic background, restated context, headings and bold in
   chat messages, listicles where a sentence works, and filler. Tie it to the
   specifics of their situation (their product, numbers, thread). Target: the
   recipient should spend less time reading than the user spent preparing it.
4. **Disclose.** Say how AI helped, proportionate to how much it did:
   - Read, verified, and edited → send as theirs, ideally with a short note
     ("drafted with AI, I checked the numbers").
   - Raw or lightly edited output → say so plainly, and say what was *not*
     checked.
   - Optionally share the prompt or method when it helps the reader judge it.
   Passing AI work off as personal research (the Ghostwriter) spends the
   sender's credibility; flag it.
5. **Share only when requested.** If nobody asked, recommend not posting it, or
   replacing it with one human sentence ("I looked into this — happy to share
   notes if useful"). Never drop unsolicited AI text into a live discussion
   (the Eager Beaver). Answering a question someone asked *a person* with
   "ChatGPT says…" (the OrAIcle) fails this rule too — they wanted the user's
   own view.
6. **Share as a link.** In chat, anything longer than a short message goes in a
   doc or attachment with a 1–3 line summary inline, so recipients choose
   when and whether to read it. Never let a paste take over the thread.

## Output

1. **Verdict table** — the six rules with ✅/⚠️/❌ and a one-line reason.
2. **Claims to verify** — the list from rule 2, unverified items first.
3. **Recommendation** — one of: *send the revised version*, *send as a link
   with this summary*, *reply with one line instead*, or *don't send*.
4. **Revised message** — ready to paste, in the channel's register (plain
   sentences in chat, no headings), with the disclosure line included where
   rule 4 calls for one. Keep the user's voice and opinions; do not add claims
   the draft did not make. Leave unverified claims out, or mark them
   `[unverified]`.

Keep the review short. A sloppypasta review that is itself a wall of text
defeats the point.

## Patterns to recognize

| Pattern | Looks like | Fix |
|---|---|---|
| Eager Beaver | Unrequested AI essay dropped into a live discussion | One line of the user's own take; offer a link |
| OrAIcle | "ChatGPT says:" + generic answer to a specific question | Answer the actual question in the user's words, or say "I don't know" |
| Ghostwriter | AI research presented as personal work, no sources or dates | Verify, cite sources and dates, disclose AI help |

AI should speed up the user's work or improve what they send. It should not
replace thinking about what they send, or make their productivity someone
else's burden.
