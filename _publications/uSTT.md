---
title: "µSTT: Microarchitecture Design for Speculative Taint Tracking"
collection: publications
excerpt: 'µSTT analyzed the hardware complexity of the state-of-the-art hardware-based Spectre mitigation--Speculative Taint Tracking (STT)--identifying two key challenges: (1) logic delay of the taint propagation; (2) area overhead from instruction delaying. Two new mechanisms, Age Matrix and impede micro-op, are proposed to address these challenges.'
venue: 'ICCD'
authors: '<b><u>Boru Chen</u></b>, Rutvik Choudhary, Kaustubh Khulbe, Archie Lee,  Adam Morrison, Christopher W. Fletcher'
date: 2025-11-10
paperurl: '/files/ustt.pdf'
citation: '<a href="#bibtex-ustt" class="open-popup-link">bibtex</a>'
code: 'https://github.com/FPSG-UIUC/uSTT'
---
{% include citations.html %}

Speculative execution attacks exploit malicious speculation to leak sensitive data via microarchitectural covert channels.
Speculative Taint Tracking (STT) is a state-of-the-art hardware mechanism that blocks such threats by tainting data flowing from speculative loads, untainting data once all its dependencies are not speculative, and delaying instructions that create covert channels until their inputs are untainted.
However, STT's hardware feasibility remains unclear due to a lack of detailed hardware cost analysis.

This paper presents the first in-depth hardware cost analysis of STT and identifies two key challenges: (1) the logic delay of taint propagation, which grows with rename width, and (2) area overhead from instruction delaying, which requires expensive CAM-style logic to enforce speculation safety.

To address these, we propose a new microarchitecture for STT, called µSTT.
µSTT is based on two new mechanisms.
First, the *Age Matrix* is a shallow taint propagation circuit that removes 85% of the logic delay overhead of prior STT designs and only adds 36% more area at the default rename width of 8.
Second, the *impede micro-op* implements instruction delaying by leveraging existing RAW dependency tracking.
Together, these contributions make STT more practical by reducing hardware cost and maintaining strong security with only 5% more performance overhead relative to the original STT.