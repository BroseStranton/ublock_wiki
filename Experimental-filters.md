The [experimental filters](https://github.com/gorhill/uBlock/blob/master/assets/ublock/experimental.txt) are filters being evaluated for inclusion in uBlock Origin's default set of filters. They are being evaluated to assess whether they cause undue web page breakages.

The _Experimental_ filters are disabled by default, enable only if you want to help evaluate/fine tune these filters.

If you find web pages broken by one of these filters, please open a [GitHub issue](https://github.com/gorhill/uBlock/issues) with all the proper details<sup>[1]</sup> **if and only if** you are able to confirm that one of the experimental filter is causing the web page breakage.

There are currently two experimental filters, which are block-then-redirect filters, to block the following resources:

- `googletagservices.com/tag/js/gpt.js`: Normally [not blocked by EasyPrivacy](https://github.com/gorhill/uBlock/wiki/Blocking-mode#easy-mode).
    - The effect of blocking `googletagservices.com` by default can be appreciated by looking at how often it occurred as a 3rd-party in [_Easy_ blocking mode](https://github.com/gorhill/uBlock/wiki/Blocking-mode) (which is default uBO settings).
    - Specifically, this would bring the number of 3rd parties hit during the benchmark for the _Easy_ blocking mode from 512 to 466.
- `www.google-analytics.com/ga.js`: Normally blocked by uBO, but blocking this resource has sometimes led to page breakage, so exception filters have been required. By forcing a redirect to a neutered version, the goal is to reduce page breakage while avoiding the need to create an exception filter for some sites ([example](https://github.com/gorhill/uBlock/issues/1081#issuecomment-165501960)).

Note that these two experimental filters use the `important` filter option, so they will bypass any existing exception filters.

***

[1] As per [CONTRIBUTING](https://github.com/gorhill/uBlock/blob/master/CONTRIBUTING.md).