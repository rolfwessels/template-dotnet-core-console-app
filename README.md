# 🌐 Template dotnet core console app

[![CI](https://github.com/rolfwessels/template-dotnet-core-console-app/actions/workflows/github-action.yml/badge.svg)](https://github.com/rolfwessels/template-dotnet-core-console-app/actions/workflows/github-action.yml)

A .NET 8 CLI starter with Spectre.Console for command handling, Serilog for logging, and NUnit and AwesomeAssertions for tests.

![Template dotnet core console app](docs/logo.png)

## 🛠 Prerequisites

- Git and `make` (use WSL on Windows for the Makefile commands).
- The .NET 8 SDK for local development, or Docker with Compose for the development container.

## 🚀 Quick start

Run these commands from the repository root with the SDK installed. To use Docker, first run `make build up` on the host and continue in the development shell it opens.

```sh
make start
dotnet run --project src/TemplateDotnetCoreConsoleApp.Cmd -- default sample
```

The first command displays CLI help. The second prints `Processing sample..` and exits successfully.

## 📋 Make commands

| Command | Purpose |
| --- | --- |
| `make start` | Display the CLI help. |
| `make test` | Run the solution's tests with coverage. |
| `make build up` | Build the development container and open its shell. |
| `make down` | Stop the development container from the host. |

Run `make help` for more targets.

## 💻 Development

Commands live in `src/TemplateDotnetCoreConsoleApp.Cmd/`, with corresponding tests under `tests/`. Use [AGENTS.md](AGENTS.md) for branch naming, pull requests, and verification.

To extend the solution with a library and its own tests, create the projects with `dotnet new classlib` and `dotnet new nunit`, then add them to the solution with `dotnet sln add`.

## 📦 Releases and deployment

- `make publish` writes self-contained Linux and Windows x64 builds under `dist/`.
- `make docker-build` builds the application image. Use `make docker-publish` to build and push after configuring your registry.
- Set the major and minor version with `versionPrefix` in the Makefile. The patch comes from the Git commit count. `make version` writes the current version to `src/version.json`.
- Create release tags such as `v1.2.0` on `main`. For an urgent fix to an older release, branch from its tag and merge the fix back into `main`.

## 📜 License

See [LICENSE.txt](LICENSE.txt).
