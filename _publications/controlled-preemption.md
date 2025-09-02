---
title: "Controlled Preemption: Amplifying Side-Channel Attacks from Userspace"
collection: publications
excerpt: 'Controlled Preemption studies the responsiveness and fairness of OS thread schedulers, which naturally provides a preemption window where the attacker thread can interleave its execution with a victim thread at a temporally fine-grained level (i.e. single step the victim thread).'
venue: 'ASPLOS'
authors: 'Yongye Zhu, <b><u>Boru Chen</u></b>, Zirui Neil Zhao, Christopher W. Fletcher'
date: 2025-04-03
paperurl: 'https://dl.acm.org/doi/pdf/10.1145/3676641.3715985'
citation: '<a href="#bibtex-controlled-preemption" class="open-popup-link">bibtex</a>'
code: 'https://github.com/FPSG-UIUC/Controlled-Preemption'
---
{% include citations.html %}

Microarchitectural side channels are an ongoing threat in today's systems. Yet, many side-channel methodologies suffer from low temporal resolution measurement, which can either preclude or significantly complicate an attack.

This paper introduces Controlled Preemption, an attack primitive enabling a single unprivileged (user-level) attacker thread to repeatedly preempt a victim thread after colocating with that victim thread on the same logical core. Between preemptions, the victim thread executes zero to several instructions—sufficiently few to enable high-resolution side channel measurements.

The key idea in Controlled Preemption is to exploit scheduler fairness heuristics. Namely, that modern thread schedulers give a thread A the ability to preempt another thread B until a fairness tripwire (signaling that A is starving B) fires. We show how this idea enables hundreds of short preemptions before tripping the fairness tripwire is robust to noise and applies to both the Linux CFS and EEVDF schedulers. We also develop a technique that helps colocate the attacker and victim threads onto the same logical core, an attacker capability overlooked by prior work.

Our evaluation tests Controlled Preemption in the context of several different victim programs, victim privilege levels (inside and outside of Intel SGX) and choices of side channel. In each attack, we demonstrate results that are competitive with prior work but make fewer assumptions (e.g., require only user-level privilege or require fewer colocated attacker threads).