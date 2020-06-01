[Table of contents](../README.md#contents)

# Appendix C: The SARIF validation tool

## Introduction

Many but not all of the best practices in the Appendix ["SARIF log file best practices"](./Authoring-good-SARIF.md)
are enforced by the SARIF validation tool (the "validator").
You can run the validator on your own SARIF files to see how well they conform to best practices.

The validator provides a set of rules, each of which defines (as all SARIF rules should)
an opaque id (for example, `SARIF1003`) and a human-readable name (for example, `UrisMustBeValid`).
When we describe a best practice that corresponds to a validation rule, we'll refer to the rule by a
combination of its opaque id and its readable name (for example, `SARIF1003.UrisMustBeValid`).

The validator first ensures that the input file is valid JSON,
and then validates it against the SARIF schema.
This ensures, among other things, that all required properties are present,
and that property values conform to the specified data types such as "number".

The validator doesn't need to provide rules for constraints that the schema can express.
But the schema can't express many of the constraints in the specification,
and it can't express the best practices.
This is why the validator exists.

## Installation and use

The validator is a .NET Core executable (`netcoreapp3.1`), available as a NuGet tool package.
It runs on Windows, Mac, and Linux.
To install it:

1. Install .NET Core 3.1 or later.
2. Install the `Sarif.Multitool` NuGet tool package:

```
dotnet tool install Sarif.Multitool --global
```

This installs `Sarif.exe` and places it on your execution path.
To validate a SARIF file MyFile.sarif and display the results on the console:

```
sarif validate MyFile.sarif
```

To validate the file and save the results to a SARIF log file:

```
sarif validate MyFile.sarif --output MyFile-validation.sarif --pretty-print
```

Type `sarif help validate` for full command line help.

The `sarif` command actually offers several "verbs", of which `validate` is only one.
Type `sarif help` for the full list of verbs.

[Table of contents](../README.md#contents)