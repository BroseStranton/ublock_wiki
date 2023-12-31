[[Back to Wiki home|Home]]

***

- [The large power button](#the-large-power-button)
- [The per-site switches](#the-per-site-switches)
- [The number of requests blocked](#the-number-of-requests-blocked)
- [The tools](#the-tools)
- [The number of domains connected](#the-number-of-domains-connected)
- [The overview panel](#the-overview-panel)

***

This is uBlock Origin (uBO)'s popup UI when you click on uBO's icon in the toolbar:

![Popup UI](https://user-images.githubusercontent.com/95879668/161406915-26970fd2-e6b6-4b74-8a34-8704a1942dee.png)

The amount of visible information can be adjusted by clicking on the "More" and "Less" buttons:

![Toggling popup panels](https://user-images.githubusercontent.com/886325/85211186-fd7afd80-b346-11ea-99b6-ca304b867c09.gif)

***

### The large power button

![large blue power button](https://user-images.githubusercontent.com/95879668/161406975-4ad91129-e3ef-4f30-a215-26070eb74582.png)

Click the large power button to turn off uBO **for the current site** (add current site to _Trusted sites_ list). This will be remembered the next time you visit the site.

Alternatively, you can also <kbd>Ctrl</kbd>-click to turn off uBO only for the current page (<kbd>Cmd</kbd>-click on Mac).

For more advanced control, see ["How to mark a website as trusted"](./How-to-mark-a-web-site-as-trusted).

***

### The per-site switches

![Row of per-site switch buttons](https://user-images.githubusercontent.com/95879668/161407196-d2b63633-f7d6-49f6-b1d0-ddb86b46d771.png)

The per-site switches allow you to control some settings on a per-site basis. See [detailed documentation about per-site switches](./Per-site-switches).

***

### The number of requests blocked

![statistics section](https://user-images.githubusercontent.com/95879668/161407269-52821906-3d8b-4296-bbd9-2b5e9c2a5fcb.png)

Shows the number of blocked network requests on the current page. The number of network requests blocked since installation is also displayed. (This is less useful; however, users appreciate this information). The percentage indicates the number of blocked requests out of the total number of requests made.

***

### The number of domains connected

![cropped part of statistics section](https://user-images.githubusercontent.com/95879668/161407375-adf41ed0-2f8b-46ba-8bf5-ba6dce08021d.png)

The number of **distinct** domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have multiple distinct domains which are under the same administrative authority (example 1: `google.com`, `ajax.googleapis.com` and `gstatic.com`, example 2: `wikipedia.org` and `wikimedia.org`).

That said, this statistic may be seen this way: the more distinct domains your browser connects to, the greater the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**:  that of the remote server from which the web page was fetched.

**The higher the number, the higher you are exposing yourself privacy-wise.**

There is a good correlation between the _domains connected_ count and: unneeded page bloat, high privacy exposure, increased likelihood of being the target of data mining.

Example: the web page on <https://www.ibtimes.com/> (which can be read fine in all cases, by the way):

 uBO's mode | turned off | default settings | [default-deny](./Blocking-mode:-medium-mode)
--- | --- | --- | ---
domains connected | ![](https://user-images.githubusercontent.com/95879668/161407839-7b4feb81-cc36-4a02-a9c0-bf1f4972ff28.png) | ![](https://user-images.githubusercontent.com/95879668/161407792-44d68117-f874-4a38-bd4f-6e2ba64e6f03.png) | ![](https://user-images.githubusercontent.com/95879668/161408195-d9bca8a3-036e-4768-98b6-2ac683c33cb0.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, so it could have been worse (except for default-deny)...

***

### The tools

![row of tools buttons](https://user-images.githubusercontent.com/95879668/161408418-d20fc334-8dae-409a-9df9-7cc9bacc33c6.png)

#### Zap an element on the current page

Click the _flash_ icon to enter [element zapper mode](./Element-zapper), which allows you to interactively remove one or more elements on the current page. Removing an element is always temporary, i.e. the removed elements will be back when the page is reloaded.

#### Create a filter for the current site

Click the _eye-dropper_ icon to enter [element picker mode](./Element-picker), which allows you to create a filter by interactively picking an element on a page, thus permanently removing it from the page. The filters created through the element picker are added at the end of your own filter list in the _My filters_ pane in the dashboard.

#### Report an issue with current website
<span name="report-an-issue-on-this-website"></span>

New in [1.39.0](https://github.com/gorhill/uBlock/commit/eccf613edfe480d34cb225dac203d3213f3ef2f7).

The "chat" icon opens the ["Report a filter issue" form](./The-"Report-a-filter-issue"-form), which makes it easy to report filter issues with specific websites to the [`uBlockOrigin/uAssets` issue tracker](https://github.com/uBlockOrigin/uAssets/issues?q=is%3Aissue).

Reporting filter issues requires a [GitHub account](https://github.com/signup), since uBO does not have a home server through which reports could be sent.

The report icon is available only when uBO is enabled on a given site.

#### Open the logger

Click the _list_ icon to open the [logger](./The-logger) in a separate tab. This allows you to inspect real-time network traffic within the browser.

Tip: press the <kbd>Shift</kbd> key while clicking the icon to toggle between opening the logger in a separate window or a separate tab. uBO will remember that setting when you open the logger without the <kbd>Shift</kbd> key.

On mobile devices, the "Open the logger" icon is replaced by the "chat" icon (["Report a filter issue" form](./The-"Report-a-filter-issue"-form)), since it is more likely to be useful on small display devices. [The logger](./The-logger) can always be opened from [the Support pane](./Dashboard:-Support) in [the Dashboard](./Dashboard) (Link in "Filter issues/website is broken" section, in "_The logger_ is the primary tool..." sentence). If you like, you can turn it back on in [advanced settings](https://github.com/gorhill/uBlock/wiki/Advanced-settings#uipopupconfig).

#### Open the dashboard

Click the _gears_ icon to open the uBO [Dashboard](./Dashboard).

***

### The overview panel

Clicking on the "More" button will expand uBO popup panel to the point where it will show you a list with details about requests blocked and domains connected on the page:

![Overview panel expanded](https://user-images.githubusercontent.com/886325/85211429-6794a200-b349-11ea-94cb-998ee36e6d59.gif) <br>Clicking the empty space before a particular domain name or the `all` cell in the first row, will toggle on/off subdomain-level details.

The panel will also be expanded when you enable ["advanced user"](./Advanced-user-features) mode -- this is only for convenience -- it will not close automatically when "advanced user" will be disabled. To hide that panel, just click on the "Less" button to adjust it to show only the information you desire.

The colored bars near the left edge will give you the general overview when network requests to particular hostnames are all blocked (reddish), all were allowed (greenish), or some were blocked some were allowed (yellowish). The more distinct, wider bar denotes the root context - the hostname for which local rules and filters are created.

<span name="the-pluses-and-minuses">The pluses and minuses</span> will give you slightly more information, their number is proportional to the number of requests that were either allowed or blocked:
- `+`, `-`: under 10 network requests were allowed, blocked.
- `++`, `--`: under 100 network requests were allowed, blocked.
- `+++`, `---`: 100 or more network requests were allowed, blocked.

Starting with [1.24.3b7](https://github.com/gorhill/uBlock/commit/d0738c0835338a15683b9dfffd12b670f513c3f1) [canonical name (CNAME) hostnames](https://wikipedia.org/wiki/CNAME_record) are rendered in blue font. The uncloaked entries in the popup panel will also show the related aliases (in smaller characters underneath the canonical names):

![Closeup on domains in overview panel](https://user-images.githubusercontent.com/95879668/161408664-8ba66430-458b-47af-accf-750fdb309219.png)

Unless you are in ["advanced user"](./Advanced-user-features) mode, this panel is read-only and available only for informational purposes.

<details>
<summary><strong>I am an advanced user!</strong></summary>

***

In "advanced user" mode, this panel is fully interactive and can be used for advanced filtering control:

![Overview panel advanced mode](https://user-images.githubusercontent.com/886325/85384714-b3aa3700-b541-11ea-91cd-6e0e2c1aad4c.gif)

Refer to the [_Dynamic filtering_ documentation](./Dynamic-filtering) to learn more about the rules.

After modifying the rules, you can quickly reload the page without leaving the popup by clicking on the reload button appearing in the top-right corner. Click it with <kbd>Ctrl</kbd>, <kbd>Shift</kbd> or <kbd>Cmd</kbd> (Mac) pressed to bypass browser cache.

Click the `all` cell at the top with <kbd>Ctrl</kbd> and <kbd>Shift</kbd> pressed to open the popup panel as a new browser tab, which may be useful for example to capture screenshots.

</details>
