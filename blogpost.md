# **Beyond Brittle Alerts: A Detection Template for the Modern SOC**

In the world of cybersecurity, the quality of our detections is the bedrock of our defense. Yet, how often do we encounter alerts that are brittle, lack context, or are impossible for a junior analyst to triage at 2 AM? We create rules that fire on a specific file hash or a command-line string, only to have them bypassed by an adversary who simply recompiles their tool or adds an extra space. This endless cat-and-mouse game leads to alert fatigue and, ultimately, missed threats.

We needed a better way. We needed a system that forces us to build resilient, behavior-based detections from the ground up.

This is why we developed a new **Detection Analytic Template**. This isn't just another documentation standard; it's a framework for thinking. It's a guide that transforms the art of detection engineering into a repeatable science, ensuring that every analytic we create is robust, well-documented, and immediately actionable.

This template is designed to be the best friend of the **Detection Engineer**, the **SOC Analyst**, and the **Playbook Creator**.

You can find the template and contribute to its development on our GitHub repository: [th3r3d/bm-template](https://github.com/th3r3d/bm-template).

## **The Philosophy: Standing on the Shoulders of Giants**

Our approach isn't built in a vacuum. It is deeply inspired by the groundbreaking work of two key sources in the cybersecurity community:

1. **Jared Atkinson (SpecterOps):** His extensive writings on **Capability Abstraction** and the "On Detection: Tactical to Functional" series have been transformative. Atkinson teaches us that we must stop chasing tools and start detecting the underlying *operations*—the fundamental actions an adversary performs on an operating system. An attacker can easily change their tool, but it's much harder to change the sequence of API calls or system interactions required to achieve their goal. You can explore his work on his [Medium page](https://medium.com/@jaredcatkinson).  
2. **MITRE's Summiting the Pyramid Project:** Building on David Bianco's "Pyramid of Pain," this project provides a rigorous, two-dimensional model for evaluating the **robustness** of a detection. It forces us to ask: "How much 'pain' does this detection cause the adversary?" A rule based on a file hash (Level 1\) is trivial to bypass. A rule based on an invariant behavior of a technique (Level 5\) forces the attacker to completely change their TTPs. You can read more about this at the [Center for Threat-Informed Defense](https://ctid.mitre.org/projects/summiting-the-pyramid).

Our template ingrains these philosophies into the detection engineering lifecycle, forcing us to ask the right questions at every step.

## **Why This Template is Your Best Friend**

This template bridges the gap between different functions within a security team, ensuring that everyone is speaking the same language.

#### **For the Detection Engineer:**

It provides a structured, scientific process. No more "gut feeling" detections.

* **The Hypothesis:** You start by articulating a clear, testable hypothesis about adversary behavior.  
* **Robustness Scoring:** The "Summiting the Pyramid" section forces you to objectively score your analytic's resilience. You can no longer create a Level 1 or 2 detection without consciously acknowledging its limitations.  
* **Forced Documentation:** The process of filling out the template *is* the documentation. By the time you've written the logic, you've already documented the TTPs, data sources, and potential false positives.

#### **For the SOC Analyst:**

It delivers context, not just an alert.

* **The Manual Playbook:** The "Triage & Investigation Steps" section is a clear, step-by-step guide. It tells the analyst what the alert means, what to check first, and how to investigate further. This is critical for reducing Mean Time to Respond (MTTR) and preventing alert fatigue.  
* **Understanding the "Why":** The analyst can instantly see the hypothesis and MITRE ATT\&CK mapping, understanding not just *what* happened, but *why* it's a potential threat.

#### **For the Playbook Creator & SOAR Engineer:**

It provides a blueprint for automation.

* **The SOAR Playbook:** Section 6 is a dedicated, machine-readable playbook. It explicitly defines enrichment actions (like getting user details or checking a hash reputation), automated triage logic, and potential containment steps.  
* **Bridging Detection & Response:** This section directly translates detection logic into automated response actions, closing the gap and speeding up the entire incident lifecycle.

## **Comparison to the ADS Framework**

The **Alerting and Detection Strategy (ADS)** framework from Palantir was a pioneering effort in bringing rigor to the detection writing process, and it has served the community well. Our template seeks to build upon its strong foundation.

**Pros of ADS:**

* It was one of the first frameworks to formalize the need for detailed documentation.  
* Its narrative sections like "Technical Context" are excellent for capturing detailed background information.

**Where Our Template Evolves:**

* **Structured Robustness Scoring:** ADS relies on the engineer's prose to describe why a detection is good. Our template requires a *quantitative score* based on the Summiting the Pyramid framework, making the assessment of robustness a non-negotiable, standardized step.  
* **Action-Oriented Playbooks:** Where ADS has a general "Response" section, our template splits this into a **Manual Playbook** for analysts and a structured **SOAR Playbook** for automation. This makes it far more actionable for modern, automation-heavy SOCs.  
* **Hypothesis-Driven Core:** Our template places the **Hypothesis** at the forefront, reinforcing the scientific method in the detection process.  
* **Integrated Evasion-Aware Testing:** The "Validation" section explicitly requires testing against different implementation "synonyms" (functional, procedural, etc.), directly embedding Jared Atkinson's concepts of capability abstraction into the testing phase. This pushes engineers to validate the *behavioral* aspect of the detection, not just that it catches one specific tool.

In short, while ADS was a fantastic starting point for documentation, our template is a framework for **engineering**. It guides thought, enforces resilience, and is built for the realities of a modern, automated SOC.

## **Conclusion**

A detection analytic is more than just a query; it's a shared piece of knowledge that captures our understanding of a threat. It's a contract between the engineer who builds it and the analyst who responds to it.

This template is our attempt to make that contract as clear, robust, and effective as possible. By forcing us to think about TTPs, score our own work, and plan for response from the outset, it elevates the craft of detection engineering. It helps us move away from chasing ephemeral indicators and toward building a resilient defense that causes real pain for the adversary.

We encourage you to explore the template on our [GitHub repository](https://github.com/th3r3d/bm-template), adapt it for your own environment, and join the conversation on building better detections.
