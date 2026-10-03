# Architecture Katas

My solutions to architecture katas: short design exercises for practicing software architecture.

Architects only design a handful of systems from scratch in their whole career. Katas are a way to practice more often: you get a short brief (a client, users, requirements and business context), a fixed amount of time, and you design an architecture for it. The point isn't a "correct" answer. It's the reasoning: which questions you ask, which trade-offs you accept, and how you explain them.

The kata format was created by **Ted Neward**. The original briefs are collected on [Neal Ford's Architectural Katas page](https://nealford.com/katas/).

## Katas

| # | Kata | What it's about | Status |
| --- | --- | --- | --- |
| 01 | [Lights, Please](katas/01-lights-please/) | Home automation: modular devices, a protocol to design, remote access | In progress |

## How each kata is structured

Every kata has its own folder with the same structure, so they're easy to compare:

1. **The brief:** a short summary of the problem, with a link to the original.
2. **Questions for the client:** what I'd ask before designing, and the assumptions I made when there was no one to ask.
3. **Architecture characteristics:** the top three "-ilities" that drive the design, and why those three.
4. **Components:** the main building blocks and their responsibilities.
5. **Architecture style:** the overall style and why it fits.
6. **Diagrams:** C4 context and container diagrams, in [Mermaid](https://mermaid.js.org/) so they render directly on GitHub.
7. **Decisions:** the important choices, each written up as an [ADR](templates/adr-template.md) (architecture decision record) with the alternatives and trade-offs.
8. **Risks and trade-offs:** what could go wrong, and what I deliberately gave up.
9. **With more time:** what I'd explore next.

Each kata is timeboxed to 2–3 hours of design work, like the original format.

## Templates

- [Kata template](templates/kata-template.md): copy it to start a new kata.
- [ADR template](templates/adr-template.md): based on Michael Nygard's format.

## License

The text and diagrams in this repository are licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The kata briefs belong to their original authors and are summarized here with links to the source.
