uBlock Origin (uBO) comes with a logger, which gives the ability to inspect what uBO is doing with network requests and DOM elements, whether something is blocked or allowed, and which filter, if any, matched a network request or DOM element. This logger is _unified_, meaning it will display _everything_ uBO does as it occurs.

The logger is the tool of choice to see, understand, diagnose and fix the functioning of uBO.

To access the logger, click on the _list_ icon of uBO's popup UI:

![list icon](https://user-images.githubusercontent.com/95879668/199077749-4d624b9b-271e-401c-bb43-922f3c17d1c7.png)

The request logger will open in a new tab (which was moved to its own window below):

![logger window](https://user-images.githubusercontent.com/886325/62732907-c00acb80-ba25-11e9-8206-76d7f071657e.png)

The color of a row hints at how the resource was filtered:
- No color: The request for the resource was allowed to go through because it matched no filter/rule.
- Purple: The request for the resource was modified by one of the ["Modifier filters"](./Static-filter-syntax#modifier-filters).
- Red: The request for the resource was canceled (`--`) because of a block filter/rule.
- Gray: The request for the resource was allowed to go through ["Dynamic filtering"](./Dynamic-filtering) engine, because of [`noop` rule](./Dynamic-filtering:-quick-guide#noop-rules).
- Green: The request for the resource was allowed to go through (`++`) because it matched a filter/rule whose purpose is to bypass a matching block filter/rule.
- Yellow:
    - A DOM element which was blocked by a cosmetic filter; OR
    - A blocked request for a resource was redirected (`<<`) to a local, "neutered" replacement resource.
    - A defuser scriptlet was injected into the page (`+js(...)`)
- Blue font: Uncloaked [canonical name (CNAME)](https://wikipedia.org/wiki/CNAME_record) hostname.


Particular columns indicate:
1. Timestamp of the event
1. For blocked/allowed/hidden resources, the column will contains the responsible filter. For redirection, local resource used as replacement to the blocked network request.
1. Action taken by uBO:
    - `--` blocked request
    - `++` allowed by exception filter/rule
    - `<<` redirection to neutered resource
1. Context identifier (domain) in which the filter is evaluated
1. _Partyness_ of the network request related to main document, and optionally after comma, _partyness_ of the request in relation to embedded subdocument
    - `1` for the first-party requests, from current page domain (the one you see in address bar)
    - `3` for third-party requests, from other domains
    - `0` for _tabless_ requests (behind the scene, requests not assigned to any opened page)
1. HTTP request method
1. Type of request
1. Address of the resource on which filter was applied

Time, Filter/Rule, Context and Partyness columns can be disabled in [Settings dialog](#settings-dialog)


Take note that the network request logger in uBO is a forward-looking logger: this means only future requests can be logged.

In the spirit of efficiency, uBO will log entries **IF AND ONLY IF** the logger is opened. Otherwise, if the logger is not opened, no CPU/memory resources are consumed by uBO for logging purpose.

#### Tip
Hold the <kbd>Shift</kbd> key while clicking the "Open the logger" icon to toggle between opening the logger in a separate window or in a separate tab. uBO will remember that setting when you open the logger next time, without having to hold the <kbd>Shift</kbd> key.

***

- [Page selector](#page-selector)
- [Reload](#reload)
- [DOM inspector](#dom-inspector)
- [Accessing popup UI of a specific page](#accessing-popup-ui-of-a-specific-page)
- [Expand](#expand)
- [Void log entries](#void-log-entries)
- [Clear](#clear)
- [Pause the logger](#pause-the-logger)
- [Filtering the logger output](#filtering-the-logger-output)
- [Filter statistics](#filter-statistics)
- [Export dialog](#export-dialog)
- [Settings dialog](#settings-dialog)
- [Finding from which list(s) a static filter originates](#finding-from-which-lists-a-static-filter-originates)
- [Source code viewer](#source-code-viewer)
- [Creating filters](#creating-filters)
    - [Dynamic URL filtering rules](#dynamic-url-filtering-rules)
    - [Static network filters](#static-network-filters)
    - [Temporary exception filters](#temporary-exception-filters)

***

### Components

***

#### Page selector

![page selector drop-down list](https://user-images.githubusercontent.com/886325/62740200-6ca17900-ba37-11e9-9a76-d64ef10b761d.png)

The drop-down selector is to display log entries which are related to a specific page. This will hide from view all log entries which are not related to the selected page. By selecting _All_ again, all log entries will be displayed again.

Note in the figure above the entry named _"Tabless"_: selecting this entry allows to show network requests not associated with any tab. _Tabless_ request are denoted in the log by font shadow effect and `0` in "Context" column (fifth).

***

#### Reload

![reload button](https://user-images.githubusercontent.com/886325/62740268-affbe780-ba37-11e9-9144-cdc4c52370aa.png)

The big reload button aside the page selector is to force a reload of the content of the selected page. This button is enabled only for when a specific page is selected.

Click it with <kbd>Ctrl</kbd>, <kbd>Shift</kbd> or <kbd>Cmd</kbd> (Mac) to bypass cache.

***

#### DOM inspector

![code icon](https://user-images.githubusercontent.com/886325/62740302-c4d87b00-ba37-11e9-8d11-2fe9e1fc4d5d.png)

Complementary tool to the element picker.

Please read more on dedicated page: ["DOM inspector"](./DOM-inspector)

***

#### Accessing popup UI of a specific page

![uBO icon](https://user-images.githubusercontent.com/886325/62734523-863bc400-ba29-11e9-82ce-0bf4211ea7d3.png)

By clicking this button you can access the [[popup UI|Quick-guide:-popup-user-interface]] of a specific tab.

***

#### Expand

![arrow down icon](https://user-images.githubusercontent.com/886325/62740377-f7827380-ba37-11e9-8be0-fef923ada0d3.png)

By default log entries in the logger are collapsed so as to take no more than one line. Some log entries however might be truncated as a result. This button can be used to expand all entries vertically to larger number of lines (configurable in [Settings dialog](#settings-dialog), default 4) making them more visible.

***

#### Void log entries

![x icon](https://user-images.githubusercontent.com/886325/62740422-13861500-ba38-11e9-911b-6d377afe71f8.png)

With "All" selected in "Page selector" if you close a tab for which there are entries in the logger, these entries will be marked as _void_, i.e. they will be faded out, to indicate the tab for these entries does not exist anymore.

The `X` button in the toolbar allows you to remove those void entries from the logger.

***

#### Clear

![rubber icon](https://user-images.githubusercontent.com/886325/62740450-2c8ec600-ba38-11e9-9f6b-e6b113cd8ebe.png)

This is to clear the logger, to remove all entries from the selected/filtered context (Ars Technica tab in this example).

_Tabless_ request (faded out) may also appear in current page log. To clear them out, click Clear icon second time.

***

#### Pause the logger

![pause icon](https://user-images.githubusercontent.com/886325/62740475-46c8a400-ba38-11e9-9930-25af7d205abe.png)

***

#### Filtering the logger output

![expression picker drop down interface](https://user-images.githubusercontent.com/886325/62740615-97d89800-ba38-11e9-9b4c-869fac0d0129.png)

You can visually filter entries in the logger using filter expressions. Expressions can be chosen from expression picker, available by hovering mouse cursor over filter input box. Log entries which do not match _all_ filter expressions will be hidden from view. 

![expression picker arrow down](https://user-images.githubusercontent.com/886325/62762761-2aedee00-ba8a-11e9-94cf-048f3751d145.png)

Clicking on arrow in the filtering input box deactivates expression picker.

![funnel icon](https://user-images.githubusercontent.com/886325/62762820-4d800700-ba8a-11e9-9c5a-186dd3cd5ee4.png)

Funnel icon toggles on/off current filter expression.

Filter can also be entered manually. Supported syntax:

- Enter `foo` to only show entries which have a string `foo`.
- Enter `|foo` to only show entries which have a field starting with `foo`.
    - Tip: use `|--` to show only entries which were blocked (`--` may work for the most part, but there could be false positives).
- Enter `foo|` to only show entries which have a field ending with `foo`.
- Enter `|foo|` to only show entries which have exactly a field with `foo`.
- Prefix any expression with `!` to reverse the meaning of the expression.
    - `!foo` means display only entries which do not have the string `foo` in it.
    - `!|--` means display only entries which were **not** blocked.
- When more than one filter expression appear, a logical _and_ between the expressions is implied.
- You can _or_ multiple expressions together:
    - `css || image` means display entries which match either `css` or `image`.
    - `xhr || other |http:` means display entries which match either `xhr` or `other` and have a field which starts with `http:`.
    - `!css || image` means display entries which do not match either `css` or `images` (equivalent to `!css !image` really).
    - Warning: With _or_'ed expressions, the _not_ (`!`) operator can only apply to the resulting _or_'ed expression.
- Enclose expression in slash `/` characters to treat it as Regular Expression.

Examples:

- `!|-- facebook`: show only non-blocked entries with the string `facebook` in it.
- `|xhr google`: show only entries of type `XMLHttpRequest` with the word `google` in it.
- `!|image !|css`: show only entries which are not of type `image`, neither `css`.

***

#### Filter statistics

[Disabled temporarily](https://github.com/gorhill/uBlock/commit/5a5523c0b53697f816d942a1b3a712980bc77b93).

<details>
<summary>Details</summary>

![chart icon](https://user-images.githubusercontent.com/886325/62764319-e19f9d80-ba8d-11e9-8ada-7725e1ac9dae.png)

The current implementation reports statistics for all static filters, and the presentation/feature set is intentionally minimal: *Do not open issues about this.* It's still a work in progress and it will be worked on slowly and thoughtfully over time and as time allows.

Pausing the logger will not pause the collation of filter hit statistics, thus it is possible to lower the logger overhead by pausing logger output without losing filter hit collation.

</details>

***

#### Export dialog

![clipboard icon](https://user-images.githubusercontent.com/886325/62764465-3fcc8080-ba8e-11e9-9388-46a73baf7332.png)

![export dialog](https://user-images.githubusercontent.com/886325/62765195-e1a09d00-ba8f-11e9-83c4-f2197ed811a3.png)

Allows to easily export log to the system clipboard in format compatible with various discussion boards.

***

#### Settings dialog

![gear icon](https://user-images.githubusercontent.com/886325/62764519-625e9980-ba8e-11e9-839c-cf10fe0a29b8.png)

![settings dialog](https://user-images.githubusercontent.com/886325/62765348-3fcd8000-ba90-11e9-82d3-32745a41edf4.png)

***

#### Finding from which list(s) a static filter originates

You can find out from which filter list(s) a static filter originates, by simply clicking on it (or in any other highlighted column):

![mouse over log in active column](https://user-images.githubusercontent.com/886325/62765676-e6198580-ba90-11e9-89b7-1a2d02dc98b4.png)

![filter details dialog](https://user-images.githubusercontent.com/886325/62765805-32fd5c00-ba91-11e9-8fd6-709279411319.png)

- Clicking on filter list name will open assets viewer with content of that list.
- Home icon next to the filter name will bring you to the support site for that list.

***

#### Source code viewer

New in [1.47.3b4](https://github.com/gorhill/uBlock/commit/33c437f99f30daa3172b097ba35ae662239f6013).

You can use the logger to view beautified and syntax-highlighted source code of HTML/CSS/JS/xhr resources when clicking the link in a logger entry. This should help save time when investigating solutions to filter issues.

The goal is to make it easier for filter list authors to investigate filter-related issues.

When on the logger, you should click on the arrow at the end of the link, it will automatically open the source code viewer.

![the arrow to open the source code viewer](https://user-images.githubusercontent.com/17685483/223643864-5ae1e2c2-3aae-4e55-a252-6a08799faad7.png)

![source code viewer](https://user-images.githubusercontent.com/17685483/223644130-3fdde8bc-ae36-4140-bbec-ae0e6d5d8edd.png)

***

#### Creating filters

![mouse over log in active column](https://user-images.githubusercontent.com/886325/62770372-309fff80-ba9b-11e9-8847-89c858e3db63.png)

Clicking on the highlighted cell of the log entry will give you access to the filtering tools dialog (modal), from where you can easily create dynamic URL filtering rules or just standard static filters.

***

##### Dynamic URL filtering rules

![URL rule tab in details dialog](https://user-images.githubusercontent.com/886325/62770688-cdfb3380-ba9b-11e9-916c-03dc1bf9643a.png)

Point-and-click to create dynamic URL filtering rules. These rules are temporary by default - click the padlock button if you want to make them permanent. Pressing <kbd>Ctrl</kbd> (<kbd>Cmd</kbd> on Mac) when setting rules will make them permanent immediately. Useful to find out which network requests need to be blocked or allowed on a page in order, to fix a broken page, or to further block more useless resources from a page.

See [_"Overview of uBlock's network filtering engine: details"_](./Overview-of-uBlock's-network-filtering-engine:-details) for more details about where dynamic URL filtering fits in the overall filtering engine.

***

##### Static network filters

![Static filter tab in details dialog](https://user-images.githubusercontent.com/886325/62770779-0733a380-ba9c-11e9-99e2-77eeb7ac6290.png)

This dialog will assist you in creating static filters compatible with [ABP filter syntax](https://adblockplus.org/filter-cheatsheet). Note that creating static filters incur a significant overhead relative to dynamic URL filtering rules. Typically, you will first use dynamic URL filtering rules to quickly diagnose which network requests need to be allowed/blocked.

See [_"Overview of uBlock's network filtering engine: details"_](./Overview-of-uBlock's-network-filtering-engine:-details) for more details about where static filtering fits in the overall filtering engine.

***

##### Temporary exception filters

The button to toggle the "exceptor" on/off is labeled `#@#`:

![filtering tools dialog](https://user-images.githubusercontent.com/886325/69076705-4fb41300-0a34-11ea-8e9a-463b9a1d29d8.png)

Prior to [1.45.3rc2/1.46](https://github.com/gorhill/uBlock/commit/a91781a4959c0381c8ab3230545e4e0f579d4a2c), the feature worked only for static extended filters (i.e. cosmetic, scriptlet & HTML filters) and was hidden under an [[advanced setting|Advanced-settings#filterauthormode]].  
It now works with all static filters (including network filters) and open for regular use.

The temporary exceptions will be disabled when closing the logger (after 1.45.3rc2/1.46) or by manually toggling them off.

**Important** - When toggling on/off a temporary exception, filter lists are now fully reloaded and this means **there might be a perceptible delay** when adding/removing temporary exceptions. At this point, this is considered to be an acceptable side-effect just to bring the ability to easily create temporary exception for network filters.