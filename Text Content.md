## Title

##### Main title
One LIMS Interface To Connect Them All

##### Subtitle
Exploring LIMS Agnosticity and Abstraction

## Introduction - The Hardwired Legacy

The legacy IAC application was hardwired to Illumina LIMS, making integration with other systems, such as Clarity LIMS, difficult. The root cause was a legacy architecture that did not account for flexible future integrations.

Because IAC was tightly coupled to Illumina LIMS, integrating with alternative LIMS solutions presented substantial architectural challenges.

## ILASS Integration Design Goals

When developing the Illumina Lab Automation Software Solution (ILASS), we recognized that a lab management platform must connect seamlessly to various external tools and services. By defining the required interactions between ILASS and a LIMS as a set of public API specifications, any LIMS can implement an adapter to satisfy these requirements. We call this abstraction layer ILASS LIMS Communication Services (LCS).

**Business Advantage**: A flexible, open LIMS connectivity specification allows clients to use their preferred (or existing) LIMS, significantly enhancing ILASS's value and appeal.

## Implementation

The initial LCS interface was implemented as a .NET class library (.dll) distributed to ILASS as a NuGet package. Its public interface enabled third-party developers to build LIMS adapters as .NET libraries. However, this architecture coupled third-party development tightly to the .NET ecosystem. To eliminate tech-stack constraints, we transitioned the LCS architecture to an HTTP-based Web API microservice. Internal and external teams can now build adapters against the LCS API specifications using the technology stack of their choice.

![[LCS architecture.png]]

#### Challenges
- Frankenstein problem: LIMS solutions often expose vastly different public API surfaces. Adapting to diverse paradigms risks turning the LCS interface into a "Frankenstein" API where only a subset of endpoints applies to any specific LIMS.

## Current Status of Work

- Clarity LIMS for Infinium and Cabrillo (cancelled) workflows
- iLIMS for Infinium workflows
- [Aquarium Lab Operating System](https://github.com/aquariumbio/aquarium) for a 3rd-party LIMS connectivity proof of concept.

## Potential Future Work

- Gemini LIMS (MRD - future work)
- IOS
	- Interstellar Orchestrator Software (IOS) is a sample-to-answer solution designed to automate NGS workflows. Its core capabilities encompass sample, run, and workflow management, alongside integrated data analysis for secondary and tertiary analysis and reporting. IOS builds on several major independently releasable Illumina software components—including DRAGEN Applications, Illumina Connected Insights (ICI), and Illumina Connected Analytics (ICA)—leveraging AWS for cloud deployment. For on-premises environments (IOS Local), a self-contained solution is available on the DRAGEN server.
- Genos
- Third-party LIMS integrations
- Extend LCS connectivity beyond ILASS, enabling other teams to integrate with the LCS interface
- LIMS Model Context Protocol (MCP)
- Standardize LIMS APIs across the industry
- Host lcs interface or adapters in cloud

## References
- IOS SAD
- 
## Acknowledgements
1. Joshua Dion
2. Josh Humpherys 
3. Wilson Chandra Tjhi


## Contact Us

![[Email Robocops QR.png|232]]