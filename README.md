# Spin A Yarn 🧶

A browser-based dialogue tree editor and player. Write a branching script, watch it become a graph, then click through it like a player would.

No install. No build step. One HTML file.

**[Live demo](https://spin-a-yarn.vercel.app)**

---

## What it is

I built this because I kept sketching dialogue trees on paper while thinking about narrative games, and paper is terrible for this. Boxes, arrows, crossing lines, running out of space. There had to be a better way that wasn't a full-blown tool requiring an account and a tutorial.

So: you write a simple script in a little syntax I made up, hit Run, and it draws the tree for you. Then you can flip to Play mode and actually walk through it as a player, making choices, following branches, seeing where they lead. It's good for prototyping interactive fiction, planning dialogue for games, or just messing around with branching stories.

The built-in example is a short spy thriller with 9 endings. Some of them are pretty bleak.

---

## Features

- **Graph view** — auto-lays out your whole dialogue tree as a node graph, with amber edges for player choices and green edges for auto-continues. Loops and back-edges are drawn as dashed curves. Broken links get flagged right on the card.
- **Play view** — click through your story exactly as a player would. Full transcript, numbered choices, keyboard shortcuts (press 1-9 to pick options), restart button at the end.
- **Focus mode** — in Play view, hit "focus mode" to collapse the editor and go full-width. Good for actually reading without distraction.
- **6 themes** — Osaka Jade, Tokyo Night, Amber Terminal, Blood Moon, Paper, Deep Ocean. Pick one with the coloured dots in the header.
- **File in / file out** — open any `.txt` or `.dlg` file, save your script back out. Works entirely client-side.
- **Warnings** — duplicate nodes, undefined link targets, and unreachable nodes all get surfaced automatically.
- **CRT aesthetic** — subtle scanlines, phosphor glow, Space Mono and JetBrains Mono. Looks great on a dark monitor at 2am, which is when you'll probably be using it.

---

## Syntax

It's deliberately minimal. Six things to learn:

```
:: node-name          starts a new node
Speaker: text         a line of dialogue
just text             narration (no speaker)
+ [Choice text] -> target    a player choice leading to another node
-> target             auto-continues to the next node (no choice shown)
-> end                ends the conversation
```

A full example:

```
:: start
Guard: Halt. Who goes there?
+ [Tell the truth] -> truth
+ [Run for it] -> run

:: truth
You: Just a traveler.
Guard: Move along then.
-> end

:: run
You bolt into the alley. The guard shouts behind you.
-> end
```

Nodes are case-insensitive for link targets, so `-> Start` and `-> start` both work. Speaker names are detected automatically if the word before the colon is 30 characters or fewer with no special characters, so normal narration sentences with colons are handled correctly.

---

## Tech

- Vanilla JS, no framework
- HTML/CSS/JS in a single file
- Space Mono + JetBrains Mono via Google Fonts
- Deployed on Vercel as a static site

---

## Running locally

Download `index.html` and open it in a browser. Done.

Or clone and serve it:

```bash
git clone https://github.com/vijithvaratharajan/spin-a-yarn.git
cd spin-a-yarn
npx serve .
```

---

## License

MIT

## Author

Vijith Varatharajan
[ORCID: 0009-0007-8713-1343](https://orcid.org/0009-0007-8713-1343)
