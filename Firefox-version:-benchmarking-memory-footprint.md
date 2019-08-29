**Note:** Results have been updated with latest Firefox 52 and Chrome 59. Previous benchmarks:
- Firefox 41/Chromium 45: [see revision](./Firefox-version:-benchmarking-memory-footprint/0e022fdbeff93ee22890533ad33f8dd07c4c1efa)
- Firefox 35/Chromium 39: [see revision](./Firefox-version:-benchmarking-memory-footprint/4dddff63af59f69b6301a82a790619099e2ac2ef)

#### Setup

1. Ensure the blocker is the only active extension (to avoid results to be polluted by other extensions)
1. Ensure click-to-play (or whatever equivalent) is enabled before launching the benchmark
1. How blockers were configured:
    - uBlock Origin: default settings.
    - Adblock Plus: EasyList + EasyPrivacy, minus "acceptable ads".

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

- **Firefox 52** (benchmark results updated on April 3rd, 2017)
    - Two measurements needed with FF 52.0: Main Process + Web Content
    - No blocker: 175 MB + 1,397 MB = **1,572 MB** (reference memory usage)
    - **Adblock Plus** 2.8.2: 241 MB + 626 MB = **867 MB** (reference _minus_ 705 MB)
    - **uBlock Origin** 1.11.4: 176 MB + 488 MB = **664 MB** (reference _minus_ 908 MB, ABP _minus_ 203 MB)
- **Chrome 59** (benchmark results updated on April 3rd, 2017)
    - No blocker: **1,615 MB** (reference memory usage)
    - **Adblock Plus** 1.13.2: **1,253 MB** (reference _minus_ 362 MB)
    - **uBlock Origin** 1.11.4: **832 MB** (reference _minus_ 783 MB, ABP _minus_ 421 MB)

**Important:** You can't compare directly the figures between the browsers -- they are taken using different methodology from one browser to the other. The benchmarks are more to compare the figures for various blockers within the same browser.

#### Notes

No other extensions were present.

For Firefox, I chose the _"Explicit Allocations"_  figure because as per Firefox, it is "the single best number to focus on" with regard to memory usage.

Without going into details, hardware is i5 quadcore + 8 GB

If other users feel like repeating the tests, it would be nice just to confirm I got everything right.
