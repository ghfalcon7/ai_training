# Security, Privacy, Intellectual Property, and Compliance

AI-assisted development can send company data to external systems and introduce generated material of uncertain provenance. Developers therefore need to answer four questions before using an AI tool:

1. **Is this exact tool, account, model, and feature approved?**
2. **Am I allowed to send all the data the tool will receive?**
3. **Am I allowed to use and distribute the generated output?**
4. **Does this use affect people or enter a regulated product or process?**

This is general engineering guidance, not legal advice. Follow the current approved company policy. The company-policy topic links to [Technical Definition 85](https://sb-conflu.ads.local/spaces/XMS40/pages/682758023/Draft+of+new+TD+-+85+-+Using+GenAI+Assistants+in+Software+Development_MSU); verify its current approval status and version internally.

Detailed prompt injection, secrets management, tool permissions, generated-code security, secure automation, incident response, and governance are covered in later modules.

## Know what leaves your machine

The visible prompt may not be the complete request. Depending on the product and feature, a coding assistant may also send:

- surrounding code and open files;
- repository data and instructions;
- chat history and uploaded files;
- retrieved documents and tool results;
- identifiers, telemetry, and feedback.

Adding web search, another model, a connector, plug-in, or MCP server can add new recipients. Treat each feature as a separate data flow rather than assuming that approval of the product name covers everything.

"Not used for training" does not mean "not stored or processed." Prompts and outputs may still appear in chat history, abuse-monitoring systems, audit logs, telemetry, feedback, support records, caches, or connected services. Retention and processing can vary by product, plan, endpoint, region, feature, configuration, and contract.

## Protect company and personal data

Apply the organization's existing data-classification rules before transmission. Source code may contain personal data, customer material, trade secrets, credentials, security architecture, contract-restricted information, or legally privileged content.

Subject to company policy, use this conservative baseline:

| Data | Default action |
|---|---|
| Public | Use only in an approved tool and use case. |
| Internal | Use only through the approved organizational account. |
| Confidential | Minimize it and confirm that the approved deployment and contract cover it. |
| Restricted or regulated | Do not submit without explicit approval from the relevant owner. |
| Credentials or live secrets | Never intentionally submit. Report accidental exposure immediately. |

Before prompting:

- provide only the smallest relevant fragment;
- replace real names, identifiers, and records with synthetic values where possible;
- remove unrelated files, secrets, customer data, and proprietary context;
- prefer a minimal reproduction over an entire ticket, repository, log, or database export.

Redacted, pseudonymized, aggregated, or synthetic data is not automatically anonymous if a person can still be identified or the data can be linked back to real records.

If personal data is involved, the organization must have a defined purpose, lawful basis, appropriate processor terms, retention period, security controls, transparency, and a way to honor data-subject rights. A Data Protection Impact Assessment may be required for likely high-risk uses such as large-scale monitoring, sensitive data, profiling, or consequential decisions. Escalate these uses to Privacy or Legal before implementation.

If restricted data is accidentally sent, stop further use and report it through the normal security/privacy incident process. Deleting the conversation does not prove that logs, feedback copies, subprocessors, or provider records were deleted.

## Protect intellectual property

Separate three questions that are often confused:

1. **Input authority:** Are we permitted to disclose and process the supplied code, data, document, or image?
2. **Output ownership:** Is the generated result protectable, and who owns any rights?
3. **Freedom to use:** Could using or distributing it infringe copyright, a license, a patent, a trademark, a trade secret, or a contract?

A vendor assigning output rights does not guarantee that the output is copyrightable or free of third-party rights.

### Inputs

Do not submit company, customer, open-source, or third-party material unless its ownership, license, confidentiality terms, and permitted recipients allow it. A promise not to train on the material does not create permission to disclose it.

Trade-secret protection depends partly on reasonable measures to preserve secrecy. Sending confidential code to an unapproved service can breach contractual duties and weaken trade-secret protection.

### Generated output

Treat generated code as having **unknown provenance**. Investigate output that contains:

- a license or copyright notice;
- distinctive comments, names, strings, or test data;
- a long block closely resembling a known project;
- a public-code match or citation reported by the tool.

AI does not remove an upstream open-source license. If generated output incorporates protected licensed code, obligations such as attribution, notices, source availability, or copyleft may still apply. "Permissive" does not mean "no obligations," and there is no universal safe number of matching lines.

When provenance is suspicious:

1. Do not merge the output.
2. Search distinctive fragments and inspect the original repository and license.
3. Run the organization's normal composition and license checks.
4. Satisfy the obligations, obtain Legal guidance, or independently implement from the requirements without using the suspect text.

Patent and trademark risks are separate. Independently generated code can still practice a patent, and generated product names or logos can still infringe trademarks. Escalate commercially significant or market-facing cases rather than relying on a model answer.

## Recognize compliance triggers

Different requirements come from different sources:

- **Laws and regulations** are binding when their scope applies.
- **Contracts** may impose stricter confidentiality, residency, security, IP, or audit requirements.
- **Company policy** governs internal use.
- **Standards and frameworks** such as NIST AI RMF or ISO/IEC 42001 are generally voluntary unless adopted by contract, regulation, or policy.
