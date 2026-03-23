# Repertoire

Declarative specs for the [Orchestrator](https://github.com/AngryTux/orchestrator). Pure YAML. No code required to contribute.

## Structure

```
providers/       Who plays — provider CLI definitions
  claude.yaml

formations/      How they play — execution patterns
  solo.yaml      1 workspace
  duet.yaml      2 workspaces in parallel + consolidation

isolation/       Security constraints
  open.yaml      Minimal isolation (experimentation)
  sandbox.yaml   Standard isolation (daily use)
  strict.yaml    Maximum isolation (sensitive workloads)

integrations/    LLM role prompts (coming soon)
  arranger.yaml  Intent classification
  maestro.yaml   Composition + consolidation

spec/            JSON Schemas for validation (coming soon)
```

## Contributing a provider

Create a YAML file in `providers/`:

```yaml
kind: Provider
version: 1
metadata:
  name: your-provider
  display_name: "Your Provider"
detection:
  binary: your-cli
  version_cmd: ["your-cli", "--version"]
invocation:
  cmd: ["your-cli"]
  prompt_flag: "-p"
auth:
  env_var: "YOUR_API_KEY"
  methods: [env]
```

The daemon reads these specs to know how to invoke each provider. No Rust code needed.

## License

MIT
