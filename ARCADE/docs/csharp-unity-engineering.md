# C# / Unity Engineering Instructions

These instructions are mandatory for every agent when generating or modifying
C#, `.csproj`, `.asmdef`, managed-plugin, or Unity serialization code in this
repository.

## Priorities

Optimize in this order: correctness, Unity and target-platform compatibility,
readability, maintainability, required determinism, testability, measured
performance, and brevity. Do not trade clarity or compatibility for cleverness.

## Compatibility gate

Before coding, read `ARCADE/ProjectSettings/ProjectVersion.txt` and the
relevant Unity Player settings. The pinned editor is Unity `6000.5.2f1`.
Verify language support, API Compatibility Level, target platforms, scripting
backend, and IL2CPP/AOT implications before introducing language features, BCL
APIs, dependencies, generators, analyzers, or runtime behavior.

The project currently documents API Compatibility Level 6 as `.NET Standard
2.1`. Treat the pinned Unity project settings and compatibility documentation as
the source of truth. C# language compatibility and .NET API compatibility are
separate checks. Never use `LangVersion: latest` as evidence that Unity can
compile a feature. Prefer the newest feature supported by the pinned Unity
compiler only when it improves clarity or safety.

Unity-consumed assemblies must expose a Unity-supported API surface and runtime
behavior. Portable libraries should target `.NET Standard 2.1` when supported.
Use multi-targeting only for a concrete need, keep Unity on the compatible
target, and prevent modern-target-only APIs from leaking into shared code.

## Architecture and assemblies

Keep the dependency direction:

```text
Unity presentation/adapters -> application/orchestration -> domain/simulation
```

Pure domain, simulation, protocol, and portable application code must not
reference `UnityEngine`, `UnityEditor`, `MonoBehaviour`, `ScriptableObject`,
scene lookup, Unity lifecycle, input, rendering, audio, asset, GameObject,
`Time`, `Random`, `Physics`, or other implicit Unity global state. Use ordinary
C# APIs and explicit dependencies.

Unity code is an adapter: translate lifecycle, input, time, assets, scenes,
serialization, platform APIs, and presentation at the boundary. Keep adapters
thin and do not move business rules into `MonoBehaviour` classes for
convenience.

Use explicit `.asmdef` boundaries where practical. Keep editor-only code out of
runtime assemblies, never reference `UnityEditor` from player code, forbid
circular assembly dependencies, and do not let portable DLLs reference Unity
adapters.

Prefer constructor injection for ordinary C# classes. Provide dependencies to
Unity-created objects through composition roots, serialized references,
factories, or bootstrap code. Do not use service locators, static mutable state,
`FindObjectOfType`, `GameObject.Find`, tag searches, or repeated hierarchy
traversal as dependency injection.

## C# design and naming

Follow standard .NET naming: PascalCase for types, methods, properties, events,
and public/protected members; camelCase for locals and parameters; `_camelCase`
for private instance fields; `I` prefixes only for meaningful abstractions; and
`Async` suffixes for asynchronous methods.

Prefer pattern matching, clear switch expressions, `readonly`, immutable state,
local functions, and other supported modern C# features when they improve the
code. Use records and `init` cautiously; never use records for Unity-serialized
data. Prefer simple serializable classes/structs at Unity boundaries.

Methods should do one cohesive thing at one abstraction level. Prefer early
returns, explicit invariants, explicit inputs/outputs, and composition over
inheritance. Seal classes when inheritance is not intended and Unity does not
require it. Avoid god classes, unrelated mutation, deep nesting, unclear
boolean parameters, and speculative interfaces or abstractions.

Use repository `.editorconfig`; otherwise use four spaces, braces for control
flow, one primary type per file, reasonable line lengths, and logical blank
lines. Use `var` when the type is obvious and explicit types when they improve
understanding.

## Unity lifecycle, time, randomness, and serialization

Keep `Awake`, `Start`, `Update`, `FixedUpdate`, `LateUpdate`, `OnEnable`, and
similar callbacks small. They should forward to application code, not contain
domain rules. Do not rely on callback ordering without making the dependency
explicit and documented.

Pass time or inject a clock. Pure code must not read Unity time or wall-clock
APIs. Deterministic simulation should use integer ticks or an explicit
simulation clock and must not mix frame time with simulation time implicitly.

Do not use `UnityEngine.Random` or `System.Random` directly in deterministic
domain/simulation code. Use an explicit seeded random abstraction/state. The
same initial state, inputs, and seed must reproduce the same result.

For Unity-owned serialized data, prefer `[SerializeField] private` fields and
read-only public properties. Verify supported container and generic shapes, use
`[SerializeReference]` intentionally, avoid records, and preserve renamed
serialized fields with `FormerlySerializedAs` where required. Do not make the
domain model conform to Unity serialization; convert at the boundary.

Treat Unity object null semantics separately from ordinary CLR nullability.
Validate required dependencies at construction/bootstrap boundaries and do not
use null-forgiving operators merely to silence warnings.

## Async, threading, exceptions, and logging

Use async all the way, propagate `CancellationToken`, avoid `.Result`, `.Wait()`,
unowned fire-and-forget tasks, unnecessary `Task.Run`, and `async void` except
for required callback signatures. Unity APIs, GameObjects, Components, scenes,
rendering, and similar state are main-thread-only. Marshal worker results back
before touching Unity. Worker code must be pure/thread-safe with explicit
ownership and cancellation.

Use exceptions for exceptional failures, not ordinary game flow. Catch only to
recover, translate, add context, or clean up; preserve the original exception
as `InnerException`. Never catch and ignore exceptions or throw per-frame as
normal behavior.

Portable code must not depend directly on `UnityEngine.Debug`; use a logging
abstraction and translate logs in Unity adapters. Avoid expensive messages when
logging is filtered and never log credentials, tokens, keys, or sensitive data.

## Collections, allocation, and AOT

Use LINQ for clarity outside measured hot paths. Avoid avoidable allocations,
boxing, closures, temporary collections, repeated string construction, and
component resolution in per-frame/per-tick code. Cache references where useful,
reuse buffers only with clear ownership, and optimize based on profiling or a
clear complexity/allocation argument.

Define iteration order whenever it affects deterministic behavior. Do not make
dictionary or hash-set ordering an accidental simulation contract.

Assume IL2CPP/AOT is required for Unity-consumed code. Avoid runtime code
generation, `Reflection.Emit`, JIT-only behavior, dynamic-heavy libraries,
runtime-generated serializers, open-ended reflection, and generic types only
instantiated through reflection. Preserve reflected or serialized types through
the established `link.xml`, preserve-attribute, or generated-registration
strategy. Verify representative IL2CPP builds for sensitive changes.

Before adding a dependency, verify Unity/API/framework compatibility, IL2CPP,
platforms, transitive dependencies, licensing, maintenance, ownership, and
version pinning. Do not add a package for a trivial helper.

## APIs and testing

Make invalid use difficult. Prefer explicit domain types over ambiguous strings
or integers and keep serialized/network contracts stable and deliberately
versioned. Keep public portable contracts free from Unity types unless the
assembly is intentionally a Unity adapter.

Test pure domain/application code without Unity where possible. Use Unity
EditMode/PlayMode tests only for engine-dependent behavior. Test behavior and
invariants, add regression tests for bugs where practical, and test
deterministic repeatability. Test managed DLLs both independently and through
representative Unity integration.

Keep editor tooling in editor-only assemblies/folders. Public non-obvious APIs
may have concise XML documentation. Comments should explain constraints,
invariants, compatibility workarounds, deterministic requirements, or measured
performance decisions, not restate code.

## Required pre-edit report

Before modifying code, state:

- Change: what is being implemented.
- Packages: new packages, or `None`.
- Files: files to modify or create.
- Compatibility: pinned Unity version, supported C# version, API Compatibility
  Level, whether code runs inside Unity/outside Unity/both, and IL2CPP needs.
- Risks: affected systems, performance impact, and security impact.
- Plan: dependencies between changes, task split, and verification steps.

Do not proceed on an assumed Unity version when the repository can determine it.

## ADR and verification requirements

For meaningful architectural or cross-cutting changes, create or update a
Markdown ADR covering overview, files, decisions, challenges/solutions,
compatibility, and future considerations. Do not create ADRs for trivial edits
unless project policy requires it.

Before completion, review for unsupported language/API features, Unity leaks in
portable code, assembly direction, unnecessary abstractions/dependencies,
serialization and AOT risks, and scope creep.

Run applicable checks: `dotnet build`, `dotnet test`, Unity compilation,
relevant EditMode/PlayMode tests, assembly resolution checks, and representative
IL2CPP builds for reflection, serialization, generic registration, interop,
stripping, or managed-plugin changes. Report checks that could not run.

## Prohibited shortcuts

Do not disable analyzers/nullability to silence warnings, suppress warnings
without documenting why, block asynchronous tasks, swallow exceptions, add
global mutable state for convenience, add mechanical interfaces, introduce
unsupported syntax or APIs, reference Unity from domain/simulation code,
reference `UnityEditor` from runtime code, rely on Editor/JIT-only behavior, or
perform unrelated refactors during scoped work.
