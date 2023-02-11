# Ck Hosting Benchmark Script
Simple benchmark script to estimate Linux server performance using fio, iperf3, & Geekbench

## How to Run

```
curl -sL benchmark.ck-hosting.com | bash
```

or 

```
wget -qO- benchmark.ck-hosting.com | bash
```

This script has been tested on Linux distributions such as CentOS 6+, Debian 8+, Fedora 30, and Ubuntu 16.04+. It is designed to run without the need for external dependencies or elevated privileges.

### Flags (Skipping Tests, Reducing iperf Locations, Geekbench 4, etc.)

By default, the script runs all three tests described in the next section below. In the event that you wish to skip one or more of the tests, use the commands below:

```
curl -sL benchmark.ck-hosting.com | bash -s -- -flags
```

* `-b` this option forces use of pre-compiled binaries from repo over local packages
* `-f`/`-d` this option disables the fio (disk performance) test
* `-i` this option disables the iperf (network performance) test
* `-g` this option disables the Geekbench (system performance) test
* `-h` this option prints the help message with usage, flags detected, and local package (fio/iperf) status
* `-r` this option reduces the number of iperf locations (Online.net/Clouvider LON+NYC) to lessen bandwidth usage
* `-4` this option overrides the Geekbench 5 performance test and runs a Geekbench 4 test instead
* `-9` this option runs the Geekbench 4 test in addition to the Geekbench 5 test
* `-j` this option prints a JSON representation of the results to the screen
* `-w <filename>` this option writes the JSON results to a file using the file name provided
* `-s <url>` this option sends a JSON representation of the results to the designated URL(s) (see section below)

Options can be grouped together to skip multiple tests, i.e. `-fg` to skip the disk and system performance tests (effectively only testing network performance).

**Geekbench License Key**: A Geekbench license key can be utilized during the Geekbench test to unlock all features. Simply put the email and key for the license in a file called _geekbench.license_. `echo "email@domain.com ABCDE-12345-FGHIJ-57890" > geekbench.license`

### Security Notice

This script is dependent on external executables for the completion of performance testing. The network test (iperf3) and disk test (fio) make use of binary files that were compiled by the author using the [Holy Build Box](https://github.com/phusion/holy-build-box) environment to guarantee binary compatibility. This was done to standardize output, provide support for both 32-bit and 64-bit architectures, eliminate the need for additional prerequisite installations, and for various other reasons. The system test involves downloading a Geekbench tarball, extracting it, and running the resulting binary. Please use this script with caution as you would with any script available on the internet. Detailed information about the binary files, including the compilation process, can be found in the [README page](bin/README.md) located in the bin directory.

## Acknowledgements

This script is a modified version of the YABS (https://yabs.sh/) benchmark script which was inspired by several great benchmarking scripts out there, including, but not limited to, [bench.sh](https://bench.sh/), [nench.sh](https://github.com/n-st/nench), [ServerBench](https://github.com/K4Y5/ServerBench), among others. Members of the [HostedTalk](https://hostedtalk.net), [LowEndSpirit](https://talk.lowendspirit.com), and [LowEndTalk](https://www.lowendtalk.com) hosting-related communities play a pivotal role in testing, evaluating, and shaping this script as it matures.
