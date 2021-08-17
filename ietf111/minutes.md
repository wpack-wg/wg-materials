# WPACK@IETF111

## Logistics

### Time

MONDAY, July 26, 2021 @ 2130-2230 UTC

### Meeting Information

Meetecho (a/v and chat):
https://meetings.conf.meetecho.com/ietf111/?group=wpack&short=&item=1

Audio (only):
http://mp3.conf.meetecho.com/ietf111/wpack/1.m3u

CodiMD (notes):
https://codimd.ietf.org/notes-ietf-111-wpack

## Agenda

### Administrivia

Chairs (10min)

- Virtual Meeting Tips
- Note Well
- Note Taker
- Jabber Scribe
- Status

Slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-wpack-wpack-chairs-slides-ietf111-00

### draft-yasskin-wpack-use-cases adoption - 10min - Chairs

### Bundle PRs

Slides: https://datatracker.ietf.org/meeting/111/materials/slides-111-wpack-web-bundles-00

I-D: https://www.ietf.org/archive/id/draft-yasskin-wpack-bundled-exchanges-03.txt
Repo: https://wicg.github.io/webpackage/draft-yasskin-wpack-bundled-exchanges.html 

PRs 5-7 - 15min - Felipe Erias

https://github.com/wpack-wg/bundled-responses/pull/5
https://github.com/wpack-wg/bundled-responses/pull/6
https://github.com/wpack-wg/bundled-responses/pull/7

# Notes

No agenda bashing.

WG call for adoption -> only got a couple of responses.

Proposal: drop use-case document from charter and go forward.  Just need to point to emails.

Rick Taylor: am chair of another working group which does bundles.  There is some relevance to people coming in from outside to understand.

David: like it as the background for why the group is doing what it's doing.

Rick: there's a benefit to keeping it for posterity so we understand why we did what we did.

Sean: no intention to publish as an RFC, either publish early and protocol makes it be incorrect.

Rick: suggest -> use cases be put into protocol spec itself.

...

Alexey Melnikov: If it's not adopted, the WG has no control over it.  Suggest: adopt, but don't publish as an RFC.  At least you have a snapshot.

Martin Thomson: if we adopt something like this, we need to reach consensus on things - lots in this document that I object to, some things I really like.  Don't want to go to the effort of litigating those points.

Daniel Gillmor: the idea that reaching consensus on what we want to do it hard means that we won't get consensus on the document!

Ted Hardie: agree with Alexey -> we should adopt and litigate about the use cases first, and separate that from the technology to achieve them.  It won't be faster, but at least it's cleaner.

Jeffrey Yasskin: want to comment on DKG's comment.  Some use cases are part of long-term vision.  Current focus is on the use cases that have more consensus.  Don't have to get around to discussing the more controversial use cases, except where designing flexibility into the format to support the contoversy, people might want to remove it.

Martin Thomson: There are bits that have general support.  The problem with taking on a document that includes the difficult parts is that we then have to disucss those.  Think doing the narrow bits with consensus is constructive use of time.

David Lawrence (without chair hat): would like to see document of the use cases the working group is trying to solve.

Mike Bishop: if we think we have good consensus on some cases, then we should have a working group document with only those cases!

Sean Turner: can we separate into two documents?  One with the stuff we agree on, another with the bits that are contentious.

Jeffrey: is an appendix OK?  Would prefer that to be there to keep flexibility.  Any objection?

NO OBJECTION.

## Web Bundles - Felipe Erias

Jeffrey: want working group's opinon on whether to do these things, rather than just discussion among authors.
 - e.g. removing primary URL means you can't navigate back to original source to fetch extra bits not included.
 - manifest, don't lose anything except efficiency
 - content negotiation: here to represent HTTP (which has it) but adds complexity and not clear that you would ever use this (except in narrow cases like translated data on an SD card) but represent HTTP less well.

Rick Taylor: not so much negotiation as just multiple representations just in different formats?  Jeffrey: Correct. Rick - then would suggest call it something else.  Multiple formats available.

Martin Thomson: think content-type is enough, if you don't support it you don't support it.  Don't need primary url.  Manifest unclear on.  Content-negotiation is clearly complexity.  The spec document should explain things, not a seprate markdown file somewhere.

Jeffrey (via Jabber): +1, should merge bundle-format.md into the spec.

Daniel E: (missed it sorry)

Rick Taylor: talking about offline and peer-to-peer use cases. This is part 2, not part 1 - keep it out of scope for now.

Watson Ladd: if a long term format for things like document - questions about what kind of images you can use, etc.  Agree step 2.

Ted Hardie: OK to be step 2, but even more anxious about keeping things in the appendix is important, so we don't close off this path in the future.  Deal with in a separate document, but make sure we have the extension points for it.

Daniel Ehrenberg: Think all the things we are removing with these proposed changes can be added back in with additional sections later.    Might be a bit ugly, but with extension architecture it would all work OK.

...

Felipe: have been focusing on use cases of bundles to preload resources:
- server sends a list of resources
- client requests the ones it doesn't have cached
- server creates a bundle of those resources

(I'm not noting what's on slides generally)

Jabber discussion: proxying, 'Cache-Control' headers.

Daniel Ehrenberg: want to ask - what do people think of the bundle subset approach?

No comment from AD.  Nobody jumping up to mic.
Martin Thompson via Jabber - was not prepared.

Watson Ladd; confused about how URL structure is supposed to work.  Representation of all resources in the directory?  How do you handle cache times?

Philipp Tiesel (via Jabber): this is much narrower than I expected, why not just request the server push the resources.

Daniel E: would only request the URLs that hadn't changed.  We've gone backwards and forwards on different designs.

...

Justin Richer: want to raise awareness of HTTP message signatures work in HTTP.

