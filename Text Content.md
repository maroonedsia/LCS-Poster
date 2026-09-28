## Title

##### Main title
One LIMS Interface To Connect Them All

##### Subtitle
Our Efforts towards LIMS Agnosticity and Abstraction

## Introduction - The ~~Problem~~ Why
IAC legacy app was hard-wired to Illumina LIMS. This made it very difficult to connect IAC to other systems, such as Clarity LIMS. The root cause of the problem was the legacy architecture that had not predicated flexible connections for future integrations.

The legacy application IAC was designed to tightly integrate with illumina LIMS, this presented challenges when integrating with other LIMS such as Clarity.

## Design Goals

As my team started developing Illumina Lab Automation Software Solution (ILASS), we realized that a lab management application should be able to get connected to various external tools and services. By extracting the interactions that are required between ILASS and a LIMS into a public API specifications, we allow any LIMS to create an adapter for these requirements. The abstraction layer that defines the specifications is called ILASS LIMS Communication Services (LCS).

**Business Advantage**: A flexible and open LIMS connectivity specification gives the freedom to clients to use their own (and maybe existing) LIMS. This will make ILASS much more desirable. 

## Implementation

The initial implementation of LCS interface was a .NET class library (.dll) that could be added ILASS as a nuget package. The public interface of this library allowed 3rd party developers to implement adapters for their LIMS, as .NET libraries. This architecture was limiting the 3rd party developers to .NET technology. To remove this tech stack dependency, we move the LCS architecture to an HTTP-based web APIs microservice. This way, other internal or external teams can develop their adapter using the LCS API specifications, using the tech stack of their own choice.

![[LCS architecture.png]]

#### Challenges
- Frankenstein problem: LIMS solutions may expose very different public API surface to the outside. This means if the LCS Interface wants to adapt LIMS with different paradigms, it gradually become a Frankenstein of APIs, that only a subset of them is applicable to a certain LIMS.

## Current Status of Work

- Clarity LIMS
- iLIMS => (Infinium)
- [Aquarium Lab Operating System](https://github.com/aquariumbio/aquarium) => Proof of concept

## Potential Future Work

- Gemini LIMS (MRD - future work)
- IOS
	- The Interstellar Orchestrator Software (IOS) is a sample to answer solution developed to automate NGS workflows. Its core functionalities encompass sample, run, and workflow management, alongside integrated data analysis capabilities for secondary, tertiary analysis & reporting. IOS is built upon several major independently releasable Illumina software components including DRAGEN Applications, Illumina Connected Insights (ICI), and Illumina Connected Analytics (ICA) leveraging the AWS cloud platform for deployment. For local deployments (IOS local), a self-contained solution is available on the DRAGEN server.
	- **ADD CHART**![[Pasted image 20260915100123.png]]
- genos?
- Third-party LIMS 
- Expand the concept to Instrument APIs, such as Hamilton and Tecan robots.
- LCS connector is not limited to ILASS. Other teams can integrate to LCS Interface to update connected

## References
- IOS SAD
- 
## Acknowledgements
1. Joshua Dion
2. Josh Humpherys 
3. Wilson Chandra Tjhi


## Contact Us

![[Email Robocops QR.png|232]]