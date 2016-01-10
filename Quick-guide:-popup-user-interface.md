[Back to Wiki home](https://github.com/gorhill/uBlock/wiki)

***

- [The title bar](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-title-bar)
- [The large power button](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-large-power-button)
- [The number of requests blocked](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-requests-blocked)
- [The number of domains connected](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-number-of-domains-connected)
- [The site-based switches](https://github.com/gorhill/uBlock/wiki/Quick-guide:-popup-user-interface#the-site-based-switches)

***

This is uBlock's popup UI when you click on uBlock's icon in the toolbar:

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1.png)

***

#### The title bar

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1a.png)

Click the title bar of the popup to go to uBlock's dashboard.

***

#### The large power button

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1b.png)

Click the large power button to turn off uBlock **for the current site** (a.k.a. _whitelist_ the current site). This will be remembered the next time you visit the site.

Alternatively, you can also <kbd>Ctrl</kbd>-click to turn off uBlock only for the current page (<kbd>command ⌘</kbd>-click on Mac).

For more advanced whitelisting control, see ["How to whitelist a web site"](https://github.com/gorhill/uBlock/wiki/How-to-whitelist-a-web-site).

***

#### The number of requests blocked

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1c.png)

This shows the number of network requests uBlock blocked on the current page. Also, less useful (but people like this kind of thing), the number of network requests uBlock blocked since you installed it. The percentage figure tells you how many requests were blocked out of all the requests made.

Click the _eye-dropper_ icon to enter [element picker mode](https://github.com/gorhill/uBlock/wiki/Element-picker), which allows you to create a filter by interactively picking an element on a page, thus permanently removing it from the page.

Click the _list_ icon to open the [network request logger](https://github.com/gorhill/uBlock/wiki/The-logger) in a separate tab. This allows you to inspect real-time network traffic within the browser.

***

#### The number of domains connected

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png)

The number of **distinct** domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have a multiple distinct domains which are under the same administrative authority (example 1: `google.com`, `ajax.googleapis.com` and `gstatic.com`, example 2: `wikipedia.org` and `wikimedia.org`).

That said, this statistic may be seen this way: the more distinct domains your browser connects to, the greater the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**:  that of the remote server from which the web page was fetched.

**The higher the number, the higher you are exposing yourself privacy-wise.**

There is a good correlation between the _domains connected_ count and: unneeded page bloat, high privacy exposure, increased likelihood of being the target of data mining.

Example: the web page on <http://www.ibtimes.com/> (which can be read fine in all cases, by the way):

 uBlock's mode | turned off | default settings | [default-deny](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering)
--- | --- | --- | ---
domains connected | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1e.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1f.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, so it could have been worse (except for default-deny)...

***

#### The site-based switches

![Popup UI](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1g.png)

The per-site switches allow you to control some settings on a per-site basis. See [detailed documentation about per-site switches](https://github.com/gorhill/uBlock/wiki/Per-site-switches).