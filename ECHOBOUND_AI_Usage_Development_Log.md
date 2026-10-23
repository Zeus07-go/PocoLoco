# ECHOBOUND — AI Usage & Development Log

**Project:** ECHOBOUND — Two Worlds. One Escape.  
**Project type:** Browser-based two-realm puzzle game  
**Development period:** October 2026  
**Level 1:** Move Mimic  
**Level 2:** Move Mirror  
**Primary development constraint:** Build a compelling playable prototype within a short hackathon window.

---

## 1. Project Overview

ECHOBOUND is a puzzle game built around a simple idea: **one player's movement has consequences in two different worlds.**

The player navigates a grid in Reality while a shadow counterpart moves in Reflection. The two realms share a coordinate system but contain different obstacles, traps, and collectible power-ups. A movement that is safe in one realm may put the shadow in danger in the other.

The player must therefore think beyond the character they directly see. Every move needs to be considered in terms of both worlds.

The current design divides the experience into two levels with distinct mechanics:

- **Level 1 — Move Mimic:** The shadow copies the player's movement. The challenge is predicting the consequences of a shared movement sequence across two different maps.
- **Level 2 — Move Mirror:** A teammate is developing a separate mirror-based mechanic, intended to introduce a different puzzle-solving challenge.

The intention is to make the player feel clever when they discover a route that satisfies both realms' constraints.

## 2. How the Idea Developed

### Stage 1 — Finding a suitable game concept

The initial objective was to find a game concept that could be implemented in a browser during a short hackathon, with four teammates working in parallel.

The concept needed to be understandable quickly, visually demonstrable, and mechanically interesting enough to stand out from a conventional maze.

The early direction was a time-echo puzzle: a shadow would repeat the player's previous movements, turning past actions into an additional challenge.

**Design question:** How can a simple movement mechanic create a genuinely difficult puzzle?

### Stage 2 — Establishing the two realms

The concept evolved into two coordinate-aligned realms:

- **Reality:** The player's realm.
- **Reflection:** The shadow's realm.

The player and shadow share movement inputs, but the environments differ. The same directional input must be evaluated against both maps.

This created the core design constraint: the player cannot solve the puzzle by considering only one character.

### Stage 3 — Introducing meaningful power-ups

Two power-ups were selected:

1. **Jump:** Allows the player and shadow to cross a designated gap.
2. **Shield / Mine Immunity:** Protects against one landmine.

The power-ups were intended to be located in different realms. The player must collect both and use them at the correct points in the route.

The design also specifies automatic power-up consumption when the matching hazard is encountered, regardless of which realm is currently visible.

This reduces control complexity while preserving the strategic challenge.

### Stage 4 — Constraining the puzzle to a 6×6 grid

A 6×6 grid was chosen so the puzzle would be compact enough to implement and test quickly.

The challenge was to fit the following into a small space:

- A meaningful route with several turns.
- Different obstacles in both realms.
- A gap and a landmine.
- Two realm-specific power-ups.
- A shared movement sequence that works in both worlds.
- A clear exit and a satisfying completion state.

The grid constraint makes every tile important. Walls cannot be placed randomly; they must shape the route and make the player's choices meaningful.

### Stage 5 — Reconsidering realm switching

The first version included limited realm switching. The player could inspect one realm, switch to the other, and use a limited number of switches to reveal hidden information.

However, this introduced a design problem: switching could feel like an unnecessary restriction rather than an enjoyable mechanic.

The design was reconsidered, and the current direction is to show both realms at once.

This change shifts the difficulty away from memorizing hidden information and toward understanding how a single movement affects two different environments.

**Lesson:** A mechanic should exist because it creates interesting decisions, not simply because it makes the game harder.

### Stage 6 — Separating the two levels

The project was divided into two distinct level mechanics:

- Level 1 uses **Move Mimic**.
- Level 2 uses **Move Mirror**.

The intention is to make the second level introduce a new way of thinking rather than simply repeating the first level with a different map.

This gives the game a clearer progression: first, learn to anticipate the consequences of shared movement; then, apply a different spatial reasoning mechanic.

## 3. Current Gameplay Specification

### Level 1 — Move Mimic

**Objective:** Collect both required power-ups, navigate the hazards in Reality and Reflection, and reach the exit.

#### Map rules

- Both realms use a 6×6 grid.
- Each tile has a row and column coordinate.
- Both characters begin at their designated starting positions.
- The shadow follows the player's movement.
- Walls in either realm block the shared move.
- The two realms can contain different hazards and pickups.

#### Power-up rules

**Jump**
- Collected from a designated tile in Reality.
- Enables one designated gap crossing.
- Automatically consumed when the gap is encountered.

**Shield**
- Collected from a designated tile in Reflection.
- Protects against one landmine.
- Automatically consumed when a landmine is encountered.

The intended design uses a shared inventory, so the power-up can protect the characters even when the corresponding realm is not the currently focused realm.

#### Win condition

Both characters must reach the required exit positions without an unprotected hazard collision.

#### Failure and recovery

A failed route should give clear feedback. The player should be able to restart quickly and, if implemented, undo a previous move to experiment with another strategy.

**Implementation status:** These are the intended rules. The final maps, route validity, power-up ordering, and collision behavior must be tested in the actual game before being described as fully verified.

## 4. AI Tools and Their Intended Roles

The project creator reported using or considering the following tools:

- ChatGPT
- Claude
- LM Arena
- Replit
- ElevenLabs
- Kiro
- Antigravity
- Codex
- Gemini

The following table describes how these tools can contribute to the workflow. Only the ChatGPT activity described in this log is directly supported by the conversation record available for this document.

| AI tool | Best-fit role | Evidence to attach |
|---|---|---|
| ChatGPT | Brainstorming mechanics, refining level rules, drafting implementation prompts, documenting the design. | Conversation screenshots or exported chat. |
| Claude | Alternative design critique, code review, identifying edge cases. | Actual prompt and response used. |
| LM Arena | Comparing responses from different models to evaluate alternative ideas. | Models compared and relevant outputs. |
| Replit | Browser-based implementation, running a web prototype, and sharing it. | Project URL, screenshots, or version history. |
| ElevenLabs | Creating audio feedback, sound effects, voice lines, or ambience. | Audio files and generation history. |
| Kiro | Coding assistance, task breakdown, implementation planning, and code refinement. | Project changes or prompt history. |
| Antigravity | Implementing the game from a detailed specification, testing the mechanics, and iterating on the code. | Prompt, project files, and a playable build. |
| Codex | Code generation, debugging, logic review, and potentially automated route validation. | Code changes, prompts, or test output. |
| Gemini | Alternative reasoning, visual exploration, code assistance, or design feedback. | Relevant conversations, generated assets, or files. |

The table should be treated as a workflow map, not proof that every tool completed every listed task. The final report should name the specific contribution of each tool only where supporting evidence exists.

## 5. ChatGPT Prompt and Iteration Log

The following entries summarize the design work recorded in the ChatGPT conversation.

### Entry 1 — Selecting the game direction

**Purpose:** Identify a concept suitable for a short hackathon.

**Prompt summary:** Explore the hackathon problem statement and choose an idea that can be implemented by a four-person team within approximately two hours.

**Result:** A browser-based puzzle game became the chosen direction.

### Entry 2 — Defining the shadow mechanic

**Purpose:** Create a distinctive core mechanic.

**Prompt summary:** Develop the concept in which the player's past movements are repeated by a shadow, forcing the player to plan ahead.

**Result:** The concept evolved into ECHOBOUND, with the shadow serving as an additional movement constraint.

### Entry 3 — Designing Level 1

**Purpose:** Create a harder, more meaningful puzzle for the first level.

**Prompt summary:** The creator explained that a teammate was building Level 2 while they were responsible for Level 1. They wanted two realms, obstacles, limited realm switching, and two power-ups.

**Result:** The first level was structured around Reality, Reflection, synchronized movement, and realm-specific hazards.

### Entry 4 — Defining the power-ups

**Purpose:** Make route planning depend on collecting useful resources.

**Prompt summary:** The creator specified two power-ups: one to jump across a gap and another to provide immunity against a landmine.

**Result:** Jump and Shield became distinct resources associated with different hazards.

### Entry 5 — Limiting the grid size

**Original prompt:**

> make me the puzzle first , one i can build with 6*6 grid

**Purpose:** Make the level practical to construct and code.

**Result:** The puzzle was constrained to a 6×6 grid.

### Entry 6 — Requiring a route across both realms

**Prompt summary:** The creator requested one path that includes obstacles in both realms and requires collecting one power-up in each. Power-ups should be used automatically when their matching hazards are reached. The route should be long enough to feel engaging and presented in a readable format for later implementation.

**Purpose:** Move from a loose concept to a specific, implementable puzzle.

**Result:** The design requirements became more concrete: a shared route, two mandatory pickups, and hazards that require the correct resources.

### Entry 7 — Drafting the Antigravity implementation prompt

**Purpose:** Translate the game concept into a development specification.

A detailed prompt was prepared asking Antigravity to implement:

- Two coordinate-aligned 6×6 maps.
- Synchronized player and shadow movement.
- Realm-specific hazards and power-ups.
- Jump and Shield inventory.
- Automatic power-up consumption.
- Realm-switching behavior for the earlier version.
- A route-validation algorithm.
- A readable solution path.
- Victory, failure, and restart behavior.
- A polished browser interface.

The prompt explicitly instructed the implementation to prioritize puzzle correctness before visual polish.

**Evidence required:** The Antigravity prompt and the actual output or project files should be attached before claiming the complete game was implemented or validated.

### Entry 8 — Questioning the value of switching

**Original prompt:**

> what will give incentive for player to switch

**Purpose:** Ensure that realm switching serves a real gameplay purpose.

**Result:** The design discussion identified realm-specific collectibles as one possible reason to switch, rather than treating switching only as a way to reveal information.

### Entry 9 — Simplifying the mechanic and differentiating the levels

**Original prompt, spelling normalized:**

> fine forget switch cause its impractical , suppose u can c both relms at one time , level 2 move mirror , level 1 move mimic how can we make it interesting , exciting for the user to actuually get hooked use real games inspo to help ppleaseeeee fastt

**Purpose:** Make the game more intuitive and improve player engagement.

**Result:** The current direction removes limited switching and keeps both realms visible. Level 1 becomes Move Mimic, while Level 2 uses the separate Move Mirror mechanic.

The design discussion considered general puzzle-design lessons associated with games such as *Braid*, *Portal 2*, and *Baba Is You*: simple rules, meaningful interactions, and satisfying moments of discovery. These were sources of inspiration, not claims that their code or assets were used.

### Entry 10 — Improving the player experience

**Purpose:** Make the game more engaging than a conventional maze.

The proposed improvements included:

- Showing a fading trail of the shadow's previous positions.
- Providing clear visual and audio feedback when power-ups are collected or consumed.
- Adding an undo option to encourage experimentation.
- Rewarding efficient solutions.
- Using a brief near-miss effect when the shadow approaches a hazard.

These are design recommendations. They should be marked as implemented only after they appear in the playable build.

## 6. How the AI tools fit into the development process

The workflow is most effective when each tool has a clearly defined job.

### A. Ideation and design

Use conversational models to generate mechanics, challenge weak assumptions, compare alternative designs, and identify confusing rules.

The important human contribution is selecting which ideas to keep, rejecting unnecessary complexity, and deciding how the levels should differ.

### B. Implementation

Use coding assistants to turn the selected design into a working game. Keep the maps separate from movement and collision logic so that puzzle layouts can be changed without rewriting the whole game.

### C. Validation

Use code and actual playtesting to verify the puzzle. The route must be tested against both realms, including every wall, gap, mine, pickup, and exit.

A generated explanation that says a route works is not sufficient evidence that it actually works.

### D. Visual and audio polish

Use appropriate creative tools to explore the visual style and create assets or audio when needed. Check asset licensing and ensure the effects help players recognize hazards and actions rather than obscuring the board.

### E. Integration

The final game should run reliably on the presentation machine. Keep Level 1 and Level 2 modular so the team can integrate them without breaking each other's work.

## 7. What Makes ECHOBOUND Interesting

ECHOBOUND's design goal is to make a small board produce a meaningful reasoning challenge.

The main elements are:

1. **Dual-world movement:** One action affects two environments.
2. **Conflicting layouts:** A safe route in one realm may be dangerous in the other.
3. **Resource planning:** Jump and Shield each solve a specific obstacle.
4. **Consequential decisions:** The player must consider both characters before moving.
5. **Distinct level mechanics:** Move Mimic and Move Mirror are intended to offer different experiences.
6. **Fast experimentation:** Clear feedback and quick retries help players learn the puzzle.
7. **A compact scope:** The 6×6 grid makes the game practical to prototype during a short hackathon.

The key design principle is that **difficulty should come from reasoning about the rules, not from confusing controls or arbitrary punishment**.

## 8. Verification and Evidence Checklist

Before presenting this as the final development log, collect:

- [ ] The actual prompts used in Claude.
- [ ] The actual models and prompts used in LM Arena.
- [ ] The Replit project URL or relevant files, if used.
- [ ] ElevenLabs audio files or generation records, if used.
- [ ] Kiro prompts or code changes, if used.
- [ ] The Antigravity prompt and resulting implementation.
- [ ] Codex prompts, code changes, or test results, if used.
- [ ] Gemini prompts and relevant outputs, if used.
- [ ] The final Reality and Reflection maps.
- [ ] The verified solution route and its validation results.
- [ ] A screenshot or recording of the playable game.
- [ ] Evidence that pickups, hazards, restart, and victory work.
- [ ] Attribution and licensing details for external or generated assets.
- [ ] A short record of design decisions made by the team.

## 9. Final Project Summary

ECHOBOUND is a two-realm puzzle-game concept in which the player's movement affects both their character and a shadow counterpart. Reality and Reflection contain different hazards and pickups, so the player must find a route that works across both environments.

The first level, Move Mimic, focuses on predicting the consequences of shared movement and planning around the two realms. The second level, Move Mirror, is being developed separately with a distinct mechanic.

AI tools supported the ideation and specification process, while the final record should document each tool's actual contribution with prompts, files, screenshots, and test results. The project's defining goal is to turn a small 6×6 grid into a satisfying puzzle where players discover a clever route through two connected worlds.
