# Minutes

## Logistics

Date: Wednesday, March 25, 2020

Time: 20:00-21:30 UTC

Location: https://ietf.webex.com/ietf/j.php?MTID=mf340ca56e8214dc9fe2dd3c6f9f3047f

Scribe: Peter Wu

Jabber Scribe: Ted Hardie

## Agenda

11min - technical issues (#chair fail)

05min - Administrivia - Chairs

05min - Use Cases - Chairs

Protocol:

20min - Bundle Protocol - Jeffrey

    draft-yasskin-wpack-bundled-exchanges

Security:

15min - Digital Signatures - Jeffrey

    draft-yasskin-wpack-bundled-exchanges
15min - Content-Based Origins for the Web - Martin

    draft-thomson-wpack-content-origin

10min - Comparisons of Security Options - J/M

The WG bashed the Use Cases off of the agenda. The were meant to be an introduction in case the WG was not chartered. But, it was and the chairs fumbled starting the meeting so the agenda item was dropped.


## Protocol

20min - Bundle Protocol - Jeffrey Yasskin 
    
[Slides](https://datatracker.ietf.org/meeting/107/materials/slides-107-wpack-web-bundles-00)

[Draft](https://tools.ietf.org/html/draft-yasskin-wpack-bundled-exchanges-02)

EKR: what are desirable properties for random access?

Jeffrey: The design so far so far allows you to skip to the image, and allow you to start using it.
If these have integrity attached, can use MT Merkle Tree integrity for it.
There may be use cases for videos to chop it up of half of it, but as parties split a video file in smaller files it may not be needed.

Murray Kucherawy: what does "Do we need content negotaition within a bundle?" mean?

Jeffrey: You can have several representations per URL. You can have an image and HTML page for the same URL, or language for the same URL, and use the Accept or Accept-Language header for this.
Do we want to use that, or require separate URLs?

MT: (is not comfortable discussing details such as URIs at this point)

Jeffrey: the draft will change in the next weeks, removing and adding more text as needed.

EKR: what is the relationship between things in the bundle, and outside the bundle?

Jeffrey: Goal is to take stuff from the bundle, and pretend it came from an authorative server.
Things under the same part that seems pretty safe, but it has to come from consensus whether we want to do it.

Yoav Weiss: some use cases need resources outside. (incomplete minutes)

Jeffrey: (no further comments)

## Security

15min - Digital Signatures - Jeffrey Yasskin
    
[Slides](https://datatracker.ietf.org/meeting/107/materials/slides-107-wpack-signer-origins-00)

[Draft](https://tools.ietf.org/html/draft-yasskin-wpack-bundled-exchanges-02)

(no questions in the queue)

15min - Content-Based Origins for the Web - Martin Thomson

draft-thomson-wpack-content-origin
    
"Content-based Origins for the Web". [Slides](https://datatracker.ietf.org/meeting/107/materials/slides-107-wpack-draft-thomson-wpack-content-origin-01)
[Draft](https://tools.ietf.org/html/draft-thomson-wpack-content-origin-00)
 
Larry Masinter: you sign the presentation of a package instead of a transaction. (long story, couldn't catch it)

mnot: considers web packaging as packing up something, sign it, extend lifetime periodically. But here some identifier is attached. Is concerned that TTL for cached resources are easy to get wrong.

Ben Schwartz: ...

Watson Ladd: suggests that cosmetics (CSS) should not require changing the whole bundle.

Yoav Weiss: Since the origin is hash-based, should it change when the content changed?

EKR: name things not by contents, but by signature keys.

Ted Hardie: move from unsigned context to a signed context, a transfer between both would be useful. How does this relate to Signed Exchanges?

Ted: Part of this is ensuring the "web" is available when "the Internet is withdrawn" (or not available)

MT: Don't think this is an alternative to Jeffrey's proposal. Just eliminating a few other proposals
in this space.

Devin Mullins: AMP is offline by choice for resources that does not need an authoritative origin. (+some comment about IndexedDB)

## Comparisons of Security Options - J/M

Jeffrey & Martin presenting

EKR: can you clarify "Show the signer's origin in the URL bar."

Jeffrey: Signed Exchanges is about the intermediate state before you retrieve the version from the content origin.

Daniel Kahn Gillmor: use case with changing an email draft offline, then going online, what hash/URL to show for the content? (<-- could be totally misrepresenting the question)

Daniel Kahn Gillmor: are we contemplating representing authenticated proof of non-existence?  (by analogy with how NXDOMAIN doesn't work for DNSSEC, how are we handling HTTP 404?)

Mike Bishop: comment about the origin display, probably the most understandable origin is when it was signed or last validated. If it is offline, just tell it was from three weeks ago. In terms of transition to online state, it is not binary accept/reject, but also "it is old".

Wendy Seltzer: I am interested in the relation between origin and signer, and user. How much are we shifting away from the end-user who may to do something else with it. Anonymity, or changing the content. Just a thought.

15min - Open mic

N/A
