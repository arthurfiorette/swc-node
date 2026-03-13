# `@swc-node/cli`

<a href="https://npmcharts.com/compare/@swc-node/cli?minimal=true"><img src="https://img.shields.io/npm/dm/@swc-node/cli.svg?sanitize=true" alt="Downloads" /></a>

`@swc-node/cli` is a tiny Node-first CLI powered by `@swc-node/register`.

## Usage

### CLI

```bash
swc-node index.ts
swc-node --conditions=dev src/index.ts --port=3000
```

### Inline code (`-e` / `-p`)

```bash
swc-node -e "const n: number = 1; console.log(n + 1)"
swc-node -p "const n: number = 41; n + 1"
```

### Node test runner

```bash
swc-node --test ./math.test.ts
```

### CLI helpers

```bash
swc-node --help
swc-node --version
```

## Read `tsconfig.json`

Set `SWC_NODE_PROJECT` via CLI flag:

```bash
swc-node --tsconfig ./tsconfig.dev.json src/index.ts
swc-node --tsconfig ./tsconfig.dev.json -e "console.log('hello')"
```

or via environment variable:

```bash
SWC_NODE_PROJECT=./tsconfig.dev.json swc-node src/index.ts
```

`swc-node` also supports `compilerOptions.paths`/`baseUrl` path aliases from the selected tsconfig.

```bash
swc-node --tsconfig ./tsconfig.dev.json src/index.ts
# imports like `@utils/foo` resolve from tsconfig paths
```

## Notes

- Watch mode is delegated to Node (`--watch`) rather than custom orchestration.
- Running `swc-node` without an entrypoint is blocked (REPL mode is not supported).
- If you need a richer REPL/workflow tool, use [`tsx`](https://github.com/privatenumber/tsx).
