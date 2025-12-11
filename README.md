# FluentLoggerExtensions

Fluent extensions for `Microsoft.Extensions.Logging` that capture caller file, member, and line information and prepend it to your log messages.

## Install
- From NuGet: `dotnet add package FluentLoggerExtensions`
- Or reference the project directly in your solution.

## Usage
```csharp
using FluentLogger;
using Microsoft.Extensions.Logging;

var logger = loggerFactory.CreateLogger<Program>();

logger.WithCaller().LogInformation("Processing {RequestId}", requestId);
// Logs something like: [Program.cs:Main:42] Processing 12345

logger.WithCaller().LogError("Failed to process {RequestId}: {Reason}", requestId, reason);
```

## API
- `ILogger.WithCaller([CallerFilePath] file, [CallerMemberName] member, [CallerLineNumber] line)` returns a `CallerLogContext` with captured caller info.
- `CallerLogContext.LogInformation|LogWarning|LogError|LogDebug` log with a `[{File}:{Member}:{Line}]` prefix while preserving structured logging args.

## Requirements
- Target framework: `netstandard2.0`
- Dependency: `Microsoft.Extensions.Logging.Abstractions (8.0.0)`

## Development
- Build: `dotnet build` (the project is configured to generate a NuGet package and symbols on build).

## License
MIT
