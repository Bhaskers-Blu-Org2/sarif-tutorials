[Table of contents](../README.md#contents)

# Appendix A: SARIF log file best practices

This Appendix recommends best practices for the contents of SARIF log files.

Because of requirements imposed by OASIS, the SARIF specification always describes format features
using the key words defined in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt), for example
**MAY** (the feature is truly optional), **SHOULD** (use the feature unless you have a good reason not to),
and or **SHALL** (use of the feature is mandatory). There are no shades of gray between those categories.

But sometimes the importance of a feature depends on how the SARIF file will be used.
For example, if it is the input to an automatic bug filing system,
features which contribute to more informative, actionable bugs take on a greater importance.
Usage scenarios aside, some optional features have proven in our experience to be particularly valuable,
and we discuss those here as well.

Many but not all of the recommendations in this Appendix are enforced by the SARIF validation tool (the "validator").
You can run the validator on your SARIF files to see how well they conform to these recommendations.
The Appendix ["The SARIF Validation Tool"](./SARIF-validation-tool.md) explains how to install and use the validator.

## Result messages should be "dynamic" rather than "static"

The Appendix ["Authoring rule metadata and result messages"](./Authoring-rule-metadata-and-result-messages.md)
provides detailed guidance on authoring informative, actionable result messages.
One of the most important principles is to provide "uniquely identifying information" in each result message,
that is, information that describes this particular instance of an analysis rule violation.
This information might include:
- A subset of the pysical location, for example, the name of the file where the violation occurred.
- A subset of the logical location information, for example, the name of the class or method where the violation occurred.
- Other information specific to the analysis rule, for example, the name of an insecure API that was used, and the name of a more secure replacement for that API.

Providing uniquely identifying information serves at least two purposes:
- It gives developers the specific information they need to understand and solve the problem.
- It avoids the "wall of bugs" phenomenon, where a long list of identical messages presents a psychological obstacle to the developer responsible for solving the problems.

## Provide a $schema property that points to the final version of the SARIF schema.

The property `sarifLog[$schema]` is important because it enables Intellisense in VS and other IDEs.
Its value is a URI from which the SARIF JSON schema can be obtained.
Make sure to use the final, released version of the schema.

We recommend the value "https://schemastore.azurewebsites.net/schemas/json/sarif-2.1.0-rtm.5.json".

## Provide tool.version

It's important to provide `tool.version` so that toolchains can tell if an approved version of the tool is in use.

[Table of contents](../README.md#contents)