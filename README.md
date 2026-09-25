# Modern C++ Order Book Simulator

A high-performance, low-latency Limit Order Book (LOB) simulator implemented in modern C++23.

## 🚀 Key Features

- **High-Performance Matching Engine:** Implements an efficient matching algorithm using `std::map` and `std::list` to maintain price-time priority.
- **Thread-Safe Architecture:** Utilizes modern C++ concurrency primitives (`std::mutex`, `std::condition_variable`, `std::scoped_lock`) to ensure data integrity across multiple threads.
- **Real-time Level Aggregation:** Tracks Market-By-Price (MBP) data efficiently for real-time order book snapshots.
- **Automated Order Pruning:** Features a background thread dedicated to managing `GoodForDay` order lifecycles based on system time.

## 📊 Supported Order Types

The simulator supports a wide range of industry-standard order instructions:

| Order Type               | Description                                                                          |
| :----------------------- | :----------------------------------------------------------------------------------- |
| **GoodTillCancel (GTC)** | Rests in the book until fully filled or explicitly cancelled.                        |
| **FillAndKill (FAK)**    | Matches as much as possible immediately; any remaining quantity is cancelled.        |
| **FillOrKill (FOK)**     | The entire order must be filled immediately, or the whole order is cancelled.        |
| **GoodForDay (GFD)**     | Automatically pruned from the book at the end of the trading session (16:00).        |
| **Market Order**         | Executes immediately at the best available price(s) until the quantity is satisfied. |

## 🏗 How to Build

```bash
# Build the simulator
clang++ -std=c++23 main.cpp OB.cpp -o orderBookTutorial

# Run the simulator
./orderBookTutorial
```
