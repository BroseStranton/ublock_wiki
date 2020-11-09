[Back to "Quick guide: popup user interface"](./Quick-guide:-popup-user-interface)

***

The per-site switches allows you to control uBlock's behavior on a per-site basis.

![Popup UI](https://user-images.githubusercontent.com/585534/87855535-01b71e00-c8e7-11ea-9744-4e21429cfd7d.png)

Changes to the state of per-site switches are temporary until you make them permanent by clicking the padlock icon. Pressing <kbd>Ctrl</kbd> (<kbd>Cmd</kbd> on Mac) when toggling switches will make them permanent immediately.

![eraser and padlock](https://user-images.githubusercontent.com/585534/87855454-8190b880-c8e6-11ea-9d8b-5b3a4baf120d.png)
<br><sup>Eraser and padlock icons</sup>

***

- [No popups](#no-popups)
- [No large media elements](#no-large-media-elements)
- [No cosmetic filtering](#no-cosmetic-filtering)
- [No remote fonts](#no-remote-fonts)
- [No scripting](#no-scripting)

***

## No popups

By default popups are allowed unless there is a filter to block them. When this setting is enabled, **all** popups will be unconditionally blocked for the current site, regardless of filters:

![Popup UI](https://user-images.githubusercontent.com/585534/87855339-a0db1600-c8e5-11ea-987f-4445b8d83a1a.png)<br><sup>The badge shows the number of popups that have been closed on the page.</sup>

No popups rules appear as `no-popups: [hostname] true` entries in the [_My rules_ pane](./Dashboard:-My-rules).

Blocking popups depends on whether the proper filters are present in the selected filter lists, so this feature is most useful when a site creates popups for which there are no filters to take care of them in 3rd-party filter lists.

**Caveat:** It's not _always_ possible for uBlock Origin to determine for sure whether a new tab being opened is that of a popup, or is the result of a legitimate click on a link by the user. So if the no-popups switch is in use, you _may_ not be able to open a link in a new tab through the context menu.

***

## No large media elements

The second icon is to toggle on/off the blocking of large media elements for the current site. The primary purpose of this feature is to save bandwidth. Side effect is to possibly speed up page load.

![Popup UI](https://user-images.githubusercontent.com/585534/87855343-a5073380-c8e5-11ea-88ef-13f8529fb369.png)<br><sup>The badge shows the number of large media elements that have been blocked on the page.</sup>

By default, this setting is disabled. The global default can be enabled in the [_Settings_ pane](./Dashboard:-Settings) in the [dashboard](./Dashboard).

![a](https://user-images.githubusercontent.com/585534/46021852-818b4d00-c0af-11e8-8fdb-e028bc20e8ae.png)

The threshold size -- a global setting -- to decide when to block or not is also configurable. The threshold size can be set to zero: this will cause all media elements to be blocked. For the sake of documentation, let's refer to media elements (images, videos, audios) which are larger than the set size as _"large media elements"_.

You can enable/disable on a per-site basis, there is a switch in the popup panel to toggle for the current site.

When large media elements have been blocked on a page, you may force a reload of these elements interactively: if you hover over the placeholder of a blocked image and the cursor changes into a magnifier, this means that clicking on a blocked image will force a reload of that image.

If you use this feature and large media elements were blocked on a web page, the context menu will contain a new entry: _"Temporarily allow large media elements"_. When you click this entry, uBO will disable temporarily the blocking of large media element for the site, and attempt to load the blocked media elements without re-loading the page. In some cases you may need to force a reload of the page, for example if large media elements were fetched programmatically by the page. The temporary disabling will be removed for a tab as soon as you travel to a new site, or close the tab.

Blocked large media elements are reported in the logger with the filter `no-large-media: [scope] true`.

Note that this feature has no privacy value: a connection to the remote server must be performed in order to fetch the size of the resource. This of course applies only to resources which were not otherwise blocked by uBO's filtering engine.

Examples of usefulness (let's say you just stumbled onto these pages not knowing whether the article would really interest you), bandwidth consumed:

- <http://www.wired.com/2016/01/drones-arent-just-toys-anymore>
    - Not blocking large media elements: 5.5 MB.
    - Blocking media elements larger than 1 MB: 2.1 MB.
    - Blocking media elements larger than 50 kB: 1.2 MB.
- <http://www.tomshardware.com/reviews/samsung-gear-vr-headset,4405.html>
    - Not blocking large media elements: 15.1 MB.
    - Blocking media elements larger than 1 MB: 15.1 MB.
    - Blocking media elements larger than 50 kB: 61 kB.
- <https://twitter.com/> (your Twitter stream):
    - Not loading largish images by default can help Twitter page performance: click on a placeholder to load only the images which seems to be of interest to you.
    - This is true for any "infinite scrolling" web pages ([another example](http://www.bloomberg.com/news/articles/2016-01-19/being-illegal-won-t-keep-drones-from-taking-over-india)). Not loading the images by default help a lot in such cases.

#### Caveat:

If the media elements do not have `Content-Length` header present, then this switch will fail to block the said media elements by size.

***

## No cosmetic filtering

["Cosmetic filtering" in uBO](https://github.com/gorhill/uBlock/wiki/Does-uBlock-block-ads-or-just-hide-them%3F#cosmetic-filters) is what is known as "element hiding" in Adblock Plus. Purpose of these filters is to hide content of the page that cannot be blocked by network filters. 

You can easily toggle on/off cosmetic filtering for a given site:

![Popup UI](https://user-images.githubusercontent.com/585534/87855347-a6d0f700-c8e5-11ea-84f8-d64ce9ddd08a.png)<br><sup>The badge shows the number of DOM elements that have been hidden on the page.</sup>

When present, the badge number indicates the number of elements hidden on the page by uBO as a result of cosmetic filtering. If you disable cosmetic filtering while there are hidden elements on the page, these elements will become visible/hidden as you toggle off/on cosmetic filtering.

A good example of cosmetic filtering in action are the ads showing up with the results of a Google Search page ([example](https://www.google.com/search?q=buy+car&oq=buy+car)).

Cosmetic filtering is always enabled by default.

> ***
> **Tips**
>
> It is often suggested adding a custom static filter such as `@@||example.com^$elemhide` or `@@||example.com^$generichide` to prevent "adblock" detection by specific sites ([example](https://adblockplus.org/forum/viewtopic.php?f=2&t=30763#p124225), [example](https://adblockplus.org/forum/viewtopic.php?f=2&t=43961)). You can accomplish the same goal more simply by just toggling off cosmetic filtering using this switch while on the problematic site.
> 
> This switch can help uBO to further lower its CPU-cycle footprint, which might be beneficial on devices with limited CPU-cycle resources -- and thus helping extend battery life and speed up page load times. The idea is to disable cosmetic filtering everywhere by default, and to enable it only for those sites which really benefit from it.
> ***

To disable cosmetic filtering everywhere by default, go to the [_Settings_ pane](./Dashboard:-Settings) in the [dashboard](./Dashboard), and check the option _"Disable cosmetic filtering"_ under the _"Default behavior"_ header:

![Disable cosmetic filtering everywhere by default](https://user-images.githubusercontent.com/585534/46022246-3887c880-c0b0-11e8-9edc-ded22a011996.png)

From then on, cosmetic filtering will be turned off everywhere by default, and to turn it on for a specific site where it is really needed, just enable it using the switch in uBO's popup panel.

***

## No remote fonts

You can prevent web fonts from being downloaded for the current site:

![Popup UI](https://user-images.githubusercontent.com/585534/87855349-a8022400-c8e5-11ea-92fb-b7cf6cc431fc.png)<br><sup>The badge shows the number of font resources that have been seen on the page.</sup>

Because of security and privacy concerns, many prefer to block all web fonts by default -- toggle the appropriate default behavior in the [_Settings_ pane](./Dashboard:-Settings) in the [dashboard](./Dashboard):

![Block remote fonts everywhere by default](https://user-images.githubusercontent.com/585534/46022554-da0f1a00-c0b0-11e8-9689-542f26b7126e.png)

This will block all web fonts everywhere by default, and in this case you can toggle off the switch to allow web fonts on a per-site basis.

Keep in mind, though, that this rule blocks **all** first-party and third-party fonts. As a lighter alternative you can also choose to allow first-party fonts and block _only_ third-party fonts by adding the filter 

`*$font,third-party`

to the _"My filters"_ pane. If you want to allow third-party fonts for some specific sites you can add them by modifying the above filter:

`*$font,third-party,domain=~example.com|~other.example.net|~different.example.org`

***

## No scripting

New in [1.17.0](https://github.com/gorhill/uBlock/commit/3c85c0319462ca331d53c350fba4bc6c1b2ef96f)

Wholly disable JavaScript for a given site.

![Popup UI](https://user-images.githubusercontent.com/585534/87855351-a9cbe780-c8e5-11ea-87ed-ee6ea2693fad.png)
<br>The badge shows approximate number of script resources which have
been seen on the page (number is limited to 99 because of layout constraints)

![purple badge](https://user-images.githubusercontent.com/886325/64036667-039fb380-cb54-11e9-8199-cf042837d481.png)
<br>Starting with [v1.21.7b5](https://github.com/gorhill/uBlock/commit/7ff750eaf6007bdea4e843d3314fc7275b1ce945), a purple badge on uBlock₀ toolbar button indicates activation of the "No scripting" switch.

This master switch has blocking precedence over dynamic filtering rules and static filters related to script resources.

Furthermore, when JavaScript is disabled through this master switch, [`noscript`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noscript#Example) tags will be honoured on a page (as opposed to when just using filters/rules to block script resources).

As with some other per-site switches, the default state of per-site JavaScript master switch can be set in the [_Settings_ pane](./Dashboard:-Settings), thus allowing to disable JavaScript everywhere by default, and enable on a per-site basis:

![a](https://user-images.githubusercontent.com/585534/46022411-84d30880-c0b0-11e8-9055-7e37b113ec13.png)

JavaScript master switch rules appear as `no-scripting: [hostname] true` entries in the [_My rules_ pane](./Dashboard:-My-rules).

The JavaScript master switch can be disabled through the "Relax blocking mode" keyboard shortcut.
