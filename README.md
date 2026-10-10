# audit-anything

Run a structured, evidence-first audit in almost any domain by pairing with the relevant skill. It is designed for explicit audit requests, not ordinary implementation work.

## What it does

`audit-anything` provides the shared audit discipline:

- frames the target and scope;
- chooses a narrow audit mode;
- pairs with a domain-specific skill when available;
- gathers evidence before judging;
- separates findings from speculation;
- assigns a clear verdict;
- persists a complete report when requested.

It is intentionally not a code-review shortcut. It is for broader assessments where coverage, evidence, and traceability matter.

## When to use it

Use this skill when the user asks for:

- an audit;
- a domain assessment;
- a design review;
- an architecture review;
- a contract or schema audit;
- a live product review;
- a persisted report rather than quick inline comments.

Do not use it for ordinary implementation, feature work, or a narrow code-review-only request.

## Installation

Copy this folder into:

```text
~/.codex/skills/audit-anything
```

No additional dependencies are required. The skill works best when other domain skills are also installed, such as frontend, UX, architecture, database, information architecture, user flow, or AI workflow skills.

## How pairing works

The audit skill owns process and evidence. The paired skill supplies domain knowledge.

```text
audit-anything        -> scope, evidence, verdict, report
frontend-design       -> visual and interaction criteria
database designer     -> schema and integrity criteria
architecture skill    -> boundaries and coupling criteria
```

If no domain skill is named, the skill infers the most likely domain from the request. If the domain is genuinely ambiguous, it asks one concise question before proceeding.

## Audit modes

| Mode | Typical target |
|---|---|
| Change audit | diff, commit, or pull request |
| Module audit | file, component, service, or workflow |
| System audit | architecture or domain model |
| Live product audit | running app or website |
| Contract audit | API, schema, event, or data model |
| Document audit | plan, specification, report, or flow |

It selects the narrowest mode that satisfies the request.

## Evidence discipline

A finding must be supported by concrete evidence, such as:

- file and line references;
- command output;
- request or response data;
- screenshots;
- schema definitions;
- quotes from the audited artifact.

Speculative concerns, unrelated pre-existing issues, and style-only preferences are not reported as findings.

## Verdicts

The skill uses one of four verdicts:

- `Pass`
- `Conditional Pass`
- `Fail`
- `Incomplete`

`Incomplete` is used when required access, running state, credentials, tests, or evidence is missing.

## Report output

Unless the user asks for chat-only output, the skill writes a full report to:

```text
docs/audits/YYYY-MM-DD-<domain>-<target>.md
```

If there is no `docs/` directory, it saves the report to the OS temp directory and returns the absolute path.

Reports include:

- scope;
- pairing;
- audit mode;
- verdict;
- findings with evidence and next change;
- coverage;
- what was not verified.

## Safety

The audit is read-only by default. It does not refactor, install dependencies, mutate files, or call external services unless the user explicitly asks for that work.

## Limitations

- It is not a substitute for domain expertise when no paired domain skill is available.
- It cannot verify runtime behavior without access to a running product.
- It will not fabricate coverage that was not actually checked.

## License

MIT.
