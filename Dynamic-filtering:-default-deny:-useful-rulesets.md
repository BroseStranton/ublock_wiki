Reminder: the `noop` rule action means that network requests will not be filtered through dynamic filtering, but they will still be filtered through static filtering (_EasyList_, _EasyPrivacy_, etc). 

    # the default-deny rules
    * * 3p block
    * * 3p-frame block

    # Pick whatever you want, or all

    # Global

    # To translate any web page using the contextual menu in Chromium
    * translate.googleapis.com * noop

    # Exception for enabling firefox sync
    * services.mozilla.com * noop

    # Local

    # 9to5mac.com
    9to5mac.com 9to5mac.files.wordpress.com * noop
    9to5mac.com i0.wp.com * noop
    9to5mac.com i1.wp.com * noop
    9to5mac.com i2.wp.com * noop
    9to5mac.com s0.wp.com * noop
    9to5mac.com s1.wp.com * noop
    9to5mac.com s2.wp.com * noop

    # amazon.ca
    www.amazon.ca images-amazon.com * noop
    www.amazon.ca ssl-images-amazon.com * noop

    # arstechnica.com
    arstechnica.com arstechnica.net * noop

    # bbc.com
    www.bbc.com bbc.co.uk * noop
    www.bbc.com bbci.co.uk * noop
    www.bbc.com bbcimg.co.uk * noop

    # bloomberg.com
    www.bloomberg.com bwbx.io * noop
    www.bloomberg.com gotraffic.net * noop

    # buzzfeed.com
    www.buzzfeed.com akamaihd.net * noop
    www.buzzfeed.com buzzfed.com * noop
    www.buzzfeed.com instagram.com * noop

    # change.org
    www.change.org d22r54gnmuhwmk.cloudfront.net * noop

    # chromium.org
    www.chromium.org gstatic.com * noop

    # cnet.com
    www.cnet.com cbsimg.net * noop
    www.cnet.com cbsistatic.com * noop

    # cnn.com
    www.cnn.com turner.com * noop
    # for videos
    www.cnn.com cnn-f.akamaihd.net * noop

    # crowdin.com
    crowdin.com d1ztvzf22lmr1j.cloudfront.net * noop

    # deviantart.com
    deviantart.com deviantart.net * noop

    # ebay.com
    www.ebay.com ebaydesc.com * noop
    www.ebay.com ebayimg.com * noop
    www.ebay.com ebaystatic.com * noop

    # economist.com
    www.economist.com static-economist.com * noop

    # engadget.com
    www.engadget.com 5min.com * noop
    www.engadget.com aolcdn.com * noop
    www.engadget.com blogcdn.com * noop
    www.engadget.com blogsmithmedia.com * noop

    # facebook.com
    facebook.com akamaihd.net * noop
    facebook.com fbcdn.net * noop

    # fastcompany.com
    www.fastcompany.com fastcompany.net * noop

    # fool.com
    www.fool.com foolcdn.com * noop

    # foxnews.com
    foxnews.com fncstatic.com * noop

    # funnyjunk.com
    www.funnyjunk.com fjcdn.com * noop

    # gigaom.com
    gigaom.com wordpress.com * noop
    gigaom.com wp.com * noop

    # github.com
    github.com avatars0.githubusercontent.com * noop
    github.com avatars1.githubusercontent.com * noop
    github.com avatars2.githubusercontent.com * noop
    github.com avatars3.githubusercontent.com * noop
    github.com camo.githubusercontent.com * noop
    github.com cloud.githubusercontent.com * noop
    github.com raw.githubusercontent.com * noop
    github.com render.githubusercontent.com * noop
    # This one is needed to allow auto-upload of images through drag-n-drop
    github.com s3.amazonaws.com * noop

    # gizmodo.com
    gizmodo.com kinja-img.com * noop
    gizmodo.com kinja-static.com * noop
    gizmodo.com kinja.com * noop

    # ign.com
    www.ign.com ignimgs.com * noop

    # mail.google.com
    mail.google.com googleusercontent.com * noop
    mail.google.com gstatic.com * noop

    # huffingtonpost.ca
    www.huffingtonpost.ca huffpost.com * noop

    # huffingtonpost.co.uk
    www.huffingtonpost.co.uk huffpost.com * noop

    # kaspersky.com
    blog.kaspersky.com kaspersky-cyberstat.com * noop
    blog.kaspersky.com kasperskycontenthub.com * noop
    blog.kaspersky.com netdna-cdn.com * noop

    # kickstarter.com
    www.kickstarter.com d297h9he240fqh.cloudfront.net * noop
    www.kickstarter.com d2pq0u4uni88oo.cloudfront.net * noop
    www.kickstarter.com imgix.net * noop
    www.kickstarter.com kck.st * noop

    # lapresse.ca
    www.lapresse.ca lpcdn.ca * noop

    # latimes.com
    www.latimes.com trbas.com * noop
    www.latimes.com trbimg.com * noop
    www.latimes.com tribdss.com * noop
    www.latimes.com tribune.com * noop

    # lemonde.fr
    www.lemonde.fr lemde.fr * noop

    # lifehacker.com
    lifehacker.com kinja-img.com * noop
    lifehacker.com kinja-static.com * noop
    lifehacker.com kinja.com * noop

    # linkedin.com
    www.linkedin.com licdn.com * noop

    # marketwatch.com
    www.marketwatch.com mktw.net * noop
    www.marketwatch.com wsj.net * noop

    # mashable.com
    mashable.com mshcdn.com * noop

    # medium.com
    medium.com d262ilb51hltx0.cloudfront.net * noop
    medium.com dnqgz544uhbo8.cloudfront.net * noop

    # mozilla.org
    mozilla.org mozilla.net * noop
    mozilla.org mozillademos.org * noop

    # nbcnews.com
    www.nbcnews.com nbcudigitaladops.com * noop
    www.nbcnews.com s-nbcnews.com * noop

    # nytimes.com
    nytimes.com nyt.com * noop

    # reddit.com
    reddit.com redditmedia.com * noop
    reddit.com redditstatic.com * noop

    # reuters.com
    www.reuters.com reutersmedia.net * noop

    # scribd.com
    www.scribd.com scribdassets.com * noop

    # seekingalpha.com
    seekingalpha.com cdn-seekingalpha.com * noop

    # slashdot.org
    slashdot.org bootstrapcdn.com * noop
    slashdot.org fsdn.com * noop

    # slate.com
    www.slate.com cdnslate.com * noop

    # slideshare.net
    www.slideshare.net slidesharecdn.com * noop

    # smashingmagazine.com
    www.smashingmagazine.com netdna-cdn.com * noop

    # stackoverflow.com
    stackoverflow.com sstatic.net * noop
    stackoverflow.com ajax.googleapis.com * noop

    # superuser.com
    superuser.com sstatic.net * noop

    # techcrunch.com
    techcrunch.com 5min.com * noop
    techcrunch.com wordpress.com * noop
    techcrunch.com wp.com * noop
    techcrunch.com wpcomwidgets.com * noop

    # techrepublic.com
    www.techrepublic.com cbsimg.net * noop
    www.techrepublic.com cbsistatic.com * noop

    # theguardian.com
    www.theguardian.com guardianapps.co.uk * noop
    www.theguardian.com guim.co.uk * noop
    www.theguardian.com theguardian.tv * noop
    profile.theguardian.com guardianapis.com * noop
    profile.theguardian.com guardianapps.co.uk * noop
    profile.theguardian.com guim.co.uk * noop

    # thenextweb.com
    thenextweb.com tnwcdn.com * noop

    # theregister.co.uk
    www.theregister.co.uk regmedia.co.uk * noop
    forums.theregister.co.uk regmedia.co.uk * noop

    # theverge.com
    www.theverge.com ajax.googleapis.com * noop
    www.theverge.com vox-cdn.com * noop
    www.theverge.com voxmedia.com * noop

    # netdna-ssl.com
    threatpost.com netdna-ssl.com * noop

    # tomshardware.com
    www.tomshardware.com bestofmedia.com * noop
    www.tomshardware.com bestofmicro.com * noop

    # twitch.tv
    twitch.tv jtvnw.net * noop
    twitch.tv swiftype.com * noop
    twitch.tv ttvnw.net * noop

    # twitter.com
    twitter.com twimg.com * noop

    # usatoday.com
    www.usatoday.com gannett-cdn.com * noop
    www.usatoday.com usatoday.net * noop

    # variety.com
    variety.com wordpress.com * noop
    variety.com wp.com * noop

    # veetle.com
    veetle.com ajax.googleapis.com * noop
    veetle.com d3u3s1yur1h76d.cloudfront.net * noop
    # probably you will have to add more if video doesn't play
    # I plan to add ability to 38.102.* eventually
    veetle.com 38.102.162.229 * noop
    veetle.com 38.102.162.242 * noop
    veetle.com 38.102.162.254 * noop

    # venturebeat.com
    venturebeat.com netdna-cdn.com * noop
    venturebeat.com vbstatic.co * noop

    # vox.com
    www.vox.com ajax.googleapis.com * noop
    www.vox.com vox-cdn.com * noop

    # washingtonpost.com
    www.washingtonpost.com wpdigital.net * noop
    # embedded videos
    www.washingtonpost.com jwpcdn.com * noop
    www.washingtonpost.com posttv.com * noop

    # wiktionary.org
    wiktionary.org wikimedia.org * noop

    # wikipedia.org
    wikipedia.org wikimedia.org * noop

    # wsj.com
    www.wsj.com wsj.net * noop

    # yahoo.com
    yahoo.com yimg.com * noop

    # ycombinator.com
    blog.ycombinator.com phaven-prod.s3.amazonaws.com * noop
    blog.ycombinator.com posthaven-assets.s3.amazonaws.com * noop

    # youtube.com
    www.youtube.com content.googleapis.com * noop
    www.youtube.com ggpht.com * noop
    www.youtube.com google.com * noop
    www.youtube.com googleusercontent.com * noop
    www.youtube.com googlevideo.com * noop
    www.youtube.com gstatic.com * noop
    www.youtube.com plus.googleapis.com * noop
    www.youtube.com youtube-nocookie.com * noop
    www.youtube.com ytimg.com * noop

    # zdnet.com
    www.zdnet.com cbsistatic.com * noop