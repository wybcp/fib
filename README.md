# Recursive Fibonacci Benchmark using top languages on Github

Top 10: JavaScript, Java, Python, Ruby, Php, C++, C#, C, Go [reference](http://www.techworm.net/2016/09/top-10-popular-programming-languages-github.html)

Others: Crystal, Rust, Swift, Mono, Elixir, Perl, R, Julia

This code performs a recursive fibonacci to the 46th position with the result of 2,971,215,073.

All tests are run on:
 - iMac (Retina 5K, 27-inch, Late 2015)
 - OS: macOS High Sierra 10.13.6
 - Processor: 3.2 GHz Intel Core i5
 - Memory: 16 GB 1867 MHz DDR3

Last benchmark was ran on September 25th, 2018

## Natively compiled, statically typed (optimized code)

| Language        | Time, s  | Compile                              | Run          |
|-----------------|----------|--------------------------------------|--------------|
| Go (mem)        |  0.005*  | `go build -o fib fib-mem.go`         | `time ./fib` |
| C++ (constexpr) |  0.086*  | `g++-8 -O3 -o fib fib-constexpr.cpp` | `time ./fib` |

**NOTE:**

The C++ (constexpr) is using a `constexpr` which optimizes the recursive call to a constant. The Go (mem) is using memoization. Go 1.11 is also faster than previous versions.

These solutions break the benchmark since they don't perform the same internal tasks as the other languages. It demonstrates that all benchmarks will have some caveat. The C++ (constexpr) was provided by [Ole Christian Eidheim](https://gitlab.com/eidheim).  The Go (mem) was provided by [Alexander F. Rødseth](https://github.com/xyproto).

## Natively compiled, statically typed

| Language | Time, s | Compile                           | Run          |
|----------|---------|-----------------------------------|--------------|
| Crystal  |  5.300  | `crystal build --release fib.cr`  | `time ./fib` |
| C++      |  5.751  | `g++ -O3 -o fib fib.cpp`          | `time ./fib` |
| Nim      |  6.030  | `nim compile -d:release fib.nim`  | `time ./fib` |
| C        |  6.258  | `gcc -O3 -o fib fib.c`            | `time ./fib` |
| Rust     |  6.567  | `rustc -O fib.rs`                 | `time ./fib` |
| Swift    | 10.307  | `swiftc -O -g fib.swift`          | `time ./fib` |
| Go       | 10.492  | `go build fib.go`                 | `time ./fib` |

## VM compiled bytecode, statically typed

| Language  | Time, s | Compile          | Run                 |
|-----------|---------|------------------|---------------------|
| Java      |  7.447  | `javac Fib.java` | `time java Fib`     |
| C# (Mono) | 11.323  | `mcs fib.cs`     | `time mono fib.exe` |
| C#        | 72.486  | `dotnet restore` | `time dotnet run`   |

## VM compiled before execution, mixed/dynamically typed

| Language | Time, s  | Run                  |
|----------|----------|----------------------|
| Dart     | 10.467   | `time dart fib.dart` |
| Julia    | 10.799   | `time julia fib.jl`  |
| Node     | 18.874   | `time node fib.js`   |
| Elixir   | 69.101   | `time elixir fib.exs`|

NOTE: These languages include compilation time which should be taken into consideration when comparing.

## Interpreted, dynamically typed

| Language | Time, s  | Run                   |
|----------|----------|-----------------------|
| Ruby     |  195.601 | `time ruby fib.rb`    |
| Php      |  206.346 | `time php fib.php`    |
| Python   |  502.036 | `time python fib.py`  |
| Python3  |  758.681 | `time python3 fib.py` |
| Perl     | 1133.131 | `time perl fib.pl`    |
| R        | 1796.495 | `time r -f fib.r`     |


## Versions

- go version go1.11 darwin/amd64
- g++-8 (Homebrew GCC 8.2.0) 8.2.0
- crystal Crystal 0.26.1 (2018-08-27) LLVM: 6.0.1
- g++ Apple LLVM version 10.0.0 (clang-1000.11.45.2)
- gcc Apple LLVM version 10.0.0 (clang-1000.11.45.2)
- nim Nim Compiler Version 0.18.0 [MacOSX: amd64]
- swiftc Apple Swift version 4.2 (swiftlang-1000.11.37.1 clang-1000.11.45.1)
- rustc 1.29.0
- javac 10.0.1
- mcs Mono C# compiler version 5.12.0.226
- dotnet 2.1.4
- dart Dart VM version: 2.0.0 (Fri Aug 3 10:53:23 2018 +0200)
- julia version 0.6.3
- node v9.4.0
- elixir Elixir 1.7.3 (compiled with Erlang/OTP 21)
- ruby 2.5.1p57 (2018-03-29 revision 63029)
- php 7.1.16 (cli) (built: Apr  1 2018 13:14:42)
- python 2.7.15
- python3 3.7.0
- perl 5, version 26, subversion 2 (v5.26.2)
- r version 3.5.0 (2018-04-23)

## Caveats

[Fibonacci Benchmark](https://crystal-lang.org/2016/07/15/fibonacci-benchmark.html)
