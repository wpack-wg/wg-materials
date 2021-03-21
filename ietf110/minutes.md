# WPACK@IETF110

Chairs: Sean Turner, David Lawrence

Responsible AD: Francesca Palombini 

Notes taker: Chris Lemmons

jabber logs: https://www.ietf.org/jabber/logs/wpack/2021-03-12.html

## Logistics

### Time

FRIDAY, March 12, 2021 @ 1530-1630 UTC

### Meeting Information

Meetecho (a/v and chat):
https://meetings.conf.meetecho.com/ietf110/?group=wpack&short=&item=1

Audio (only):
http://mp3.conf.meetecho.com/ietf110/wpack/1.m3u

CodiMD (notes):
https://codimd.ietf.org/notes-ietf-110-wpack

## Agenda

### Administrivia - Chairs (Sean Turner, David Lawrence)

### Work Towards Adopting Web Bundles

Presenter: Jeffrey Yasskin (50min)
Presentation: TBD
I-D: https://www.ietf.org/archive/id/draft-yasskin-wpack-bundled-exchanges-03.txt
Repo: https://wicg.github.io/webpackage/draft-yasskin-wpack-bundled-exchanges.html

#### Slide 9

Daniel Ehrenberg: The motivation for removing some of these features is to reduce the scope to increase the adoption. There is particular concern around how content-blockers will work in this context.

Martin Thomson: I think this is the right sort of thing to be thinking about right now. But a narrowly targeted thing is more likely to be successful here. If we cut a little too deep, we always have the opportunity to define something more specific later, possibly with a different MIME type.

Can you talk about the current state of how people expect to use the bundle or pull things out of them.

Jeffrey: Chrome is working on an origin trial that loads somewhat incautiously. It lets you use a bundle for sub-resources. The likely eventual answer is a sort of loading map that intercepts requests. Bundles probably have internal references as well.

Martin: The fetchmaps concept is important. The idea is that when a page requests one url, the browser can replace the url directly, possibly with one in a bundle.

Daniel: Bundles allow incremental loading, this is really important, but not fully fleshed out at this point.

Jeff: We haven't pinned down the details on how bundles and caching interact.

#### Slide 10

Martin: Are there any ordering requirements for these fallback URLs?

Jeff: No ordering requirements in particular, other than the fact that you have to wait for it to be transmitted.

Martin: No structural constraints?

Jeff: No.

Martin: So what special behavior is associated with the fallback url?

Daniel: Different use cases are going to have very different semantics for this fallback url. We have discussion of fallback semantics, but it is going to vary based on the use case. I think that's why it would be a good thing to remove this from the draft. There are a lot of valid points in this design space, though.

David: We're discussing refining the document, but we haven't adopted it. Perhaps we can focus our attention on whether we want to adopt it?

#### Discussion

Show of hands: Should we formally adopt this draft as a working group document?  
Raised Hands: 12  
Unraised Hands: 2  
Total People: 27

Show of hands: Do you OBJECT to adopting this document?  
Raised Hands: 0  
Unraised Hands: 9  
Total People: 26

Chairs will take it back WG adoption to list. Will also move the datatracker status to be "Candidate for WG Adoption".

David: I will get the GitHub repo set up.

PSnyder (from Jabber, voiced at mic by dkg): Brave (and Eyeo I believe, but I don't mean to speak for them) have both stated serious concerns with the implications for opinionated / "blocking" clients. Others who do content blocking have registered similar concerns on the original GH issue I filed. I know JY and MT have found those concerns either mistaken, or a cost worth the benefit from the proposal, or similar. I don't mean to re-litigate that here (at least not in this text field 🙂 ). But I just wanted to re-note that the folks who are most invested in / concerned with content blocking are the folks who have raised the loudest concerns. Some of the previously noted rejections or responses to those concerns are from vendors who do (relatively) less blocking in their products. Again, I don't mean to re-argue the specific concerns here, only that I hope the group will consider the content blocking concerns going forward, and will solicit / invite input from the content blocking folks with the content blocking concerns 🙂

Daniel: One aspect of the content-blocking concerns is whether a bundle should represent a single page on the web. This differs from the idea of sub-resource loading which is more granulal. There are different concerns that I'm attempting to address with some of these PRs. Do these removals help work toward your goals?

Pete Snyder: Yes, they do.

Martin Thompson: Let's be clear: this is a starting point. Pete and others have expressed concern that we do something bad for semantic availability type features. There are risks. We could design something very, very bad for those use cases and we need to work through those things. Indexes at the end makes it easy to change contents of bundles, for example.

Pete: i think there is a core for the sub resource loading that is great, and being able to split the sub-resource case from the document case seems valuable

Jeff: Let's get a sense of the room on these four issues. How do people feel about removing the fallback url.

Martin: The idea of a fallback is interesting. It's largely for compatibility reasons. It provides an escape hatch for simpler clients. I don't feel this use case as acutely. We should discuss whether it should be metadata or sections or something else and it can enable a variety of use cases.

Jeff: The reason for a primary url is when you navigate to the bundle itself and need to know what to load.

Martin: Lots of ways to skin this cat.

Jeff: Only reason not to move this is because it prevents us from using it for fallback.

Martin: If you think of a referencing infrastructure can refer to either a bundled or non-bundled resource, we don't need this.

Jeff: Hum?

Daniel: Keep in mind, these things can move to another document. Just because we remove it from here, we can still move it into a separate document.

Show of Hands: Should we merge in PR 617 into the draft for initial submission as a wg doc?
Raised Hands: 5  
Unraised Hands: 2  
Total People: 26  
Sense of the room: Quiet positive hum

Jeff: Should we remove content negotiation?

Daniel: If you're thinking about subresource loading, this adds more complexity. For the content-blocking story, this really comes back to separating subresource loading cases from whole website cases. Offline usage is really a separate question.

Martin: This one is hard because I can see the value in multiple image sizes or multiple languages. Having all the different CSS for small and large screens instead of the single factor that is often delivered can be useful. I'm on the fence. why would we keep this?

Jeff: You mentioned reasons to keep it. But more speculatively, when the server would check something like Sec-Fetch headers and wants to constrain things, then it could use that to block content from within the bundle. But more often, it's for offline uses.

Martin: Can we do CORS with bundles? I'm not sure it's possible at all.

Daniel: CORS are in response headers. Could we do it that way?

Martin: But you would have to put that in an OPTIONS request.

Daniel: We have two kinds of index sections. You could have a basic bundle with nothing negotiated and an advanced bundle with this additional content negotiation.

Jeff: I'm not a huge fan of two different section types. But we _could_ do it that way. Hum?

from the chat: Psynder: yes, removing content negotiation here is important. 1) it makes it more likely we'll maintain the benefits of blocking (less likely to fetch multiple versions of the same resource), 2) it makes personalization less likely (though def not impossible of course)

Sean Turner: The discussion in the chat suggests that we could adopt the -04 and then decide how we want to make changes at that point. We can merge these at any point.
No objections from the participants.

Martin: re: negotiation. Thinking about the image case... perhaps we don't need content negotiation for image selection. We can just have clients downscale images if they need to because we're already sending all the bytes to start with. Things like translations need this negotiation more. Sites might do "negotiation" after the fact via scripting, though.

Show of Hands: Should PR 618 to remove content negotiation be merged for the WG doc?
Raised Hands: 5  
Unraised Hands: 4  
Total People: 26  
Sense of the room: Pretty even, warrants more discussion on list.

Jeff: Should we move the manifest section out of the core?

Martin: I think a manifest is another sort of top level thing you might want to go looking for. The question of whether you use a dedicated section for it or whether it's just another thing that is just annotated as manifest is important. Different use cases are going to need different sorts of manifests.

Jeff: So move it out so we can have different kinds of manifests for different kinds of use cases?

Martin: Yes.

Jeff: The current system relies on content negotiation. If we remove that, then this will face challenges.

Sean: We're running out of time, so we're going to have to take some of this to the list.

Daniel: What about an interim?

Sean: We can take it to the list, but I was thinking the same thing.

Show of Hands: Interesting in an interim  
Raised Hands: 9  
Unraised Hands: 1  
Total People: 26
