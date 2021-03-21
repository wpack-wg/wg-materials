 WPACK@IETF018
2020-07-31 - Virtual

adhoc minutes takers: Martin Thomson and Brian Trammell

## Logistics

### Time

Friday 2020-07-31 13:00 UTC 

### Meeting Information

Meetecho (a/v and chat):
https://meetings.conf.meetecho.com/ietf108/?group=wpack&short=&item=1

Audio (only):
http://mp3.conf.meetecho.com/ietf/ietf1083.m3u

Jabber (chat):
wpack@jabber.ietf.org

## Agenda

### Administrivia

- Virtual Meeting Tips
- Note Well
- Virtual Bluesheet (automatic)
- Note Taker
- Jabber Scribe
- Status

### Package: URL scheme - J. Yasskin

[slides](https://www.ietf.org/proceedings/108/slides/slides-108-wpack-urls-for-bundle-contents-01)

Ben Schwartz: exposing file:/// might cause some issues for this.  Even archives on servers might want to move.

Jeffrey: Some things about *desync*

Martin Thomson: having a fair bit of trouble with the notion of displaying these URLs to people. The problem with the URLs is I'm parsing information out of that. What am I expected to learn when I look at one of these things? I'm going to make inferences based on first domain name (no matter what).

Jeffrey: that domain can decide what is in the bundle. Might have done that with stuff it doesn't fully trust. May want users to think about both domain names. Browser should emphasize bundle's domain name (content controller)

Martin Thomson: can we have an authority URL in these things?

Jeffrey: scheme 3a/3b are the closest to the authority form. authority is the origin piece. 

Ted Hardie: Semantics and security properties are tightly related. One way to think about this, most critically what we need to convey is (1) it's a bundle and (1a) that that means the bundle author has the right to change what is present in the bundle, but not the bundle resource content. Distinct origins in bundles. Bundle creator sets bundle TOC. Bundle creator asserts they came from (somewhere else). Go back from these to the syntax -- you have split authority, the person who created the bundle is authority from the programmatic interface, but not the user interface. One of these (schemes 3) is programmatically appropriate. If you're creating a UI, you don't use the common UI, you have a new UI element that says "everything up to $ in 3B created a package for you which contains things that they think came from everything up to the first slash after." You never want to say that archive.example was the creator of the resource, to get across the semantics you want. This means either of these are fine. None of our current presentation methods will work, we should not build that here. 

Jeffrey: UI people say don't put the bundle owner in the UI, you'll confuse people.

Brian: (bikeshedding on URLs: formats that don't introduce new symbols are preferable to those that do, from a parser security standpoint. 

Ben Schwartz: Do bundles have collective integrity or resource integrity? Is the wbn an unvalidatable collection of signed objects?

Jeffrey: I'm assuming no signatures at all

Ben: You need some way to attribute resources to source domain 

Jeffrey: If you can verify the claimed URL, use that as origin. If not, chain through the domain of the bundle URL (vouched for by the connection security, e.g. TLS). 

--> please take it to the list

Martin Thomson: larger arch question here, thought bundles would be signed by camera.example. Then you have questions about how many origins in a bundle, etc, lots of complexity here. Maybe camera.example is a property of the bundle when you parse it. Without constraints on the problem, looks like an unconstrained solution. 

### Streaming Bundles - J. Yasskin

[slides](https://www.ietf.org/proceedings/108/slides/slides-108-wpack-streamed-bundle-generation-00)

Ben Schwartz: if you have streaming generation, client can't validate bundle as collective object until the end.

Jeffrey: you could validate chunks

Ben: i'm worried. validation properties shouldn't change during loading process based on mode. 

Jeffrey: chunk signatures protect against that. if signed individually, attacker could combine 

Ben: I prefer a system where each bundle has a big stamp on it -- breaking it up requires multiple bundles. 

Yoav Weiss: regardless of signing, value in using bundles to send multiple resources as optimization, which is currently concatenated JS. having a way to generate bundles enables adjacent use cases with partial dynamic content. we could add limitations on signed bundles to fix issues there.

Martin Thomson: if you're talking about serving dynamic content, it's a scheme that is competitive with HTTP, not sure why this is necessary. 

Jeffrey: Request bundling: too many requests. 

MT: turns out that's not that terrible a thing. 

ekr: not here to design a general purpose replacement for HTTP. let's not pretend the whole bundle shows up in an RTT, 

Jeffrey: have heard more arguments against doing this today. people that want to do this, please bring arguments forward on the list.

### Structuring Documents - Chairs

(no time remaining)
