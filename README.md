# fddt
Concurrent error detection : comparison between 2  code based error detection strategies implementations PARITY VS BERGER CODE

Monte Carlo comparison of two code-based concurrent error detection
schemes on a 16-bit datapath: single-bit parity and Berger code
(zero-count). 100000 trials per error model, fixed seed.
How to setup:
  Python 3.8+, standard library only.
Explaining:
  Encodes a random word with both schemes, injects an error, recomputes
  the check symbols from the corrupted word, counts a detection when
  they differ from the stored ones. Four error models: single flip,
  double flip, 2-4 bit burst, 1-4 bit unidirectional (all 1->0).
Results:
  parity overhead : 1 check bit  (6.25%)
  berger overhead : 5 check bits (31.25%)

  error model      parity det. berger det.
  single               100.00%     100.00%
  double                 0.00%      49.55%
  burst                 33.19%      70.70%
  unidirectional        50.39%     100.00%
Conclusions|:
  Parity catches exactly odd-weight errors, cheap at 1 bit. Berger
  catches all unidirectional errors regardless of multiplicity, at 5x
  the redundancy. Parity for SEU-dominated, area-tight designs; Berger
  when the fault model is unidirectional and full coverage of that
  class is required.
