### uBlock Origin (uBO)'s required (Chromium) permissions

uBO's required permissions are the same as those of [Privacy Badger](https://privacybadger.org/), except that Privacy Badger requires one extra permission, `cookies`. These are uBO's required permissions:

    "permissions": [
        "contextMenus",
        "dns",
        "privacy",
        "storage",
        "tabs",
        "unlimitedStorage",
        "webNavigation",
        "webRequest",
        "webRequestBlocking",
        "http://*/*",
        "https://*/*"
    ],

[`"privacy"`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/privacy) is the only permission added in [version 0.9.8.2](https://github.com/gorhill/uBlock/releases/tag/0.9.8.2). All the others were there since when uBO was first published (except for `"contextMenus"` which was added at some point, to support blocking elements from within the context menu).

The `privacy` permission is needed for uBO to be able to disable the setting "Prefetch resources to load pages more quickly". This will ensure no connection is opened at all for blocked requests: It's for your protection privacy-wise.

This is Privacy Badger required permissions:

    "permissions": [
        "contextMenus",
        "cookies",
        "privacy",
        "storage",
        "tabs",
        "unlimitedStorage",
        "webNavigation",
        "webRequest",
        "webRequestBlocking",
        "http://*/*",
        "https://*/*"
    ],

### "Access your data on all web sites"

Since [first version](https://github.com/gorhill/uBlock/blob/b5fdac90539b19a0db8f36ea537bd150edb4d9c8/manifest.json).

- To be able to inspect all net requests so that they can be canceled if needed.
    - Only on http- and https-based URL addresses.

See code:

- [browser.webRequest](https://github.com/gorhill/uBlock/search?q=%22browser.webRequest%22&type=Code)

---

### "Access your tabs and browsing activity"

Since [first version](https://github.com/gorhill/uBlock/blob/b5fdac90539b19a0db8f36ea537bd150edb4d9c8/manifest.json).

This is necessary to be able to:

- Create new tabs (when you click on a filter list, to see its content)
- To detect when a tab is added or removed:
- To update badge
- To flush from memory internal data structures
- To find out which tab is currently active (to fill popup menu with associated stats/settings)
- To be able to inject the element picker script
- To implement the popup-blocker

See code:

- [browser.tabs](https://github.com/gorhill/uBlock/search?q=%22browser.tabs%22&type=Code)
- [browser.webNavigation](https://github.com/gorhill/uBlock/search?q=%22browser.webNavigation%22&type=Code)

---

### "Access IP address and hostname information"

Related permission: `dns`.

Since [version 1.25.0](https://github.com/gorhill/uBlock/releases/tag/1.25.0) (Firefox 60+ only).

This warning is triggered by the `dns` permission, which allows using the [`browser.dns` API](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/dns). The purpose is for uBO to gain the [ability to reveal the canonical name of aliased hostnames](https://github.com/uBlockOrigin/uBlock-issues/issues/780).

Note that even without this permission, uBO can see the IP address and hostname information, through the [`browser.webRequest API`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/API/webRequest) which uBO already requires.

**Important:** the statement "IP address" refers to the IP address of the servers to which your browser connects, **NOT** your specific IP address. uBO has **no access to** (and no need to know) **your specific IP address**.

<sub>There is a [Firefox issue](https://bugzilla.mozilla.org/show_bug.cgi?id=1617861) regarding the confusing wording of the permission. Firefox 74 Beta 9 no longer asks for this permission.</sub>

---

### "Store unlimited amount of client-side data"

Related permission: [`unlimitedStorage`](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions/manifest.json/permissions#unlimited_storage).

Since [first version](https://github.com/gorhill/uBlock/blob/b5fdac90539b19a0db8f36ea537bd150edb4d9c8/manifest.json).

This permission is necessary to allow uBO to use more than 5 MB of storage. uBO uses client-side storage to save the assets downloaded from remote servers (filter lists and other assets), the compiled version of those assets and the selfie representation of various assets (for efficient launch time). The storage used by uBO is shown at the bottom of the _Settings_ pane in the dashboard. Without this permission, uBO would not be able to use more than 5 MB, which is not enough for uBO to function properly.

---

### "Change your privacy-related settings"

Since [version 0.9.8.2](https://github.com/gorhill/uBlock/commit/e65c2939757f09db646d277b82da8690aaf3adbc) ([release notes](https://github.com/gorhill/uBlock/releases/tag/0.9.8.2)).

This is necessary to be able to:

- Disable _"Prefetch resources to load pages more quickly"_
    - This will ensure no TCP connection is opened **at all** for blocked requests: **It's for your own protection privacy-wise.**<sup>[1]</sup>
    - For pages with lots of blocked requests, this will remove overhead from page load (if you did not have the setting already disabled).
    - When uBO blocks a network request, the expectation is that it blocks **completely** the connection, hence the new permission is necessary for uBO to do **truthfully** what it says it does.
- Disable [hyperlink auditing/beacon](https://www.wilderssecurity.com/threads/hyperlink-auditing-aka-a-ping-and-beacon-aka-navigator-sendbeacon.364904/) (0.9.8.5)

uBO's primary purpose is to block **network connections**, not just data transfer. Not blocking the connection while just blocking the data transfer would mean uBO is lying to users. So this permission will stay, and sorry for those who do not understand that it allows uBO to do its intended job more thoroughly<sup>[2]</sup>. A blocker that does not thoroughly prevent connections is not a real blocker.

**Privacy Badger also requires the same permissions.** I want uBO to also serve privacy-minded users first.

If _prefetching_ had been disabled by default, this new permission would not be needed, but _prefetching_ is unfortunately enabled by default, and under _Privacy_ heading, which is itself hidden by default under _"advanced settings"_, and even at this point, you would still have to dig to find out the [negative side effects of prefetching](https://en.wikipedia.org/wiki/Link_prefetching#Issues_and_criticisms) (related: [Deceptive Design](https://www.deceptive.design/)).

![c](https://cloud.githubusercontent.com/assets/585534/7914528/924b9314-0845-11e5-8012-f67e4b1814cd.png)

Also, the benefits of _prefetching_ are probably marginal, and in the context of a blocker, the benefits could be negative, since a lot of useless connections would be made, just to be discarded after the browser find out the requests won't be made anyway. So do not fall for the _"loss of major performance boost"_ claim I read elsewhere, this is just a silly and baseless claim.

**Edit:** actually, prefetching is worse than I first thought, I had tested that it was just a connection issue, but [as per Google (archive.org copy)](https://web.archive.org/web/20150905193636/https://support.google.com/chrome/answer/1385029):

> If you turn this setting on in Chrome, websites (and any of their embedded resources) that are prerendered or prefetched may set and read their own cookies as if you had visited them before -- even if you don’t visit the prerendered or prefetched pages after all.

or [per Mozilla](https://developer.mozilla.org/en-US/docs/Glossary/Page_prediction):

>Although browser page prediction and prediction services enable faster page loads, they consume additional bandwidth. Also, pre-loaded websites and embedded content can set and read their cookies as if they were visited even if they weren't.

See code:

- [browser.privacy.network](https://github.com/gorhill/uBlock/commit/e65c2939757f09db646d277b82da8690aaf3adbc)

<sub>[1] Merely opening a TCP connection leaks your IP address to the remote server -- this is incompatible with an extension whose primary purpose is to **completely** prevent connections to remove server, not just merely prevent the transfer of data. For instance, [see what can be found](https://browserleaks.com/ip) with a just that connection being established (IP, OS Fingerprinting, IP Address Location).</sub>

<sub>[2] In version 0.9.8.3, there will be [a setting to allow re-enabling prefetching](https://github.com/gorhill/uBlock/issues/274), default will still be to disable it though.
</sub>