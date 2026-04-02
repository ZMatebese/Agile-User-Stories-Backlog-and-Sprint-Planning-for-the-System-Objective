# Reflection: Challenges in Agile Planning for the RPL System
## Prioritisation, Estimation, and Aligning Agile with Stakeholder Needs

**Author:** Boniface Kabaso
**Date:** March 2026
**Assignment:** Assignment 6

---

Working through the Agile planning process for the RPL Application System as a solo developer forced me to confront a set of tensions that I had not fully anticipated when reading about Agile methodology in theory. The assignment note was accurate: at this stage I am the only "stakeholder," and the resistance I had to work through was entirely internal — competing impulses about what matters most, what I can realistically achieve, and how honest I was willing to be about my own capacity.

**The Illusion of Clarity in Prioritisation**

The MoSCoW prioritisation exercise seemed straightforward at first glance. Surely it is obvious that a student being able to submit an application is a "Must-have" and that a reporting dashboard for the Registrar is a "Could-have." But when I sat with the full list of user stories, I found myself second-guessing every decision. Is security (AES-256 encryption) a Must-have from day one, or can I defer it to a later sprint and add it before going live? The answer, rationally, is that legal compliance under POPIA cannot be deferred — personal data must be encrypted from the moment it is stored. But there was a part of me that wanted to push it to Sprint 2 because the implementation complexity was intimidating. Recognising that impulse — and overriding it — was a genuine challenge. Good prioritisation is not just a logical exercise; it requires honesty about what you are avoiding and why.

**Story Point Estimation as Structured Guessing**

Effort estimation using story points was the part of this process that felt most like structured guessing. Having never built this specific system before, I had no historical velocity data to anchor my estimates. I used the Fibonacci sequence as instructed, and I found the relative comparison approach helpful — asking "is US-009 (RBAC) harder than US-001 (registration)?" is more tractable than asking "how many hours will RBAC take?" But I am aware that my estimates are optimistic. The 77 hours of tasks I planned for Sprint 1 would be challenging even for an experienced developer working full-time, and I am a student with other commitments. This created an uncomfortable realisation: a sprint plan that looks complete on paper can still be unrealistic in practice. An honest Agile team would have pushed back and reduced scope. Playing all the Scrum roles simultaneously — product owner, scrum master, and developer — made it tempting to approve my own ambitious plan without the pushback that a real team dynamic would provide.

**Breaking Requirements into INVEST-Compliant Stories**

Translating the functional requirements from Assignment 4 into user stories that genuinely follow the INVEST criteria was harder than it appeared. The "Independent" criterion in particular caused difficulties. US-002 (submit application) and US-003 (duplicate prevention) are technically separate stories, but they are so tightly coupled in implementation that building one without the other would produce a broken feature. I kept them as separate stories for traceability and clarity, but I had to acknowledge in the sprint plan that they must be developed together. This is a real tension in Agile: the desire for clean, independent stories sometimes conflicts with the reality of tightly integrated system behaviour.

**Deferring Assessor Features: The Right Call or Avoidance?**

One of the most difficult decisions was deferring the assessor review stories (US-005 and US-006) to Sprint 2. From a purely student-facing perspective, the Sprint 1 MVP makes sense — a student can register, apply, and track their status. But in reality, an RPL system with no assessor workflow is not truly functional. Applications would pile up with no way to process them. I justified the deferral on the grounds that Sprint 1 is an internal development milestone, not a public release, and assessor functionality can follow immediately in Sprint 2. But I sat with the discomfort of that decision for a while, because it represents a real limitation of MVP thinking: the "minimum" in MVP must be carefully defined to avoid delivering something that looks complete but cannot actually fulfil its core purpose.

**Conclusion**

The Agile planning process revealed that the discipline is as much about managing one's own judgment and biases as it is about organising tasks. Without a team to challenge assumptions, the planning process requires a heightened level of self-critical thinking. I came away with a deeper respect for why Scrum distributes these roles across multiple people — the product owner, scrum master, and development team serve as checks on each other's blind spots in ways that a single person simply cannot replicate alone.

---

*Reflection prepared for Assignment 6 — RPL Application System*
*Author: Boniface Kabaso | March 2026*
*(Word count: approximately 660 words)*
