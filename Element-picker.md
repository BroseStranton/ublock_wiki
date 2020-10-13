[Back to Wiki home](./)

***

The element picker's purpose is to assist the user in the creation of network or cosmetic filters.

![eye dropper highlighted in row of tool buttons](https://user-images.githubusercontent.com/886325/95906120-fd8d8600-0d99-11eb-9a91-84585e4c5739.png)

If there is an element on a web page you wish to remove forever, open the extension's popup menu, and click the small "eye-dropper" icon. You will enter the interactive element picker mode.

![Element picker](https://user-images.githubusercontent.com/585534/76684433-69c8c100-65e2-11ea-9588-60417dc00781.png)
<!-- ![Element picker](https://raw.githubusercontent.com/gorhill/uBlock/master/doc/img/ss-element-picker.png) -->

Once in element-picker mode, you have to point and click on the element you wish to remove.

Once you click on the element, you will be presented with a modal dialog box which allows you to select, and optionally edit and create a filter for the element(s) you wish to remove from the web page.


> ***
> **Tip:**
>
> You can easily move element picker dialog using mouse, by grabbing and dragging by empty space between buttons<sup>New in [1.24.0](https://github.com/gorhill/uBlock/commit/d1995778ff5908a4709c51dd30a08e2478c59251)</sup>
> ***

If possible, one or more network filters will be suggested, as well as a list of cosmetic filters. The top most cosmetic filter is the most specific which could be derived from the element you clicked. The bottom-most is the broadest, the least specific. Pick the one which matches best what you wish to accomplish (see [demo of this](https://www.youtube.com/watch?v=8TvCGWwQr5o)).

When you click on one of the suggested filters, you will be shown what effect it will have on the page. You may want to ensure the selected filter will not also get rid of useful items on the page.

You may manually edit the filter. However the result needs to be a valid filter, otherwise you won't be allowed to create a filter out of it. A valid filter in the context of the element picker is one which matches at least one element on the web page.

You may quit the interactive element picker by clicking the _Quit_ button (or press _Esc_). You may close the modal dialog and go pick an element again by clicking the _Pick_ button.

The _Create_ button will be enabled only if a proper filter can be created from the content of the text area. Once you click the _Create_ button, the element picker will add the necessary tokens to ensure the filter apply **only** to the current web site, will add it to your custom list of filters and save it.

On touch screen devices:
- swipe right to exit element-picker mode
- when dialog is visible, swiping right will hide element-picker dialog (will make it dimmed and transparent)
- when dialog is hidden, swipe right again to exit element-picker mode
- swipe left to make dialog visible again

### Element picker does not work, removed element reappears when you reload the page?

There may be many different reasons for this.

- If this is a network filter you may need to bypass the browser cache when you reload the page -- hold down the <kbd>Shift</kbd> key when you click the reload button.
- The URL or selector for the blocked element has variable part(s) in it, which changes each time a page is loaded.
    - If this is a network filter you may need to manually edit the filter to make use of wildcards for the parts of the URL which are variable.
    - If this is a cosmetic filter, you may have to manually craft a better [CSS selector](https://www.w3.org/TR/selectors/#overview). Sometimes this requires observing the surrounding DOM data.
- Cosmetic filtering is disabled for the site, or globally. There are many ways to disable cosmetic filtering:
    - The [per-site cosmetic filtering switch](./Per-site-switches#no-cosmetic-filtering).
    - The option [_"Parse and enforce cosmetic filters"_](./Dashboard:-3rd-party-filters#parse-and-enforce-cosmetic-filters) is un-checked in the [_3rd-party filters_](./Dashboard:-3rd-party-filters) pane in the dashboard.
- You un-checked _My filters_ in the _3rd-party filters_ pane in the dashboard.
- There is a static filter in one of the 3rd-party filter lists in use which counters your filter.
    - Exception cosmetic filters (`#@#`) cancel cosmetic filters (`##`).
    - Exception filter with [`elemhide`](./Static-filter-syntax#elemhide-1) or [`specifichide`](./Static-filter-syntax#specifichide) option.
