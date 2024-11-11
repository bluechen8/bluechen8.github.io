---
title: "Peek-a-Walk: Leaking Secrets via Page Walk Side Channels"
collection: publications
excerpt: 'Peek-a-Walk is a microarchitectural side-channel attack that leaks secrets from the page walk process. This amplifies an attacker’s bit leakage capabilities (up to 42 of the 64 secret bits) in scenarios where secrets are dereferenced microarchitecturally.'
venue: 'IEEE S&P (Oakland)'
authors: 'Alan Wang, <b><u>Boru Chen</u></b>, Yingchen Wang, Christopher W. Fletcher, Daniel Genkin, David Kohlbrenner, Riccardo Paccagnella'
date: 2025-05-12
citation: '<a href="#bibtex-peek-a-walk" class="open-popup-link">bibtex</a>'
---
{% include citations.html %}

Microarchitectural side-channel attacks are an insidious
threat to program security. An emerging class of
these attacks constructs gadgets that dereference the contents
of data memory directly. This is caused by optimizations,
such as speculative execution and data-memory prefetching,
that can guess (incorrectly) that the program is performing
a pointer chase. In theory, this is devastating for security,
as dereferencing a secret seemingly leaks it over memorybased
side channels, e.g., through the cache. In practice, it
is not. Since most secrets do not look like valid pointers, their
dereference typically fails and does not leak anything.

In this paper, we introduce the page walk side channel
(PWSC), a new attack that can leak information even when
an invalid pointer is dereferenced. In particular, given a 64-
bit secret that passes the address canonicality check, PWSC
can leak all remaining bits of the secret except for the loworder
6 bits, without making any assumptions on what these
bits look like. We demonstrate how PWSC amplifies leakage
in scenarios exploiting speculative execution and data-memory
prefetching. For speculative execution, we show that PWSC,
combined with Intel’s LAM feature, can be exploited to leak
nearly all of physical memory and that even without LAM,
PWSC can be used to leak Dilithium secret keys. For datamemory
prefetching, we reverse engineer the semantics of
Intel’s data-memory dependent prefetcher (DMP) and show
how this DMP and PWSC can be combined to break security
in an intra-process sandbox setting.