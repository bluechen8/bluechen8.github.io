---
title: "Evict+Skip: A High-Bandwidth, Non-Shared-Page Cache Covert Channel Attack"
excerpt: "Streamline, a paper published in ASPLOS 2021, introduced an asynchronous framework to construct high-bandwidth covert-channels. However, it required that the sender and the receiver had to share the virtual memory, which made it less general. In order to figure this out, we proposed a brand new high-bandwidth covert-channel, which leveraged the directory conflicts of non-inclusive machine and the universal feature of Prime+Probe Attack."
collection: project
---

[Streamline](https://memlab.ece.gatech.edu/papers/ASPLOS_2021_1.pdf), a paper published in ASPLOS 2021, introduced an asynchronous framework to construct high-bandwidth covert-channels. However, it required that the sender and the receiver had to share the virtual memory, which made it less general. In order to figure this out, we proposed a brand new high-bandwidth covert-channel named Evict+Skip, which leveraged the directory conflicts of non-inclusive machine and the universal feature of Prime+Probe Attack.

Intuitionally, as for unfastening the constrain of the shared page table, blending a universal method named Prime+Probe into the framework of Streamline came to mind. However, this method lost the most of bandwidth, for much more addresses should be accessed.

Enlightened by the work of [directory attack](http://iacoma.cs.uiuc.edu/iacoma-papers/ssp19.pdf), we discovered huge potential of non-inclusive machine orchestrating universal covert-channel attacks with even higher band-width. (1) Instead of kicking the target to the DRAM, we generated directory-conflicts cache sets to booststrap cache replacement between L2 cache and LLC. In this way, the latency of single access was eliminated. (2) In addition, the associativity of the directory is usually less than the LLC, which resulted in fewer number of cache access. Both (1) and (2) contributed to a boost of the transmission rate.

Through sweeping various parameter settings, we obtained the Accuracy-Bandwidth diagram (Figure 1) revealing that Evict+Skip could achieve 0.6x bandwidth of Streamline with the optimal parameter setting on the same non-inclusive machine. And both of them reached high accuracy (Evict+Skip: 99+%, Streamline: 96+%).

<div align="center">
<img src='/images/EvictSkip.png' width="600" height="400" alt="EvictSkip" align=center />
</div>

<center>Figure 1: Evict+Skip vs Streamline</center>

To further improve the bandwidth, we explored the parallelism of memory access, such as pipelining the access to the disparate LLC banks. Meanwhile, the theoretical analysis had disclosed that Evict+Skip could achieve similar bandwidth as or even higher bandwidth than Streamline.

