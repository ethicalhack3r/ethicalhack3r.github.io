---
layout: post
status: publish
published: false
title: Google Chrome Protocol Handler Fun
excerpt: "Certificate Pinning is an extra layer of security that is used by applications to ensure that the certificate provided by the remote server is the one which is expected.
\r\n\r\n
By including the remote server’s x509 certificate or public key within the application, it is possible to compare the locally stored certificate or key with the one provided by the remote server.
\r\n\r\n
If you have been unable to intercept (Man-in-the-Middle) the application’s HTTPS traffic, after taking the necessary steps, this is probably due to the application using Certificate Pinning."
---

You're probably all familiar of the custom protocol handlers browsers use for various things such as ```chrome://settings/``` and ```chrome://credits/```. I was using a Chrome app (extention) the other day that suggested I copy and pasted ```chrome://restart``` in to my browser address bar to restart Chrome. This got me thinking about the ```chrome``` protocol handler, what other ones are there and how they might they be able to be used for a bit of fun.

The first obvious bit of fun we could have is if someone clicked on a HTML link to ```chrome://restart``` and have their browser restart, losing all of their open tabs. This is so obvious that Chrome do not allow this to happen by default and you will see the following error in the browser console ```Not allowed to load local resource: chrome://restart/```.

So I thought about setting ```chrome://restart``` as the browser's startup page, the idea being that Chrome would just restart itself everytime the browser is opened. This kind of worked, but Chrome only restarted itself once and then continued as usual, not much fun.

Next idea was to set ```chrome://restart``` as the default search engine, this way anytime someone mistypes a URL or searches for something using the address bar the browser will restart, very frustrating! This didn't work initially as Chrome expects all search engine URLs to have the ```%s``` marker to denote the search keyword value position. After some fiddling this was achieved by setting the URL as ```chrome://restart/../%s./../```, and voila, Chrome now restarts everytime the adress bar is used to search for something. That's much more fun!

Later it was pointed out to me on Twitter that the browser's startup page could actually be set to ```chrome://quit```. This is much more annoying than using ```chrome://restart``` for the startup page as the browser would just quit straight after opening. I had ```rm -rf``` all of the Chrome directories on my machine that contained saved settings to get Chrome to start again. Don't try this unless you want spend some time recovering Chrome!

So what other Chrome Protocol Handlers are there? I couldn't find a definitive up to date list online so I decided to download the Google Chrome source code and extract them all, resulting in the list below:

```
chrome://-alkuisissa
chrome://-nettadresser
chrome://-webbadresser
chrome://ChromeTestChromeWebUIControllerFactory
chrome://DummyURL
chrome://URLs
chrome://about
chrome://accessibility
chrome://anything
chrome://app-list
chrome://appcache-internals
chrome://apps
chrome://badala
chrome://badcastcrash
chrome://bar
chrome://blah
chrome://blank
chrome://blob-internals
chrome://bluetooth-pairing
chrome://bogus
chrome://bookmarks
chrome://browser
chrome://certificate-manager
chrome://choose-mobile-network
chrome://chrome
chrome://chrome-signin
chrome://chrome-urls
chrome://components
chrome://conflicts
chrome://constrained-test
chrome://consumer-management
chrome://contextual-search-promo
chrome://cookieset
chrome://copresence
chrome://crash
chrome://crashdump
chrome://crashes
chrome://credits
chrome://credits-
chrome://cryptohome
chrome://device-emulator
chrome://device-log
chrome://devices
chrome://discards
chrome://dns
chrome://dom-distiller
chrome://domain-reliability-internals
chrome://downloads
chrome://drive
chrome://drive-internals
chrome://example
chrome://extension
chrome://extension-crash
chrome://extension-icon
chrome://extensions
chrome://extensions-frame
chrome://extensions-kohdassa
chrome://external-file
chrome://f
chrome://fallback-icon
chrome://favicon
chrome://fblahblahblah
chrome://fg
chrome://fileicon
chrome://first-run
chrome://fl
chrome://flag
chrome://flagg
chrome://flags
chrome://flash
chrome://foo
chrome://gcm-internals
chrome://gesture
chrome://gpu
chrome://gpuclean
chrome://gpucrash
chrome://gpuhang
chrome://hang
chrome://help
chrome://help-frame
chrome://histograms
chrome://historik
chrome://history
chrome://history-frame
chrome://host
chrome://http
chrome://identity-internals
chrome://imageburner
chrome://indexeddb-internals
chrome://inducebrowsercrashforrealz
chrome://inspect
chrome://instant
chrome://internal
chrome://interstitials
chrome://invalidations
chrome://javascript
chrome://kasko
chrome://keyboard
chrome://keyboardoverlay
chrome://kill
chrome://large-icon
chrome://linux-proxy-config
chrome://local-state
chrome://make-metro
chrome://managed-user-passphrase
chrome://md-policy
chrome://md-settings
chrome://measurepageloadtimeextension
chrome://media-internals
chrome://media-router
chrome://memory
chrome://memory-internals
chrome://memory-redirect
chrome://mobilesetup
chrome://mojo-web-ui
chrome://most_visited
chrome://nacl
chrome://navigate
chrome://net
chrome://net-export
chrome://net-internals
chrome://network
chrome://network-error
chrome://network-errors
chrome://newprofile
chrome://newtab
chrome://newtab2
chrome://newtab3
chrome://nfc-debug
chrome://omaha
chrome://omnibox
chrome://oobe
chrome://options
chrome://os-credits
chrome://os_credits
chrome://password-manager-internals
chrome://path
chrome://peripheral-battery
chrome://plugins
chrome://pnacl-translator
chrome://policy
chrome://popular-sites-internals
chrome://power
chrome://ppapiflashcrash
chrome://ppapiflashhang
chrome://predictors
chrome://preferences
chrome://print
chrome://profile-signin-confirmation
chrome://profiler
chrome://proximity-auth
chrome://proximity_auth
chrome://proxy-settings
chrome://quit
chrome://quit-with-apps
chrome://quota-internals
chrome://recent-tabs
chrome://resources
chrome://restart
chrome://s
chrome://salsa
chrome://sandbox
chrome://screen
chrome://screenlock-icon
chrome://screenshot
chrome://serviceworker-internals
chrome://session
chrome://set-time
chrome://settings
chrome://settings-frame
chrome://setupfortesting
chrome://shorthang
chrome://sign-in
chrome://signin
chrome://signin-internals
chrome://sim-unlock
chrome://site-engagement
chrome://slow
chrome://slow_trace
chrome://somepage
chrome://source_name
chrome://stylesheet
chrome://suggestions
chrome://supervised-user-internals
chrome://sync-internals
chrome://syncfs-internals
chrome://syncresources
chrome://system
chrome://tab-modal-confirm-dialog
chrome://tcmalloc
chrome://terms
chrome://test
chrome://test-page
chrome://theme
chrome://thumb
chrome://thumbnail
chrome://thumbnails
chrome://thumbs
chrome://tracing
chrome://trailing2blah
chrome://translate-internals
chrome://uber-frame
chrome://ui-alternatives
chrome://uithreadhang
chrome://user
chrome://user-actions
chrome://user-chooser
chrome://user-manager
chrome://userimage
chrome://usr
chrome://ve
chrome://version
chrome://view-cert
chrome://view-cert-dialog
chrome://view-http-cache
chrome://voicesearch
chrome://webrtc-device-provider
chrome://webrtc-internals
chrome://webrtc-logs
chrome://webui
chrome://welcome
chrome://youtube
```

Not all of these will work as some will have come from unit tests, code comments and other places, but there are some interesting ones there to play about with!  ```chrome://inducebrowsercrashforrealz``` is especially interesting!

Later it was also pointed out to me on Twitter that I had used an outdated version of Google Chrome to extract the protocol handlers from, so the above list is a revised version using the lastest version of Chrome I could find. It was also pointed out to me that you can use ```chrome://chrome-urls``` to list some of the protocol handlers but I did find that there were some missing from that list such as ```chrome://inducebrowsercrashforrealz```.






