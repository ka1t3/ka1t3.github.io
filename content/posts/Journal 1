+++
date  = 2026-05-15
draft  = false
title  = 'Why only Python and npm for auto-remediation'
tags = ["Supply chain security","Journal"]
+++

# Observation

Some notes on a point i noticed during an assignment. it may seem obvious, but it raises questions for me, and i will probably have more later on.

Recently, i worked on securing Open Source libraries, and more specifically on securing the libraries made available to projects. Working in a large company with thousands of projects, the goal was to establish the first lines of defense to allow projects to consume dependencies with less friction.

There are several ways to enable the use of Open Source dependencies, but generally, in large companies, you will have this kind of setup:

Distribution ---> Consumption (wow, you’re not teaching us anything there)

Actually, it’s very simple.

Public registries such as PyPi, Maven ---> Mirror: [Pulp Project](https://pulpproject.org/help/more/why-pulp/?utm_source=chatgpt.com) or [Nexus Repository](https://www.sonatype.com/products/sonatype-nexus-repository?utm_source=chatgpt.com) or [ProGet](https://inedo.com/proget/features?utm_source=chatgpt.com)

After that, other defense mechanisms may come into play through security plug-ins in iDEs, SCA tools in the Ci/CD pipeline, signature and signature verification, etc.
But that is not the subject of this short note.

At the registry level, we do not really have control. But starting from the mirror, we begin to see different security mechanisms, notably before entering the mirror (in proxy mode) and once the library has been downloaded into the mirror.

As part of this expertise task i was carrying out, i had a debate with several developers from one department regarding the necessity of having this kind of proxy.

And to summarize, my position was:

"Yeah, how’s your baby doing? Ah great, growing so fast... few moments later... So, regarding the necessity, we can already answer this question with the universal response of iT professionals: ‘it depends.’

More seriously, it depends on many parameters such as your governance (yes yes, how the company is structured around this topic), your cyber maturity, your exposure to risk (for example: are these dependencies used in your critical assets? what is the scale of your SBOM?), your human/financial resources, your security controls (your tools), etc."

But above all, we discussed a point i was not aware of, and thanks to that, i now make sure to go deeper into things (and i recommend doing the same when benchmarking tools).

Dev: "Ok, one of the points we find important with the proxy firewall feature of the solution [i won’t name the solution, i’m not advertising haha], is the auto-remediation functionality that blocks vulnerable dependencies and automatically proposes a non-vulnerable alternative instead."

Me: "Of course, that’s very convenient. Give me some time to evaluate that before taking this criterion into account."

While digging into the documentation, i saw that it only works with npm and pip. Knowing that the developers in the company i work for use several languages (with quite a lot of exoticism), how do projects that do not use these technologies handle this?

Can we say that if we manage to establish alternatives for these other technologies, then we might as well also distribute them for npm and pip? So maybe it is not that important after all? And therefore no longer a decisive argument when choosing a proxy?

To explore a few directions and answer the question of how others handle this:
ask developers to pin their dependencies (which is a good practice), scanning in the iDE | scanning in the mirror | scanning in the pipeline (SCA tool) | dependency signing. The [SLSA framework](https://slsa.dev/?utm_source=chatgpt.com) provides quite a lot of good practices in that regard (even though they are not easy to implement).

Anyway, this was a short note around a conversation about Open Source dependencies.
