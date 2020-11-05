# Benchmarking with drill

### Install drill and run

The easiest way right now is to install with [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html):

```
cargo install drill
drill --benchmark benchmark.yml --stats
```

or download the source code and compile it:

```
git clone git@github.com:fcsonline/drill.git && cd drill
cargo build --release
./target/release/drill --benchmark benchmark.yml --stats
```

**Note:** You will need to install `libssl-dev` and `pkg-config` packages.

## Features

This is the list of all features supported by the current version of `drill`:

- **Concurrency:** run your benchmarks choosing the number of concurrent iterations.
- **Multi iterations:** specify the number of iterations you want to run the benchmark.
- **Ramp-up:** specify the amount of time it will take `drill` to start all iterations.
- **Delay:** introduce controlled delay between requests.
- **Dynamic urls:** execute requests with dynamic interpolations in the url, like `/api/users/{{ item }}`
- **Dynamic headers:** execute requests with dynamic headers.
- **Interpolate environment variables:** set environment variables, like `/api/users/{{ EDITOR }}`
- **Request dependencies:** create dependencies between requests with `assign` and url interpolations.
- **Split files:** organize your benchmarks in multiple files and include them.
- **CSV support:** read CSV files and build N requests fill dynamic interpolations with CSV data.
- **HTTP methods:** build request with different http methods like GET, POST, PUT, PATCH, HEAD or DELETE.
- **Cookie support:** create benchmarks with sessions because cookies are propagates between requests.
- **Stats:** get nice statistics about all the requests. 
- **Thresholds:** compare the current benchmark performance against a stored one session and fail if a threshold is exceeded.

## Command line interface

Full list of cli options, which is available under `drill --help`

```
drill 0.7.0
HTTP load testing application written in Rust inspired by Ansible syntax

USAGE:
    drill [OPTIONS] --benchmark <benchmark>

FLAGS:
    -h, --help       Prints help information
        --no-check-certificate    Disables SSL certification check. (Not recommended)
        --relaxed-interpolations    Do not panic if an interpolation is not present. (Not recommended)
    -s, --stats      Shows request statistics
    -q, --quiet      Skips output of individual request statistics
    -n, --nanosec    Shows statistics in nanoseconds
    -V, --version    Prints version information

OPTIONS:
    -b, --benchmark <benchmark>    Sets the benchmark file
    -c, --compare <compare>        Sets a compare file
    -r, --report <report>          Sets a report file
    -t, --threshold <threshold>    Sets a threshold value in ms amongst the compared file

```
