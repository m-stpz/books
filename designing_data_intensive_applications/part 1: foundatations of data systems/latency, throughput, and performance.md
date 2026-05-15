# Latency, throughput and performance

## Metrics

1.  Latency: time it takes for a single unit of data to travel from point A to point B, or for a single operation to complete
    - measured in nanoseconds, milliseconds, or seconds
    - ex: the time it takes to drive from linz to vienna

2.  Throughput: the N of actions or data units processed within a timeframe
    - measured in Queries per second (QPS), Transactions per second (TPS)
    - ex: how many cars pass through a tool booth per minute

3.  Performance: a holistic measure of how a system handles workload
    - high performance = low latency + high throughput

## Understanding nano vs. milliseconds

- Computers operate on a clock cycle
- Modern CPU ticks billions of times per second
- Within the computer, things are measured in nanoseconds
- Within a network, we use milliseconds

### Scale: nanoseconds vs. Milliseconds

- 1 millisecond (ms) = 1k microseconds = 1M nanoseconds

A ms is one million nanoseconds

If 1 nanosecond is the width of a human hair:

- 1 millisecond = length of a football field
- 1 second = 100km

## Latency numbers

- To design fast systems, we need to understand the physical reality of hardware

### 1. Hardware and memory latency

Data access is bound by physics

- Moving electrons through a CPU cache is vastly faster than spinning a magnetic platter on an HDD

- L1/L2 cache access: 0.5 - 4 ns (insanely fast, on the CPU chip)
- Main memory (RAM) access: ~100ns (fast, but order of magnitudes slower than CPU cache)
- Solid State Drive (SSD) I/O: ~0.1 - 0.2 ms (100k - 200k ns): SSDs are electronic, eliminating mechanical seek times
- Hard disk drive (HDD): ~1 - 10 ms (1M - 10M ns): they are slow because a physical read/write must mechanically move to the correct sector on a spinning platter

> Reading from RAM is 1k-2k times faster than reading from a fast SSD, and about 100k times faster than an old-school HDD. This is why caching layers are so critical for high-performance apps

### 2. Network & data exchange latency
