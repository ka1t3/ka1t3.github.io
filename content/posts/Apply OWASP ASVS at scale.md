+++
date  = 2025-04-04
draft  = false
title  = 'Apply OWASP ASVS at scale'
tags = ["OWASP","Application Security", "ASVS"]
+++

## The ASVS

The ASVS is a framework that defines functional and non-functional security controls to be considered during the design, development, and testing phases of web applications and services. It presents itself as a system that is both demonstrable and reproducible for verifying the security level of an application. The latest officially published version is Release V4.0.3, dated October 2021, and spans 71 pages.

> A useful side note: A version 5.0 is expected in 2025, but I will discuss it further at the end of the article.

In essence, the ASVS serves two main purposes. On one hand, it allows organizations to build, evolve, and maintain thoroughly secure applications. On the other hand, it facilitates the alignment of security requirements between service and tool providers and consumers by clarifying expectations and standards.

### A Three-Tier Hierarchical Structure

The ASVS organizes its requirements around three distinct levels, reflecting the intensity of controls to be applied. The higher the level, the more stringent and numerous the requirements. These requirements are distributed across fourteen thematic domains covering all application security issues.

**Level 1**, which could be described as opportunistic, constitutes the first step towards application security. It is also the only level that can be implemented without access to the source code, relying on "black-box" tests, whether manual or automated. This is the basic level. However, it allows protection against the most obvious vulnerabilities, often listed in the OWASP Top 10 or other public checklists. It helps to deter opportunistic attackers who use basic, unsophisticated, and low-cost techniques.

**Level 2**, designated as standard, is suitable for applications that handle sensitive data or have critical functions. It provides enhanced defense against a wide range of threats by ensuring that security mechanisms are not only present but also functional and effectively used. This level is relevant for applications involved in sensitive inter-company exchanges, handling medical data, or in sectors where data integrity is crucial. For example, human resource management platforms handle sensitive personal data such as salary information, contracts, and performance evaluations. At this level, the application must be able to withstand motivated, technically competent attackers armed with widely available tools.

Finally, **Level 3** is the advanced level, designed for so-called critical applications. These are applications whose compromise could have major impacts on operations or even the survival of the organization. This includes military systems, critical infrastructure, and applications in the healthcare sector. At this level, security requirements reach an unparalleled depth, with rigorous audits of architecture, code, and testing. The goal is to demonstrate that secure design principles are followed at every stage of the software lifecycle.

## What is the ASVS Used For?

In practice, the ASVS can play several roles depending on the organization's objectives. It can first be used as a **metric** to provide technical teams and application owners with a clear scale to evaluate the security level of an application. It also serves as a **guide**, helping architects and developers identify relevant controls to integrate into their approach. Additionally, in the context of procurement or contracting, it can serve as an **evaluation criterion**, providing a basis for formulating security requirements to be met by a supplier.

### A Composite Standard

One of the strengths of the ASVS is its ability to consolidate a wide range of recognized standards into a single document. It includes references from the NIST 800-63-3 on digital identity, the well-known OWASP Top 10 (2017 version – the 2021 version is not yet integrated), and the OWASP Proactive Controls from 2018. Additionally, it incorporates elements from the PCI-DSS standard (section 6.5 of version 3.2.1), a mapping with the CWE (Common Weakness Enumeration) framework, and coverage that extends to both classical architectures and more modern approaches like Agile or DevSecOps. Although not everything is perfectly integrated yet, the unification effort is commendable.

Moreover, some adjustments from the OWASP Top 10 2021, such as the introduction of categories like "Insecure Design" (A04:2021) and "Software and Data Integrity Failures" (A08:2021), or the merging of certain vulnerabilities, are not yet reflected in the current version of the ASVS. This discrepancy highlights the need for an upcoming update.

## ASVS, SKF, WSTG: Complementary Objectives and Uses

The **Application Security Verification Standard** (ASVS) is sometimes confused or compared with other tools or frameworks offered by OWASP. It is, therefore, useful to clarify the complementarity between these different projects.

The ASVS primarily positions itself as a **verification standard**. It provides a rigorous framework for evaluating the security level of an application through a series of organized and hierarchical requirements. It is the normative building block that structures the evaluation of application security—in a way, the **"what to verify"**, with 286 requirements spread across three levels.

In parallel, the **OWASP Security Knowledge Framework** (SKF) adopts a more operational and educational approach. It is an open-source web application designed as a learning environment for developers. It aims to teach how to write secure code from the design phase, with concrete examples, best practice guides, and contextualization by category of requirement. Where the ASVS defines expectations, the SKF illustrates **how to meet them** through examples.

Finally, the **Web Security Testing Guide** (WSTG) complements the ecosystem with a clear focus on auditing. It provides a detailed methodology for conducting security tests on web applications and services. It includes scenarios, techniques, and practical advice for testing different attack surfaces. It is, in a way, the **"how to test"**, a valuable field guide for penetration testers, security analysts, or developers who wish to deepen their verification aspects.

These three projects are therefore not necessarily redundant but **complementary**.

## What the ASVS Does Not Cover (Yet)

The ASVS, although quite comprehensive, does not cover all aspects of digital system security. It is primarily focused on web applications and services. It does not address **mobile applications**, which fall under a dedicated framework: the **Mobile Application Security Verification Standard (MASVS)**. Similarly, IoT devices, embedded environments, or certain aspects related to physical security are not within its scope.

It also does not align with a security management system framework like **ISO 27001**.

## Large-Scale Implementation: Feedback

I had the opportunity to deploy the ASVS in a CAC40 company. The context? A desire to structure, at the organizational level, a secure framework for all application developments. It was in this dynamic that I naturally turned to the ASVS, convinced by its comprehensive approach and transversal nature.

Very quickly, it became necessary to go beyond simply reading the framework. The goal was to use it as a standard applicable to the entire company, in an environment where development practices varied greatly from one team to another (from one department to another and also from one country to another). In this context, a parsimonious approach, both pragmatic and progressive, was essential.

### Initial Steps and Framing

The first step was awareness. It was necessary to demonstrate the interest in adopting the ASVS on a large scale. For this, I formed a group of experienced developers from different entities to create a federating dynamic around the project. I will spare you the organizational details – it might make this post a bit soporific – but overall, **it took me a whole year** (yes, a full year) to structure and concretize the entire approach.

### Creating a Custom Standard

We started with the French version of the ASVS as our working base. Very quickly, an obvious fact emerged: for a developer, the document is too dense, too raw. It is not usable as is. We, therefore, proceeded with a complete rewrite, adapting it to our context. The rewriting was done iteratively, starting with the Level 1 requirements, with a gradual maturity progression towards higher levels based on the risk level. To clarify this point, an initial version of the framework was published based solely on Level 1 requirements.

Even within Level 1, some requirements were reformulated, enriched, or modified into recommendations. We added points deemed missing and brought more clarity where formulations were ambiguous or too strict.

### Ensuring Rules are Actually Applied

This is where the challenges begin. The ASVS provides few concrete indicators to verify the effective implementation of requirements. Therefore, ingenuity is required. We chose to capitalize on the excellent resources of the OWASP, such as the Cheat Sheets or static and dynamic analysis tools (Semgrep, Dependency-Check, etc.).

While awaiting the construction of a truly unified framework to centralize verifications, the only option is to implement a mix of methods, including code reviews, penetration tests, threat modeling, collecting implementation evidence (such as logs or configurations), and scheduled audits at regular intervals.

### Concrete Examples and Minor Issues Encountered

Some requirements are difficult to implement without clarification; verifying against compromised password databases also poses a problem: how to implement it easily? Which API, which dictionary (Rockyou, etc.)?

The rule about passwords between 64 to 128 characters maximum, which we preferred to convert into a recommendation, was deemed too rigid in certain contexts, especially for a very heterogeneous company.

There are also awkward formulations, such as the use of the word "automation" in French, or the term "strong" for a CSRF token, which lacks precision. Overall, everything related to the management of secrets, the securing of CI/CD pipelines, or the integration of DevSecOps remains underdeveloped in the framework.

***Concrete Examples of Adaptation***
7.1.3 - Verify that the application logs relevant security events, including successful and failed authentication events, access control failures, deserialization failures, and input validation failures. (C5, C7) | Reformulated as:
The application logs relevant security events, including successful and failed authentication events, access control failures, deserialization failures, input validation failures, and relevant business events.

8.2.1 - Verify that the application sets sufficient anti-caching headers so that sensitive data is not cached in modern browsers. | Reformulated as:
The application sets sufficient anti-caching headers so that sensitive data is not cached in modern browsers and content delivery networks (CDNs).

I won't list everything, as it would be too long... But here are a few more points below.

The parts about using code structures that limit risky language functions, segregating code sections that handle application secrets, and minimizing RAM storage are handled with a lot of contortion on our part (as these are not explicitly mentioned in the ASVS).

Finally, it would be interesting to have a treatment of AI-related security, which is increasingly present in development processes, or a link (or even associations, as done with NIST) to suitable standards. The same applies to code signing, where valuable insights can be found in experiences such as those of Palantir [How Palantir Secures Source Control | Palantir Blog](https://blog.palantir.com/how-palantir-secures-source-control-105c49079eae), or frameworks such as SLSA [SLSA • Supply-chain Levels for Software Artifacts](https://slsa.dev/). As for threat modeling, it is unfortunately not well-supported, which does not really encourage its adoption (I am referring here to the adoption of threat modeling, which, by the way, should be the subject of a specific post as the topic is so interesting) in the context of using the ASVS as a reference.

## In Conclusion

Despite all these limitations, the ASVS remains an exceptional framework. It is sometimes forgotten that it is a free, open project, constantly enriched by an active community. It allows for the structuring of robust application security approaches, and it is even possible to contribute to its evolution. Moreover, version 5.0 is coming soon. And for those who really want to get involved, now might be the perfect time to participate in the construction of this future version.