**Note:** Results have been updated with latest Firefox 41 and Chromium 45. The page is the same as the old one (Firefox 35/Chromium 39, [archived here](https://github.com/gorhill/uBlock/wiki/Firefox-version:-benchmarking-memory-footprint-(2015-03-07))), except all figures have been updated using latest browser versions.

***

[![Vim test](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/vim-test-abp-vs-ublock.png)](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/benchmarks/vim-test-abp-vs-ublock.png)<br><sup>Infamous VIM test: ABP 370 MB vs. uBlock 373 MB. Firefox 41 64-bit. On Chromium 45, ABP still suffers memory footprint issues from injecting huge stylesheet in each page and each embedded frames on a page.</sup>

#### Setup

1. Ensure the blocker is the only active extension (to avoid results to be polluted by other extensions)
1. Ensure click-to-play (or whatever equivalent) is enabled before launching the benchmark
1. Select the following filter lists in the benchmarked blockers:
    - EasyList
    - Peter Lowe's Ad server list
    - EasyPrivacy
    - Fanboy's Social Blocking List
    - Malware domain lists
    - ABP-specifics: _"Acceptable ads"_ disabled
    - uBlock-specifics: uBlock's filters enabled (+140 filters), extra malware domains (+1,487 filters)

#### Steps

1. Have the benchmarked blocker enabled and properly setup
1. Have only the "new tab" opened
1. Quit Firefox
1. Launch Firefox
1. Paste <http://news.yahoo.com/> in address bar, wait for page to finish loading
1. Open new tab, paste <http://news.google.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.huffingtonpost.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.cnn.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.nytimes.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.foxnews.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.nbcnews.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.dailymail.co.uk/>, wait for page to finish loading
1. Open new tab, paste <http://www.washingtonpost.com/>, wait for page to finish loading
1. Open new tab, paste <http://www.theguardian.com/>, wait for page to finish loading
1. Open new tab, paste <https://news.ycombinator.com/>, wait for page to finish loading
1. Leave the browser idle for two minutes
1. Open new tab, paste `about:memory`, wait for page to finish loading
1. Firefox: Click _"Minimize memory usage"_ button in _"Free memory"_ section
1. Firefox: Click _Measure_ button in _"Show memory reports"_ section
1. Firefox: Write down _"Explicit Allocations"_ value (see notes below) / Chromium: Write down _Σ_ value

So I did the **exact** above steps for no blocker, ABP, uBlock.

#### Results

- **Firefox**
    - No blocker: **751.22 MB** (reference memory usage)
    - **Adblock Plus** 2.6.10: **639.49 MB** (reference _minus_ 111.7 MB)
    - **uBlock Origin** 1.1.1: **465.86 MB** (reference _minus_ 285.4 MB, ABP _minus_ 173.6 MB)
- **Chromium**
    - No blocker: **1,342.87 MB** (reference memory usage)
    - **Adblock Plus** 1.9.3: **1,525.4 MB** (reference _plus_ 182.5 MB)
    - **uBlock Origin** 1.1.1: **1,110.02 MB** (reference _minus_ 232.9 MB, ABP _minus_ 415.4 MB)

**Important:** You can't compare directly the figures between the browsers -- they are taken using different methodology from one browser to the other. The benchmarks are more to compare the figures for various blockers within the same browser.

#### Notes

Tested on Firefox 41.0 64-bit and Chromium 45.0.2454.85 64-bit on Linux Mint. No other extensions were present.

For Firefox, I chose the _"Explicit Allocations"_  figure because as per Firefox, it is "the single best number to focus on" with regard to memory usage.

Without going into details, hardware is i5 quadcore + 8 GB

If other users feel like repeating the tests, it would be nice just to confirm I got everything right.
