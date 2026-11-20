# hello-dotnet

A **.NET** console application targeting .NET 8.0 — built and tested by GitHub Actions on every push.

The app prints "Hello from .NET!" along with version, OS, and architecture info.

## Build & run

```bash
# Restore dependencies
dotnet restore src/HelloDotnet.csproj

# Build
dotnet build src/HelloDotnet.csproj

# Run
dotnet run src/HelloDotnet.csproj
```

Requires the [.NET SDK](https://dotnet.microsoft.com/download) (8.0.x).

## CI pipeline

The [CI workflow](.github/workflows/ci.yml) runs on every push and pull request:

1. **Format check** — `dotnet format` on source and tests
2. **Build** — compiles the project in Release configuration
3. **Test** — runs unit tests with verbose output

When a tag (`v*`) is pushed, a **release job** publishes standalone binaries for **5 RIDs** (runtime identifiers) and uploads them as release assets:

| RID           | Asset                          |
|---------------|--------------------------------|
| `linux-x64`   | `hello-dotnet-linux-x64`       |
| `linux-arm64` | `hello-dotnet-linux-arm64`     |
| `win-x64`     | `hello-dotnet-windows-x64.exe` |
| `osx-x64`     | `hello-dotnet-macos-x64`       |
| `osx-arm64`   | `hello-dotnet-macos-arm64`     |

Binaries are self-contained single-file executables.