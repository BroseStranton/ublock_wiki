Advanced user mode can be enabled from the _Settings_ tab in uBlock's dashboard. **Enable at your own risk.**

## Read the docs
<table><tr><td width="130" align="center">
<img src="http://i.imgur.com/3kJFgHX.jpg" float="right" width="96" height="96">
</td><td>
<p><b>Advanced users are expected to read the documentation. This is very important.</b></p>

<p>If you use advanced features without fully understanding them, uBlock:</p>

<ul>
<li>might</li>
<li><i>probably <b>will</b></i>
</ul>
.. behave in ways unexpected to you.
</td></tr></table>

If you think the documentation needs more work, you are more than welcome to contribute. Look for the grey <kbd>Edit</kbd> button on any wiki page — here's what it looks like: ![Edit button](http://i.imgur.com/RElN8kr.png)

If you don't see this button, you can [suggest your edit on the issue tracker](https://github.com/gorhill/uBlock/issues) instead.

## Differences

### Dynamic filtering

Dynamic filtering ([quick guide](https://github.com/gorhill/uBlock/wiki/Dynamic-filtering:-quick-guide)) will become available to advanced users.

Novice users could easily mess up uBlock's filtering through dynamic filtering, thus it is not available by default.

On the other hand, if you are familiar with [RequestPolicy](https://www.requestpolicy.com/), then you should have no problem dealing with dynamic filtering.

**Important note:** Dynamic filtering engine is completely turned off when you un-check the setting _"I am an advanced user"_. Your dynamic filtering rules are kept intact though, in case you re-enable _advanced user_ mode again.

### Ability to filter behind-the-scene network requests

See ["Behind-the-scene network requests"](https://github.com/gorhill/uBlock/wiki/Behind-the-scene-network-requests).