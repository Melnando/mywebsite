---
title: "Adapting Digital Architectures for Efficient Post-Quantum Cryptography"
date: 2024-06-09
draft: false
tags: ["Post Quantum Cryptography", "Hardware Security", "Cybersecurity Research"]
---

As we move towards the quantum era, preparing our digital infrastructure for what lies ahead is not just important, it's essential. Over the past year, I've had the opportunity to contribute to this mission through a research project conducted during my academic exchange at National Taipei University, Taiwan. This work, titled [*"Architectural Adaptations for Post-Quantum Cryptography: A Comprehensive Review of Performance, Power, and Security Implications"*](/files/Architectural_Adaptations_for_PQC.pdf) represents a critical step in aligning future-proof cryptographic theory with real-world implementation.

## Why Post-Quantum Cryptography Matters
As quantum computing technology matures, widely used cryptographic protocols such as RSA and ECC face the risk of becoming obsolete. Algorithms like Shor's and Grover's could potentially render these methods vulnerable, posing a serious threat to everything from banking systems to secure messaging apps.

But the threat isn't just something theoretical or futuristic. Attackers today can intercept and store encrypted data, waiting for the moment quantum computers are powerful enough to decrypt it, “Harvest Now, Decrypt Later”. That means even information we consider safe today could be exposed tomorrow. Intellectual property, confidential business records, diplomatic cables. Anything encrypted under vulnerable schemes is at risk in the long term.

Post-Quantum Cryptography (PQC) aims to solve this challenge by developing algorithms that are secure against quantum attacks, while still being viable on current digital infrastructure. However, most discussions focus on the mathematical side of these algorithms. My work focused on something more practical: what are the implications of implementing these cryptographic solutions efficiently and securely on actual hardware?

## My Research Goals
The core objective of this study was to assess how different hardware architectures—such as FPGAs, ASICs, and hybrid systems—can adapt to the specific needs of PQC. We examined three primary aspects:

Performance: How fast can these systems encrypt, decrypt, sign, or verify?

Power Efficiency: Are these designs sustainable for low-power devices like IoT sensors?

Security: How resilient are they against side-channel attacks and other emerging threats?

We drew from real-world implementations and performance metrics to evaluate trade-offs and limitations. A particular focus was given to lattice-based cryptography, one of the most promising families of PQC algorithms.

## Key Insights and Takeaways
One of the most surprising discoveries was the vast trade-off between security and efficiency. For example, while ASICs offer superior performance and energy savings, they lack the adaptability of FPGAs, especially during this transitional phase of PQC standardization.

Here are a few key insights from the research:

FPGAs are ideal for prototyping and exploring different security configurations, thanks to their reconfigurability.

ASICs shine in energy efficiency and performance, but they are harder to update as PQC standards evolve.

Hybrid systems that blend classical and quantum-resistant algorithms offer a transitional solution, albeit with increased complexity and power consumption.

There is a lack of standardized benchmarking frameworks, which makes it difficult to compare results across platforms. This is a significant gap in current research.

## What This Means for the Future
The migration to PQC is not just about replacing algorithms, it’s about rethinking the entire architecture supporting secure communication. From my perspective as a cybersecurity and IoT engineering student, this work lays the groundwork for more secure and scalable cryptographic hardware, especially for constrained environments like embedded systems and IoT.

As part of the Cyber Campus working group in Paris, I continue to contribute to efforts helping organizations transition smoothly to PQC. Whether it's through writing technical guides or conducting research, I’m committed to bridging the gap between emerging cryptographic standards and their practical deployment.

## Closing Thoughts
This project was more than an academic exercise. It challenged me to work at the intersection of cryptography, hardware engineering, and cybersecurity, a space where future-proof digital systems are born. I'm excited to keep contributing to this field, and I'm actively looking for opportunities that allow me to do just that.