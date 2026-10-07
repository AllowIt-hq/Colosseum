# Human-facing report policy

Keep all evidence and validation records in private project run artifacts. Do not add evidence pages or sections to reports unless the owner explicitly requests them. Do not publish provider errors, HTTP failures, retries or temporary service conditions. Permanent reports contain implementation facts and the latest relevant completed execution. Remove generic disclaimers and debugging commentary. Do not link private project records from public reports.

# Colosseum report instructions

## Check the template before every report edit

Read the [original Colosseum template](https://github.com/Marakaya/colosseum_example/tree/315695b07dbf4c2fff3c0144a31c9153ddc0fdce) before editing submission content. Open the corresponding original file. Preserve its file purpose, section order and content placement. Use current AllowIt facts.

The [original README](https://github.com/Marakaya/colosseum_example/blob/315695b07dbf4c2fff3c0144a31c9153ddc0fdce/README.md) places the team table directly under the submission heading. Keep it after the demo area and before Problem and Solution. Preserve the section dividers. Keep pending event information in the [completion guide](docs/completion-guide.md).

Use only the template's architecture, product, API and roadmap report files. Do not add evidence.md or other report pages outside the template. Keep detailed validation in private artifacts. Keep the template's file purposes. Adapt product-specific headings without copying BBM claims. Follow the [completion guide](docs/completion-guide.md) and [contribution instructions](CONTRIBUTING.md).

## Owner-supplied team text

Alex Astrum: `tech, vision and SI alignment`. Contacts: [GitHub](https://github.com/alexastrum) and [Writing](https://hi.astrum.name).
Max: `BD, marketing and operations`.
Igor Stolyarov: `software engineering (front-end)`.
Mukhammedali Beriktassuly: `software engineering (smart contracts)`.

Preserve these names and role strings. Max's GitHub account is [mks044](https://github.com/mks044).

## Source and validation

Source dependencies are pinned in [repos/](repos/README.md). Update source inside its own repository before changing a gitlink. Preserve current implementation, recorded evidence and planned work as separate states.

Check template order, relative links, exact team roles and the diff before committing. Keep credentials and private signing material out of reports. Documentation changes do not deploy applications.

## Technical writing

Always use the [asd-ste100 skill](https://github.com/ackrate/ackrate-project/blob/main/.agents/skills/asd-ste100/SKILL.md) for technical writing. Use short sentences, active voice and consistent terms. Preserve facts, conditions, uncertainty and scope.

Write reports for humans. Keep each section concise. Describe existing implementation or specific planned behavior and data. Remove filler labels, generic disclaimers, excuses, repeated context and irrelevant links. Keep qualifications that define actual implementation limits. Omit “public” from repository link labels.

## Official voice

Use [allowit.xyz](https://allowit.xyz) as the source for the slogan and product narrative. Preserve the slogan: `Go on. On your terms.` Preserve the hero description: `AllowIt lets your AI agents spend and invest, within a policy you set.` Do not invent slogans.

Start with the owner's job and policy. Explain how the agent acts within the policy, asks about unclear requests and stops when the owner revokes authority. Keep website examples distinct from implemented features. Use Claude Opus 5.5 for creative writing, including Problem and Solution and product narratives. Check the returned model before accepting its text. Apply STE100 to technical explanations. Preserve official brand copy.
