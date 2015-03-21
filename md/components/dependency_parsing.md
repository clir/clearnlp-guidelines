# Dependency Parsing

Our dependency parser uses a transition-based, non-projective parsing algorithm coupled with bootstrapping. Our parsing algorithm is guaranteed to run in O(*n*) for projective parsing and in an expected linear time for non-projective parsing. Our dependency parser processes about 15K tokens per second on an Intel Xeon 2.30GHz machine and shows state-of-the-art accuracy for greedy parsing. See [how to run command-line tools](md/quick_start/command_line_tools.md) for more details about decoding and training.

* [Getting the Most out of Transition-based Dependency Parsing](http://aclweb.org/anthology-new/P/P11/P11-2121.pdf), Jinho D. Choi, Martha Palmer, Proceedings of the 49th Annual Meeting of the Association for Computational Linguistics: Human Language Technologies (ACL:HLT'11), 687-692, Portland, Oregon, 2011.
* [Transition-based Dependency Parsing with Selectional Branching](http://aclweb.org/anthology/P/P13/P13-1104.pdf), Jinho D. Choi, Andrew McCallum, Proceedings of the 51st Annual Meeting of the Association for Computational Linguistics (ACL'13), 1052-1062, Sofia, Bulgaria, 2013.
