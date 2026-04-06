# Tech Stack Detection Patterns

Quick reference for identifying project tech stacks from file signatures.

## By Config File

| File | Tech Stack |
|------|------------|
| `package.json` | Node.js/JavaScript/TypeScript |
| `tsconfig.json` | TypeScript |
| `pyproject.toml`, `setup.py`, `requirements.txt` | Python |
| `Cargo.toml` | Rust |
| `go.mod`, `go.sum` | Go |
| `pom.xml`, `build.gradle` | Java |
| `Gemfile` | Ruby |
| `composer.json` | PHP |
| `pubspec.yaml` | Dart/Flutter |
| `*.csproj`, `*.sln` | C#/.NET |
| `mix.exs` | Elixir |
| `deno.json` | Deno |
| `bun.lockb` | Bun |

## Framework Detection

### JavaScript/TypeScript
| Indicator | Framework |
|-----------|-----------|
| `next.config.*` | Next.js |
| `nuxt.config.*` | Nuxt.js |
| `vite.config.*` | Vite |
| `angular.json` | Angular |
| `svelte.config.*` | SvelteKit |
| `remix.config.*` | Remix |
| `astro.config.*` | Astro |
| `gatsby-config.*` | Gatsby |
| `vue.config.*` or `@vue/` in deps | Vue.js |
| `react` in deps | React |
| `express` in deps | Express.js |
| `fastify` in deps | Fastify |
| `nestjs` in deps | NestJS |

### Python
| Indicator | Framework |
|-----------|-----------|
| `django` in deps | Django |
| `flask` in deps | Flask |
| `fastapi` in deps | FastAPI |
| `streamlit` in deps | Streamlit |

### Other
| Indicator | Framework |
|-----------|-----------|
| `rails` gem | Ruby on Rails |
| `laravel` | Laravel (PHP) |
| `spring` | Spring (Java) |
| `gin-gonic` | Gin (Go) |
| `actix` or `axum` | Rust web framework |

## Common Directory Patterns

| Directory | Typical Purpose |
|-----------|-----------------|
| `src/` | Source code |
| `lib/` | Library code |
| `app/` | Application code (Rails, Next.js, Laravel) |
| `pages/` | Page routes (Next.js, Nuxt) |
| `components/` | UI components |
| `services/` | Business logic services |
| `models/` | Data models |
| `controllers/` | Request handlers (MVC) |
| `utils/`, `helpers/` | Utility functions |
| `api/` | API routes or definitions |
| `tests/`, `__tests__/`, `spec/` | Test files |
| `config/` | Configuration |
| `public/`, `static/` | Static assets |
| `migrations/` | Database migrations |
