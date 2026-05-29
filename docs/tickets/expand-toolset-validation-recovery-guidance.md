# Expand toolset skill guidance for validation recovery metadata

## Background

The reusable toolset surface is used by host apps and agents that need to recover from validation failures without parsing prose. The current `tool-surface-spec` skill mentions preserving validation/error recovery metadata, but it should make the expected shape and review questions explicit.

This is not specific to one package. Darty, KASB, Landprice, future MCP adapters, server hosts such as `creo-web`, and CLI wrappers all benefit when validation failures carry both human-readable guidance and machine-readable next actions.

## Scope

Update `skills/tool-surface-spec/SKILL.md` and referenced checklist/spec docs as needed to define validation recovery metadata for neutral toolsets.

Cover at least:

- human-facing recovery copy, e.g. `recoveryHint`;
- machine-readable recovery action, e.g. `inspect_tool_help` or `inspect_command_help`;
- command or operation name for command-scoped recovery;
- failed parameter, reason, expected shape, actual value when safe, and example input;
- a clear distinction between same-input retryability and input-repair recoverability.

Suggested neutral shape:

```ts
type ValidationRecoveryAction =
  | { kind: "inspect_tool_help" }
  | { kind: "inspect_command_help"; operationName: string };

type ValidationFailure = {
  code: "missing_parameter" | "invalid_parameter" | "unknown_parameter" | "invalid_request";
  message: string;
  operationName?: string;
  parameter?: string;
  reason?: string;
  expected?: string;
  actual?: unknown;
  exampleInput?: Record<string, unknown>;
  recoveryHint?: string;
  recoveryAction?: ValidationRecoveryAction;
  recoverable: boolean;
  retryable?: boolean;
};
```

`recoverable` should mean "a caller can repair the input by following the recovery metadata." `retryable` should be reserved for "the same request might succeed later" or documented as a compatibility alias when an existing package already uses that name for repairable validation failures.

## Acceptance criteria

- The skill tells agents to check that `validateInput()` returns structured recovery metadata for known validation failures.
- The skill warns against requiring hosts to parse localized prose or CLI help text to choose a recovery path.
- The checklist includes unknown command, non-object input, missing required parameter, invalid identifier, and unknown parameter cases.
- The updated skill/checklist guidance is generic and does not mention Darty, KASB, Landprice, Creo, or `creo-web` except as optional examples if a separate examples section is added.
- Existing CLI + neutral toolset guidance remains intact; no Pi-specific requirement is introduced.
