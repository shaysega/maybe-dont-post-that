# Maybe Don't Post That

A Claude skill that pressure-tests and rewrites public-facing leadership communication **before it ships** - LinkedIn/X posts, job listings, all-hands notes, layoff announcements, "culture" manifestos, customer apologies.

It catches the specific failure mode where a draft *feels* bold and motivating to the author but reads as contemptuous to everyone else - the kind of post that ends in a clarification thread. It is **not** a blandness filter: strong, opinionated, demanding writing is encouraged. The job is to separate "provocative because it says something true and hard" from "provocative because it punches down."

## The one idea it runs on

> Words travel without their author. Once something is published, the context stays behind: your tone, your intent, the room you imagined, what you *meant*. Only the words travel - and they have to survive on their own, in front of people who don't know you and won't fill in the gaps in your favor.

So the core test for any draft is: does it hold up with nothing but the words - stripped of your intent, your context, your tone? If what's left still says what you want it to say, ship it. If defending it would take "but what I meant was…", that meaning never made it onto the page - fix it now.

## What you get

When you hand it a draft, it responds with five sections:

- **Verdict** - ship as-is / ship with edits / don't ship yet
- **Red flags** - each problem named, with the offending line quoted
- **Stronger rewrite** - the full revised text, ready to paste
- **Why this works** - the specific swaps, so the lesson transfers
- **Residual risk** - how the rewrite could still be read badly, so the call is yours

## Install

### Claude apps (Claude.ai / Desktop) - easiest

Upload the packaged skill file:

1. Download [`maybe-dont-post-that.skill`](maybe-dont-post-that.skill).
2. In Claude, go to **Settings → Capabilities → Skills** (location varies by plan) and upload the `.skill` file.

### Claude Code (CLI)

Drop the skill folder into your personal skills directory:

```bash
git clone https://github.com/shaysega/maybe-dont-post-that.git
mkdir -p ~/.claude/skills/maybe-dont-post-that
cp maybe-dont-post-that/SKILL.md ~/.claude/skills/maybe-dont-post-that/SKILL.md
```

It loads automatically the next time you start Claude Code. Verify with `/skill` (or by asking Claude to review a draft post).

## How it triggers

You don't have to invoke it by name. It fires when you're about to publish something public and say things like "review this post," "make this sound right," "punch this up," or even just "is this fine to post?" - and also *after* a post blows up, to decide whether to clarify, correct, or stay quiet.

## Files in this repo

| File | What it is |
|------|------------|
| [`SKILL.md`](SKILL.md) | The skill itself - human-readable source. This is the thing to edit. |
| [`maybe-dont-post-that.skill`](maybe-dont-post-that.skill) | The packaged bundle (a zip of `SKILL.md`) for one-click upload to Claude apps. Regenerate it after editing `SKILL.md`. |

To repackage after editing:

```bash
mkdir -p .pkg/maybe-dont-post-that && cp SKILL.md .pkg/maybe-dont-post-that/
( cd .pkg && zip -r ../maybe-dont-post-that.skill maybe-dont-post-that ) && rm -rf .pkg
```

## License

MIT - see [`LICENSE`](LICENSE).
