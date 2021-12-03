WPACK @ IETF112

Note taker: Justin Richer

# Use Cases Document

presented by : Jeffrey

- Some use cases to be split to appendix
- reqs will be split out

anything that shouldn't be in appendix?

Shivan: what about subresources? these are ordered by priority?
Jeffrey: roughly, yes; we were looking at ways to compete with native apps.
... we can get partway there w/subresources and focusing on these first

David: mime/multipart? (from Larry), keeps coming up; haven't seen energy in the group for it
Jeffrey: multipart scheme competes w/bundle format; multipart is set of formats rather than use cases, not clear what use cases we're missing here
... use cases we've listed seem like the ones we want to focus on
David: will follow up on list, will request Larry follow up w/actual suggested text
Jeffrey: think we replace some parts w/bundles, not clear what else would need to change

Sean: implementation experience discussion now?

# Bundle Preloading
Presented by: Felipe 

Felipe: general approach: declares bundles to pre-load
... server replies with bundle of resources
... origin/path restricted
... for a given URL server must return same request

... last meeting (111), discussed changes
... simplifications (removal of items)

... tool support: nodejs module to create and read bundles, updated to newest version of spec
... can implement bundle-aware server
... supports old and new version

... can also be used in browser, prototype preloading

... insights: approach works, reasonable performance
... good way to experiment w/syntaxes

Sean: is there any reason the way you're going wouldn't work with other use cases?

Felipe: not necessarily; some use cases are pretty specific, not sure they'd work with this JS prototyping
... more of a general thought of whether we can try out other scenarios
... trying to find areas where people are interested in trying out

Jeffrey: some long-term use cases like installing webapps w/accurate trust, can't be prototyped in JS b/c of need to bootstrap
... chrome-origin trial use case (ads are being served as self-contained resources) could be prototyped this way

Felipe: you should just need to load the bundle for those

Shivan: believe preload is the way to go, client can choose which resources; wish original trial had gone with that
... any other things where client can't choose is non-starter

Felipe: want to try out some benchmarks; what happens if client requests lots of resources?

# The Bundle (binary formats)
Presented by : Jeffrey

Jeffrey: biggest question recently is how to interact w/HTTPWG binary HTTP format
... direction seems to be to try to converge them, even though it would lead to changes in bundle format

David: Martin Thompson isn't present, is working on binary representations
... convergence would be good, need to see what issues come up and work them out

Sean: we should try to achieve consensus to use one format; separate formats is recipe for disaster 🧑‍🍳💣

David: propose resolutions and discuss on the list

# Discussion

Felipe: clarify next steps in use case document

Jeffrey: you mean, how we make decisions about what to change in the use case document?

... next steps are to send a PR to re-org document to list for comments

Sean: if you update the document, people will comment
... I highly doubt it's going to be that easy
... submit version as-is, submit changed version so you can see diffs

... do it in the github, any questions referred to the list
... should get WPACK set up with auto summaries for github

Sean: we do have other drafts in our SoW, we need to begin engaging on those
... there are other things that need to get done first, but if oyu want to start working on those, go ahead


