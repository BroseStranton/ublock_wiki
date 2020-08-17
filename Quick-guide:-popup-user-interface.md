[Back to Wiki home](./)

***

- [The large power button](#the-large-power-button)
- [The per-site switches](#the-per-site-switches)
- [The number of requests blocked](#the-number-of-requests-blocked)
- [The tools](#the-tools)
- [The number of domains connected](#the-number-of-domains-connected)
- [The overview panel](#the-overview-panel)

***

This is uBlock's popup UI when you click on uBlock's icon in the toolbar:

![Popup UI](https://user-images.githubusercontent.com/886325/85211176-df150200-b346-11ea-9b9e-e503de699aa0.png)

Amount of visible information can be adjusted by clicking on "More" and "Less" buttons:

![Toggling popup panels](https://user-images.githubusercontent.com/886325/85211186-fd7afd80-b346-11ea-99b6-ca304b867c09.gif)


***

### The large power button

![large blue power button](https://user-images.githubusercontent.com/886325/85211203-1d122600-b347-11ea-8271-a60449a57c8b.png)

Click the large power button to turn off uBlock **for the current site** (a.k.a. _whitelist_ the current site). This will be remembered the next time you visit the site.

Alternatively, you can also <kbd>Ctrl</kbd>-click to turn off uBlock only for the current page (<kbd>Cmd</kbd>-click on Mac).

For more advanced whitelisting control, see ["How to whitelist a web site"](./How-to-whitelist-a-web-site).

***

### The per-site switches

![Row of per-site switch buttons](https://user-images.githubusercontent.com/585534/85226654-a73da700-b3a6-11ea-9c1b-a579981ffdfe.png)

The per-site switches allow you to control some settings on a per-site basis. See [detailed documentation about per-site switches](./Per-site-switches).

***

### The number of requests blocked

![statistics section](https://user-images.githubusercontent.com/886325/85211231-564a9600-b347-11ea-9f5b-ab926c202cb0.png)

This shows the number of network requests uBlock blocked on the current page. Also, less useful (but people like this kind of thing), the number of network requests uBlock blocked since you installed it. The percentage figure tells you how many requests were blocked out of all the requests made.

***

### The number of domains connected

![cropped part of statistics secion](https://user-images.githubusercontent.com/886325/85211255-87c36180-b347-11ea-9d79-81e91b0429db.png)

The number of **distinct** domains with which a network connection was established, out of all connections (established + blocked). The domains are derived using the official [Public Suffix List](https://publicsuffix.org/).

In general, it must be assumed that each distinct domain is managed by a distinct administrative authority. In practice, it is not uncommon to have a multiple distinct domains which are under the same administrative authority (example 1: `google.com`, `ajax.googleapis.com` and `gstatic.com`, example 2: `wikipedia.org` and `wikimedia.org`).

That said, this statistic may be seen this way: the more distinct domains your browser connects to, the greater the privacy exposure.

In a best-case scenario, the number of distinct domains to which a web page connects should be **only one**:  that of the remote server from which the web page was fetched.

**The higher the number, the higher you are exposing yourself privacy-wise.**

There is a good correlation between the _domains connected_ count and: unneeded page bloat, high privacy exposure, increased likelihood of being the target of data mining.

Example: the web page on <http://www.ibtimes.com/> (which can be read fine in all cases, by the way):

 uBlock's mode | turned off | default settings | [default-deny](./Blocking-mode:-medium-mode)
--- | --- | --- | ---
domains connected | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1e.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1d.png) | ![](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/popup-1f.png)
privacy exposure | very high | medium | very low
bloat | ridiculously high | medium | very low

And I had click-to-play enabled in all cases, so it could have been worse (except for default-deny)...

***

### The tools

![row of tools buttons](https://user-images.githubusercontent.com/886325/85211214-331fe680-b347-11ea-960e-5fa943313e67.png)

#### Zap an element on the current page

Click the _flash_ icon to enter [element zapper mode](./Element-zapper), which allows you to interactively remove one or more elements on the current page. Removing an element is always temporary, i.e. the removed elements will be back when the page is reloaded.

#### Create a filter for the current site

Click the _eye-dropper_ icon to enter [element picker mode](./Element-picker), which allows you to create a filter by interactively picking an element on a page, thus permanently removing it from the page. The filters created through the element picker are added at the end of your own filter list in the _My filters_ pane in the dashboard.

#### Open the logger

Click the _list_ icon to open the [logger](./The-logger) in a separate tab. This allows you to inspect real-time network traffic within the browser.

Tip: press the <kbd>Shift</kbd> key while clicking the icon to toggle between opening the logger in a separate window or separate tab. uBO will remember that setting when you open the logger without the <kbd>Shift</kbd> key.

#### Open the dashboard

Click the _sliders_ icon to open uBlock's dashboard.

***

### The overview panel

Clicking on "More" button, will expand uBO popup UI to the point where it will show you table with details about requests blocked and domains connected on the page:

![Overview panel expanded](https://user-images.githubusercontent.com/886325/85211429-6794a200-b349-11ea-94cb-998ee36e6d59.gif)<br>Clicking empty space before particular domain name or the `all` cell in the first row, will toggle on/off subdomain-level details.

The panel will also be expanded when you enable ["advanced user"](./Advanced-user-features) mode -- this is only for convenience -- it will not close automatically when "advanced user" will be disabled. To hide that panel, just click on "Less" button to adjust it to show only information you desire.

The pluses and minuses denote network requests which were either allowed (not blocked) or blocked, respectively for the specific domain/hostname aside which they appear. The number of pluses and minuses are proportional to the number of requests allowed or blocked:
- `+`, `-`: under 10 network requests were allowed, blocked.
- `++`, `--`: under 100 network requests were allowed, blocked.
- `+++`, `---`: 100 or more network requests were allowed, blocked.

Starting with [1.24.3b7](https://github.com/gorhill/uBlock/commit/d0738c0835338a15683b9dfffd12b670f513c3f1) [canonical name (CNAME) hostnames](https://wikipedia.org/wiki/CNAME_record) are rendered in blue font. The uncloaked entries in the popup panel will also show the related aliases (in smaller characters underneath the canonical names):

![Closeup on domains in overview panel](https://user-images.githubusercontent.com/886325/85211664-a297d500-b34b-11ea-82fd-f9fb64189091.png)

Unless you are in ["advanced user"](./Advanced-user-features) mode, this panel is read-only and available only for informational purpose.

<details>
<summary><strong>I am an advanced user!</strong></summary>

***

In "advanced user" mode, the panel is fully interactive and can be used for advanced filtering control:

![Overview panel advanced mode](https://user-images.githubusercontent.com/886325/85384714-b3aa3700-b541-11ea-91cd-6e0e2c1aad4c.gif)

This is UI for [Dynamic filtering](./Dynamic-filtering). Column on the left represents global rules, on the right - local.

![dynamic filtering cells](https://user-images.githubusercontent.com/886325/69888549-c2eb3e00-12ec-11ea-8341-9b0de36e7659.gif)

Each cell has three fields representing [Dynamic filtering actions](./Dynamic-filtering:-rule-syntax#actions):

 - Green - `allow`: matching network request will be allowed.
 - Grey - `noop`: exclude network requests from being subjected to dynamic filtering. 
 - Red -  `block`: matching network request will be blocked.

Rules set by clicking the cells are temporary by default - click the padlock button if you want to make them permanent or eraser to clear them. Pressing <kbd>Ctrl</kbd> (<kbd>Cmd</kbd> on Mac) when setting rules will make them permanent immediately.

Quickly reload the page without leaving the popup by clicking reload button appearing on the right. Click it with <kbd>Ctrl</kbd>, <kbd>Shift</kbd> or <kbd>Cmd</kbd> (Mac) pressed to bypass cache.

> ***
> **Tip:**
>
> Click the `all` cell at the top with <kbd>Ctrl</kbd> and <kbd>Shift</kbd> pressed to open panel as new browser tab.
>
> ***

</details>
