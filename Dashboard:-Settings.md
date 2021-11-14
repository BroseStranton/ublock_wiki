- Back to [[Wiki home|Home]]
- Back to [Dashboard](./Dashboard)

***

![Figure 1](https://user-images.githubusercontent.com/585534/92238602-92da5800-ee87-11ea-96ca-042fd9a6a7f7.png)

## General

### Make use of context menu where appropriate

If checked, this gives permission for uBlock to add items in the [browser's context menu](./The-context-menu) which are meant to improve convenience.

***

### Color-blind friendly

Currently mostly useful for users who checked _"I am an advanced user"_ (see below).

***

### Enable cloud storage support

See [Cloud storage](./Cloud-storage) documentation.

***

### I am an advanced user

If you check this, this will enable [uBlock's dynamic filtering](./Dynamic-filtering), and the dynamic filtering pane will become available from uBlock's popup UI.

Unchecking this disables the dynamic filtering. And the dynamic filtering pane in the popup UI will no longer be available.

_Advanced user_ mode also gives access to the [advanced settings](./Advanced-settings) (normally hidden), and enables the ability to filter [behind-the-scene network requests](./Behind-the-scene-network-requests).

You should avoid playing with advanced features and settings unless [you understand fully what you are doing](./Advanced-user-features).

***

## Privacy

### Disable pre-fetching

Checking this will disable prefetching in your browser. When prefetching is enabled, the browser _can_ still establish connections to remote servers even if the resource from these remote servers are meant to be blocked by uBlock.

This prevents the browser from bypassing uBlock's filtering engine before establishing connections to remote servers.

Mozilla's [_"Link prefetching FAQ"_](https://developer.mozilla.org/docs/Web/HTTP/Link_prefetching_FAQ):

> **Privacy implications** Along with the referral and URL-following implications already mentioned above, prefetching will generally cause the cookies of the prefetched site to be accessed.

Google's [_"Make webpages load faster"_](https://support.google.com/chrome/answer/1385029):

> If you turn this setting on in Chrome, websites (and any of their embedded resources) that are prerendered or prefetched may set and read their own cookies as if you had visited them before -- even if you don’t visit the prerendered or prefetched pages after all.

#### **IMPORTANT NOTE:**
On Chromium 51 and above (including browsers based on Chromium 51 and above), this setting is completely unreliable, as it does not cause DNS lookups, preconnections and prefetches to be reliably blocked, because Chromium allows web pages to override that user setting. For details, see:
- <https://github.com/gorhill/uBlock/issues/3219>
- <https://bugs.chromium.org/p/chromium/issues/detail?id=785125>
- Example of different behavior with Firefox: <https://github.com/uBlockOrigin/uBlock-issues/issues/435>

***

### Disable hyperlink auditing

Checking this will prevent hyperlink auditing. _Hyperlink auditing_ is best summarized as "phone home" feature (or more accurately "phone anywhere") meant to inform one or more servers of which links you click on (and when). The details are well explained [here](https://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/) and the case of why such feature is harmful to users is well argued [here](https://www.wilderssecurity.com/threads/major-browsers-to-prevent-disabling-of-click-tracking-privacy-risk.415381/#post-2822723).

***

### Prevent WebRTC from leaking local IP address

Option removed from desktop browsers in [uBlock Origin v1.38](https://github.com/uBlockOrigin/uBlock-issues/issues/1723).

Browsers now obfuscate LAN addresses by mDNS:

- Firefox: ["Enable mDNS hostname obfuscation"](https://bugzilla.mozilla.org/show_bug.cgi?id=1588817)
- Chromium: ["mDNS service for IP handling in WebRTC"](https://bugs.chromium.org/p/chromium/issues/detail?id=878465)

Option is still available in Android Firefox, because obfuscation is still not implemented there: ["Support mDNS hostname obfuscation on Android"](https://bugzilla.mozilla.org/show_bug.cgi?id=1581947)

<details>
<summary>Details</summary>

![highlighted Prevent WebRTC from leaking local IP address preference](https://cloud.githubusercontent.com/assets/585534/8344622/0ce20cc4-1ab2-11e5-8f46-a0a387c91d63.png)

Background info: [STUN IP Address requests for WebRTC](https://github.com/diafygi/webrtc-ips)

Test case: [Prevent WebRTC from leaking local IP address](./Prevent-WebRTC-from-leaking-local-IP-address)

Keep in mind that this feature is to prevent **leakage** of your non-internet-facing IP adresses. The purpose of this feature is not to hide your current internet-facing IP address -- so be cautious to not misinterpret the results of the tests above. For example, if you use a VPN, your internet-facing IP address is that of the VPN, so your ISP-provided IP address should not be visible to outside world with this setting checked. However, if you are not behind any VPN or proxy, your ISP-provided IP address will be visible regardless of this setting.

**Caveats:**
- Chromium-based browsers: 
   - the feature works only on version 42 and above.
- Firefox: 
   - due to differences in handling of network connections by different browsers, before version [1.18.12](https://github.com/gorhill/uBlock/commit/977178bef23c7711a050181be979a4668bfebcfb) WebRTC was completely disabled if Firefox was not configured to use proxy. Related issue: [#3009](https://github.com/gorhill/uBlock/issues/3009#issuecomment-329798696)

</details>

***

### Block CSP reports

**Enabled by default in Firefox** in [1.31.3rc1](https://github.com/gorhill/uBlock/commit/bc9b8a13300d7a6de93d0632369be15b05b7646e) to mitigate fingerprinting attempts described in [LiCybora/NanoDefenderFirefox#196](https://github.com/LiCybora/NanoDefenderFirefox/issues/196).

You can block network requests made as a result of your browser reporting Content Security Policy violations ("CSP reports") to a remote server (which can be 3rd-party to the site where the violation occurred).

**Important:** disabling CSP reporting is not something which will break web pages, the purpose of CSP reporting is _strictly_ a development tool for web sites.

Consider this excerpt from [Reporting API / Privacy Considerations](http://wicg.github.io/reporting/#privacy) (my emphasis):

> 8.6. Disabling Reporting
> 
> [...]
> 
> That said, it can’t be the case that this general benefit be allowed to take priority over the ability of a user to individually opt-out of such a system. Sending reports costs bandwidth, and potentially could reveal some small amount of additional information above and beyond what a website can obtain in-band ([NETWORK-ERROR-LOGGING], for instance). **User agents MUST allow users to disable reporting with some reasonable amount of granularity in order to maintain the priority of constituencies espoused in [HTML-DESIGN-PRINCIPLES].**

There is currently no way to easily toggle CSP reporting in either Chromium or Firefox. This per-site switch is to address this shortcoming.

Note that as opposed to all other network requests, behind-the-scene network requests which are actual CSP reports will also be filtered out according to this setting. So if you globally disable CSP reporting in uBO, this will also apply to behind-the-scene network requests.

Note that the blocking of CSP reports is implemented as a per-site switch internally in uBO, so this means that an advanced user could create rules in the _My rules_ pane in the dashboard to allow a more granular control of the blocking of CSP reports. For example:

    no-csp-reports: example.com false

The above rule means CSP reports would not be blocked on `example.com` when CSP reports are blocked globally. The reverse will also work:

    no-csp-reports: example.com true

The above rule means CSP reports would be blocked on `example.com` when CSP reports are not blocked globally.

***

### Uncloak canonical names

![higlighted Uncloak canonical names preference](https://user-images.githubusercontent.com/886325/111153280-0a551680-8592-11eb-9d18-058e5b845bd5.png)

From uBO 1.34.0 and above. Before 1.34.0, this was an [advanced setting](./Advanced-settings) since [1.25.0](https://github.com/gorhill/uBlock/releases/tag/1.25.0).

Enable/disable the uncloaking of canonical names -- enabled by default.

For background information see [_"What's CNAME of your game? This DNS-based tracking defies your browser privacy defenses"_](https://www.theregister.com/2021/02/24/dns_cname_tracking/).

The setting will be disabled on platforms not supporting this feature. It's currently supported only on Firefox.

In some edge cases, it might be necessary to disable this setting to prevent network-related issues. For example, [_"Pages load slowly when uBlock Origin is installed"_](https://bugzilla.mozilla.org/show_bug.cgi?id=1694404#c5), which occurred when funneling network requests through a proxy.

**Important note when using extension-based proxy service:** Extension-based proxy services are often done on-the-fly through a [browser API](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/proxy/onRequest), and in such case uBO's own DNS queries to uncloak canonical names will **NOT** be caught and proxied by an extension-based proxy service. So you may want to disable this setting when using an extension-based proxy service.

***

## Default behavior

Please see: ["Per site switches"](./Per-site-switches)

***

## Backup/restore section

![buttons](https://user-images.githubusercontent.com/585534/80806433-af3c5000-8b88-11ea-9f8c-bbd9fb3df9d7.png)

The bottom-most section is for you to easily backup/restore/reset all settings in uBlock.

It's done by saving text file to location specified by your browser.

It is suggested you backup all your settings regularly.
