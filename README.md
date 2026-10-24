# Data Export Completeness Gate

DataExportCompletenessGate stores a requester's required data categories before export submission. The designated provider submits a public manifest, and validators independently assess which categories are affirmatively evidenced as delivered. The contract records COMPLETE, PARTIAL, or NEEDS_REVIEW and allows revision submissions without changing the original requirements. It evaluates documentary completeness, not the contents of private files.

## Repository

- Repository name: `data-export-completeness-gate-genlayer`
- Description: Reviews delivered export manifests against pre-committed data categories.
- Contract file: `data_export_completeness_gate.py`
- Runner dependency: pinned `py-genlayer:1jb45aa8ynh2a9c9xn3b7qqh8sm5q93hwfp7jqmwsfhh8jpz09h6`

## Intended workflow

See the public methods and state transitions in `data_export_completeness_gate.py`. The contract uses independent leader/validator execution for web evidence and writes persistent state only after the consensus call returns.

## Validation before deployment

Run from the repository root:

```bash
genvm-lint check data_export_completeness_gate.py
genvm-lint schema data_export_completeness_gate.py
pytest tests/direct/ -v
# Then run the configured integration tests against the target GenLayer environment.
```

Static syntax checks are not a substitute for GenVM lint, schema validation, or consensus integration tests.

## Scope and limitations

This contract evaluates the evidence submitted through its public interface. It does not guarantee the truth of an off-chain source, replace legal/professional review, or make an external system perform an action unless an integration is explicitly implemented.
