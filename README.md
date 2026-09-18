# Output quality engineering for coding agents

An agent writes the code. Something has to decide whether it ships.

That decision used to be a person reading a diff. It does not scale, and not because
reviewers are careless — reviewers find defects at a roughly **fixed rate**, so a change
twice the size gets the same attention, not twice as much. Once an agent is producing the
changes, the reading is the bottleneck and nothing in the prompt fixes it.

This repo collects essays on the other half of the problem: **engineering the quality of
what comes out.** Four parts, and the last two are where most of the interesting work is:

1. **Context on the way in** — engineer the spec and the context so fewer defects are
   produced in the first place. This half is largely solved and well written up elsewhere;
   the essays here credit it and build on it rather than re-teaching it.
2. **Instruments on the way out** — inspection that a machine performs on every change, at
   machine speed, instead of a human performing it on a sample of changes at human speed.
   The human's rate is a constant; the machine's is a budget you can spend.
3. **Instruments proven to discriminate** — an instrument that returns the same verdict
   whatever you feed it is not measuring anything. Most of the failures documented here are
   of this kind: a check that reported a present thing as absent, and a step that produced
   findings at a 100% false-positive rate until it was removed by measurement.
4. **A human who still understands the system — at the speed it now changes.** Instrumenting
   the inspection does not remove the human. It **moves the bottleneck**. Defect-finding goes
   to the machine, which is better at it; understanding stays human, and it is still paid for
   at human rate while the codebase is now changed at machine rate. So the human's attention
   is redeployed rather than saved: away from hunting defects line by line, and onto intent,
   risk, and whether the change that arrived is the change that was designed.

   This is the leg that does not scale, and it is the honest limit of everything above.
   Comprehension also **decays silently** — nothing tells you that you have stopped
   understanding your own system, which is exactly why it needs an instrument of its own, and
   why not having built one yet is worth saying out loud rather than hiding.

## Essays

| Essay | What it argues |
|---|---|
| [**The Bottleneck Moves**](./bottleneck-moves.md) | *in progress* — reviewing at a fixed rate was always the constraint; instrumenting it does not remove the constraint, it promotes the next one. What that next one is, and what is left for you. |

## Evidence

Numbers in these essays are real and stated with their limits. Where a figure comes from one
run, it says so. Where work was done on a client's repository, the repository is described
and never named. Where a claim is widely circulated but not supported by its own primary
source, it is not used — several well-known figures about AI code quality do not survive
contact with the study they are attributed to, and the essays say which.

## Licence

- **Prose** — [CC BY 4.0](./LICENSE). Quote it, translate it, republish it, with attribution.
- **Code snippets** — MIT. Copy them into anything, no attribution required.
