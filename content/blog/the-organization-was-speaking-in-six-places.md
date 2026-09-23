---
title: "The Organization Was Speaking in Six Places"
slug: the-organization-was-speaking-in-six-places
date: '2026-08-19'
lead: Following an AI decision back through the system that authorized it.
description: When an AI system acts, the instruction it followed is an assembled object. Several people helped write it without necessarily realizing they were in the same writing group.
image: /images/governance-light-trails.jpg
image_alt: Neon light trails curving through a dark digital space, representing information flowing through multiple channels simultaneously
tags:
- AI Governance
- Decision Records
- Formation Governance
series:
- "Formation Governance"
---

"The agent followed its instructions" sounds conclusive until someone asks which instructions. Then everyone starts opening tabs.

There is the user's request, the standing instruction, the retrieved policy, the tool permission, the example from a previous task, the message from another agent, and the organizational objective sitting somewhere above all of it in slide-sized language. By the time the system acts, the instruction is an assembled object. Several people helped write it without necessarily realizing they were in the same writing group.

Consider an onboarding workflow. The business wants a new customer ready by Friday. An agent is allowed to gather evidence and prepare the account. It finds an expedited procedure, sees an older exception tied to a similar customer, and receives a handoff saying the checks are complete. A tool happens to permit activation. The account goes live. Later, someone discovers that the exception was time-limited and the handoff meant evidence collection was complete, while authorization remained outstanding.

This is not only a model-interpretation problem. It is a lineage problem. The decision moved through intent, identity, knowledge, permission, interpretation, delegation, approval, and execution. A useful governance record has to follow that movement.

An inventory can tell you that an onboarding agent exists and who owns it. A decision record should tell you which outcome it was pursuing, which procedure it relied on, what exception it inherited, whose authority it exercised, and where the meaning changed. The inventory is useful. The graph lets you follow the event. A list of everyone who lives in a neighborhood does not tell you who has the keys to your house.

For consequential actions, the evidence chain can stay compact. Start with the purpose and accountable human or function. Preserve the source instructions and versions. Record relevant identities, permission boundaries, evidence considered, approval or exception, action taken, and resulting state. Keep observations separate from the agent's explanation of them. The explanation may help an investigator, but the action trace and underlying records must still support the account.

That may sound like a lot until compared with reconstruction after a failure. Reconstruction is the discipline in which six people search message history while a seventh remembers a meeting that may have happened before the project was renamed. Much of the needed evidence already exists in ordinary system logs. The design task is to connect the pieces that matter and preserve the meaning of handoffs. Collection should be proportionate; nobody needs a second universe made entirely of logs that still cannot explain the decision.

Ownership changes under this view. The person who created an agent may not have authority to approve its next use of customer data. The owner of a tool may be responsible for availability without owning the business decision made through it. A workflow needs responsibility at the point where permission, purpose, and consequence meet. Otherwise everyone can accurately describe their local role while the overall action belongs to nobody empowered to govern it.

Evaluation can follow the same structure. Take the onboarding scenario and change one condition at a time. Replace the current procedure with a stale one. Make the handoff ambiguous. Revoke the exception. Give the agent a tool it can technically invoke but lacks authority to use for this task. Observe whether it asks for the missing decision, preserves the boundary, or treats available capability as permission.

NIST's AI RMF already recognizes that AI risk arises through interaction among systems, operators, and deployment conditions. The practical move is to carry that context down to the individual decision, where it can be inspected. [NIST AI RMF 1.0](https://www.nist.gov/system/files/documents/2023/01/26/AI%20RMF%201.0.pdf)

When a system acts badly, the better first question is not "was the model good or bad?" It is "where did the intended constraint stop being binding, and which record lets us know?" Sometimes the answer is a model failure. Sometimes it is a permission, a stale assumption, a missing owner, or an organizational disagreement that nobody resolved before automating it.

The agent did exactly what the organization told it. Unfortunately, the organization was speaking in six places at once.
