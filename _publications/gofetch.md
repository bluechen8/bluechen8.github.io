---
title: "GoFetch: Breaking Constant-Time Cryptographic Implementations Using Data Memory-Dependent Prefetchers"
collection: publications
excerpt: 'GoFetch is a microarchitectural side-channel attack that can extract secret keys from constant-time cryptographic implementations via data memory-dependent prefetchers (DMPs). We show that DMPs are present in many Apple CPUs and pose a real threat to multiple cryptographic implementations, allowing us to extract keys from OpenSSL Diffie-Hellman, Go RSA, as well as CRYSTALS Kyber and Dilithium.'
venue: 'USENIX Security'
highlight: 'Pwnie Award -- Best Cryptographic Attack'
authors: '<b><u>Boru Chen</u></b>, Yingchen Wang, Pradyumna Shome, Christopher W. Fletcher, David Kohlbrenner, Riccardo Paccagnella, Daniel Genkin'
date: 2024-08-14
paperurl: 'https://gofetch.fail/files/gofetch.pdf'
citation: '<a href="#bibtex-gofetch" class="open-popup-link">bibtex</a>'
code: 'https://github.com/FPSG-UIUC/GoFetch'
---
{% include citations.html %}

Microarchitectural side-channel attacks have shaken the foundations of modern processor design. The cornerstone defense against these attacks has been to ensure that security-critical programs do not use secret-dependent data as addresses. Put simply: do not pass secrets as addresses to, e.g., data memory instructions. Yet, the discovery of data memory-dependent prefetchers (DMPs)---which turn program data into addresses directly from within the memory system---calls into question whether this approach will continue to remain secure.

This paper shows that the security threat from DMPs is significantly worse than previously thought and demonstrates the first end-to-end attacks on security-critical software using the Apple m-series DMP. Undergirding our attacks is a new understanding of how DMPs behave which shows, among other things, that the Apple DMP will activate on behalf of any victim program and attempt to "leak'' any cached data that resembles a pointer. From this understanding, we design a new type of chosen-input attack that uses the DMP to perform end-to-end key extraction on popular constant-time implementations of classical (OpenSSL Diffie-Hellman Key Exchange, Go RSA decryption) and post-quantum cryptography (CRYSTALS-Kyber and CRYSTALS-Dilithium).

For more information, please check our [website](https://gofetch.fail).