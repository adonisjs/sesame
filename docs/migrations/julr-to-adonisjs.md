# Move from @julr/sesame to @adonisjs/sesame

Sésame is now published as `@adonisjs/sesame`. The package name is the only change: the API, configuration, commands, and database schema are the same. You do not need to run new migrations.

If your installation is older than 0.8, first upgrade with `@julr/sesame` by following the [0.8 migration guide](./0.7-to-0.8.md). Then switch packages.

## Replace the package

Remove the old package and install the new one:

```bash
pnpm remove @julr/sesame
pnpm add @adonisjs/sesame
```

Do not run `node ace add @adonisjs/sesame` on an existing installation. That command publishes a fresh config and fresh migrations.

## Update the import paths

Replace `@julr/sesame` with `@adonisjs/sesame` everywhere in your application. The subpaths do not change. Check these files:

- `adonisrc.ts`: the provider `@adonisjs/sesame/sesame_provider` and the commands `@adonisjs/sesame/commands`.
- `start/kernel.ts`: the `scopes` and `anyScope` named middleware.
- `config/sesame.ts`: the `defineConfig`, `stores`, and `InferScopes` imports.
- `config/auth.ts`: the `oauthGuard` and `oauthUserProvider` imports.
- Your controllers, models, and tests that import from `@julr/sesame/...`.

Also update every `declare module '@julr/sesame/types'` block, such as the scopes declaration in `config/sesame.ts`:

```ts
declare module '@adonisjs/sesame/types' {
  interface SesameScopes extends InferScopes<typeof sesameConfig> {}
}
```

To find the remaining references, run:

```bash
grep -rn "@julr/sesame" --exclude-dir=node_modules .
```
