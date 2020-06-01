[Table of contents](../README.md#contents)

# Appendix A: Authoring "good" SARIF

## Introduction

This Appendix describes best practices for the contents of SARIF log files.

Because of requirements imposed by OASIS, the SARIF specification always describes format features
using the key words defined in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt), for example
**MAY** (the feature is truly optional), **SHOULD** (use the feature unless you have a good reason not to),
and or **SHALL** (use of the feature is mandatory). There are no shades of gray between those categories.

But sometimes the importance of a feature depends on how the SARIF file will be used.
For example, if it is the input to an automatic bug filing system,
features which contribute to more informative, actionable bugs take on a greater importance.

## The SARIF validation tool

Many of the best practices in this Appendix are enforced by the SARIF validation tool,
which we'll refer to as the "validator",
and which is available from NuGet as a "tool package".
This tool defines a set of 


[Table of contents](../README.md#contents)