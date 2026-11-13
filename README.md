# Sésame

OAuth 2.1 + OpenID Connect server for AdonisJS.

Sésame adds OAuth endpoints to your application. You keep your user accounts, login page, and consent UI.

- Authorization code flow with mandatory PKCE
- Refresh token rotation, replay detection, and grant revocation
- Bearer token authentication with type-safe scopes
- OpenID Connect, client credentials, and dynamic client registration
- MCP support and Lucid or Kysely storage

## Get started

Requires AdonisJS 7, Node.js 24 or later, and `@adonisjs/auth`.

With Lucid and a session guard already configured:

```bash
node ace add @adonisjs/sesame
node ace migration:run
```

Then configure your issuer and scopes in `config/sesame.ts`, mount the OAuth routes, and connect your login and consent pages.

See the [installation guide](https://docs.adonisjs.com/guides/oauth-server/introduction#installation) for the full setup, including the Kysely store for a Lucid-free application.

## Documentation

[Read the documentation](https://docs.adonisjs.com/guides/oauth-server/introduction) on the AdonisJS website for guides and the API reference.

Coming from `@julr/sesame`? Follow the [package rename guide](docs/migrations/julr-to-adonisjs.md). Upgrading an existing installation? Follow the [0.8 migration guide](docs/migrations/0.7-to-0.8.md) or the [0.7 migration guide](docs/migrations/0.6-to-0.7.md).

## License

MIT
