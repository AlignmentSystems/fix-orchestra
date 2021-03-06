
![](FIXorchestraLogo.png)

# FIX Orchestra Resources

This project contains resources and sample code for FIX Orchestra version 1.0. Technical specifications for FIX Orchestra are in project [fix-orchestra-spec](https://github.com/FIXTradingCommunity/fix-orchestra-spec).

FIX Orchestra is intended to provide a standard and some reference implementation for *machine readable rules of engagement* between counterparties. The goal is to reduce the time to get counterparties trading, and improve accuracy of implementations.

### News

* Version 1.5 of this project conforms to Orchestra version 1.0 Draft Standard.
* The repositoryDiffMerge module was promoted to its own [xml-diff-merge project](https://github.com/FIXTradingCommunity/xml-diff-merge) since it has uses aside from Orchestra.
* See new [Orchestra tutorials](https://github.com/FIXTradingCommunity/fix-orchestra/wiki) and FAQ.

### Planned Lifecycle

The planned lifecycle of this project is to roll out new features in a series of release candidates. After each release candidate is approved, it will be exposed to public review.  When a version is considered complete, the last release candidate will be promoted to Draft Standard.

### Participation

Issues may be entered here in GitHub or in a discussion forum on the [FIX Trading Community site](http://www.fixtradingcommunity.org/). In GitHub, anyone may enter issues or pull requests for the next release candidate. 

### References
Specifications for Orchestra in GitHub.

[Orchestra specifications](https://github.com/FIXTradingCommunity/fix-orchestra-spec)

Public Orchestra files for service offerings

[Orchestrations](https://github.com/FIXTradingCommunity/orchestrations)

All FIX standards specifications

[FIX Standards](https://www.fixtrading.org/standards/)

## Standards Versions

### Version 1.0 Draft Standard

Release candidate 5 was promoted to Draft Standard with minor enhancements and corrections on February 20, 2020. A draft standard must have at least two interoperable implementations in order to be promoted to a final Technical Standard.

Version 1.5 of this project conforms to Orchestra version 1.0 Draft Standard. The XML schemas in the `repository` and `interfaces` modules are considered normative for the Orchestra standard. However, demonstration code in this project may be maintained and enhanced between versions of the standard.

### Version 1.0 Release Candidate 5
Release Candidate 5 was approved by the Global Technical Committee on Sept. 19, 2019 for 90 day public review. The key enhancements in Release Candidate 5 were:

* Security keys for sessions
* Support for XML Inclusions (XInclude)
* Syntax for mutually exclusive message elements

### Version 1.0 Release Candidate 4
Release Candidate 4 was approved by the Global Technical Committee on Feb. 21, 2019 for 90 day public review.
Themes:
* Tool development
* Schema refinements as needed

### Version 1.0 Release Candidate 3
Release Candidate 3 was approved by the Global Technical Committee on March 8, 2018 for 90 day public review.
Themes:
* Semantic concepts
* Additional demonstration applications: documentation generator, test generator
* Refinement of previous deliverables

### Version 1.0 Release Candidate 2
Release Candidate 2 was approved by the Global Technical Committee on May 18, 2017 for 90 day public review. The themes for Release Candidate 2 were:
* Completion of a DSL grammar for conditional expressions
* FIXatdl integration
* Session configuration

### Version 1.0 Release Candidate 1
Version 1.0 RC1 standardized the XML schema for FIX Orchestra. Release Candidate 1 was approved by the Global Technical Committee on Dec. 15, 2016 for 90 day public review. 

## Normative Modules
The following modules are **normative**.

### repository
This module contains an XML schema for Orchestra. It is used to convey message structures and their components, as well as FIX application behaviors. Users may express workflow as responses to messages under different scenarios, as well as external state information that may influence behaviors.

In addition to providing the XML schema as a resource, the module builds Java bindings for the schema. An XSLT is provided to translate existing Repository 2010 Edition files to the Orchestra schema.

### interfaces

This module provides an XML schema for service offerings, protocols and session provisioning. In addition to providing the XML schema as a resource, the module builds Java bindings for the schema. Service elements may link to Orchestra files composed in the `repository` schema.


### dsl-antlr - Score Domain Specific Language (DSL)

An orchestra file may contain conditional expressions to describe conditionally required fields and tell when a certain response to a message applies. Also, the DSL may be used for assignment expressions to set message fields and external state variables.

The Score grammar is provided in the notation of ANTLR4, and the project builds a lexer/parser for the grammar. This project generates Java code, but ANTLR4 is capable of generating several other programming languages from the same grammar.

## Informational Modules

### repository2010
Repository 2010 Edition was the version of the FIX Repository prior to FIX Orchestra. This module provides a parser for its XML schema. It may be used to process existing Repository files and to convert their message structures to Orchestra format.

### docgen
This utility generates documentation for an Orchestra file that can be view in any web browser. The output of the generator may be used locally or from a web server.

### testgen
This module is a demonstration of acceptance test generation from an Orchestra file using Behavior Driven Design (BDD) concepts.

## Experimental Modules
This following modules are **experimental**. Requirements are still being gathered and discussed by the FIX Orchestra working group. Participation in the working group is encouraged by FIX Trading Community members, and more broadly, feedback is welcome from interested GitHub users.

### Code Generation for Encoding

#### orchestra2sbe

This utility has been moved to repository [FIXTradingCommunity/fix-sbe-utilities](https://github.com/FIXTradingCommunity/fix-sbe-utilities).
It creates a [Simple Binary Encoding](https://github.com/FIXTradingCommunity/fix-simple-binary-encoding) message schema from an Orchestra file.

#### fix-orchestra-protobuf
See repository [FIXTradingCommunity/fix-orchestra-protobuf](https://github.com/FIXTradingCommunity/fix-orchestra-protobuf) for utilities to generate
Google Protocol Buffers schemas from an Orchestra file.

### FIX Engine Provisioning

#### repository-quickfix

This module generates a QuickFIX data dictionary from an Orchestra file. The format can be consumed by the C++, Java and .NET versions. Additionally, the module generates message classes for QuickFIX/J directly from an Orchestra file. Although the QuickFIX data dictionary format is not as richly featured as Orchestra, it is hoped that this utility will help with Orchestra adoption. In future, message validation will be able to take advantage of conditional expressions in Orchestra.

#### message-model
Generic interfaces for message validators and populators not specific to a FIX engine implementation.

#### model-quickfix
This module generates code that is conformant to the QuickFIX/J API for validating and populating messages. It is dependent on `repository-quickfix`.

#### session-quickfix
A demonstration of session configuration for QuickFIX open-source FIX engine. It consumes an XML file in the `interfaces` schema.

A module like this needs to be developed to support each FIX engine that uses a proprietary configuration format. The demonstration provides an example to follow for that work.

### state-machine
A demonstration of state machine code generation from an Orchestra file.

### Data Files
Data files in this project under `test/resources` are strictly for testing and to serve as examples for format. They are non-normative for FIX standards and may not be up to date.

See [FIX Standards](https://www.fixtrading.org/standards/) for normative standards documents and [FIX Repository](https://www.fixtrading.org/standards/fix-repository/) for latest Repository extension packs. The plan is to start publishing extension packs in the Orchestra schema in 2020.

## License
© Copyright 2016-2020 FIX Protocol Limited

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

### Technical Specifications License

Note that the related Technical Specifications project has a different license than these resources. See [fix-orchestra-spec](https://github.com/FIXTradingCommunity/fix-orchestra-spec/blob/master/LICENSE)

## Prerequisites
This project requires Java 8 or later. It should run on any platform for which the JVM is supported. The plan is update this project to a minimum of Java 11, a long-term support version, soon.

## Build
The project is built with Maven version 3.0 or later. 

