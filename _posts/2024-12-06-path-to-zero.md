# Breakpoint: path to milestone zero

One of my favourite things about engineering and in particular, about
programming, is very well summarised by this gif. I have it saved in my
computer, that's how much I like it

[!deep puddle](/assets/deep_puddle.gif)

I also vaguely remember an XKCD comic about the same topic. Programming is,
effectively, about **side quests**. I can't find the comment, please shoot me an
email if you know what I'm talking about.

## Side quest 1: The blog setup

I'm trying to do a blog. I have a concept, I have a project that I want to write
about. Great. First side quest: how do the kids blog these days? Huh. Or at
least, how do software engineers do? Out of sheer accident, I found out that Git
Hub has this nice static page hosting--oh, and it supports custom domains, will
you look at that!

So side quest number 1.1 [1] is surprisingly short due to my lack of
investment into finding a correct blog platform. Praying that won't bite me too
much, or at least too soon. [2]

On to side questi 1.2: how do I use this thing? Luckily for me, Git Hub put
together a Valve-level tutorial, which was very clear, so here's me using that:
https://github.com/royalsflush/skills-github-pages.

Great, so now I know how to create the first post. I'm still aware that my
resulting site looks hideously confusing (still in
https://royalsflush.github.io/skills-github-pages), but I decide to let that
slide because I'm sure at that point it's not gonna be a problem. (
Foreshadowing...)

So I go on my merry way, write the README trying to think about the conceptual
approach of it all. I'm pretty excited about this. I think the idea is not a bad
one, and I'm definitely keen to playing with some fancy 3D visualisation tool
in React to plot spinning graphs of my blog posts. That sounds pretty fun. I
also dig the idea of giving a blog reader a structure to explore a story without
tangling a bunch of different subjects. It feels like a cool way of consuming
content that is not the complete randomness of a blog (so it also has some
linear discovery), but it's not a book. Anyway, I'm excited!

So I turn on my Git Hub pages, and it shows me the README in all its published
glory. I also have a domain (breakpoint.royalsflush.com) that I want it
primarily. Time for some domain wrangling.

## Side quest 2: domain wrangling

I go to my domain provider, configure a CNAME record--this one I have
done plenty of times. And now, I also own royalsflush.blog. Hm. That should
redirect to breakpoint.royalsflush.com. And now I'm thinking: how can I do this?
Normally CNAME only redirects to a specific domain, can I do a wildcard
redirect? Short answer: no. [3] Slightly longer answer: CNAME only works for
specific subdomain, and if you want a full on redirect, you want an HTTP
redirect instead (https://en.wikipedia.org/wiki/URL_redirection).

Now I'm thinking I'm gonna have to configure an Apache server to do an HTTP
redirect, and I'm sighing... until I realise my domain provider offers
forwarding as a service. Side quest done!

Ha, of course not. I try to access royalsflush.blog to see my post, Chrome gives
me a security warning. Me, in my diligence, put a redirect with SSL, and I
quickly learned that SSL certificates are not for the entire domain (superbly
explained in https://serverfault.com/questions/566426/does-each-subdomain-need-its-own-ssl-certificate).
I have decided that this is not my biggest issue right now, because I try with
breakpoint.royalsflush.com (which works), and nothing is showing correctly. 
Issue count += 2 [4].

## Side quest 3: debugging Jekyll locally

Okay, so Git Hub recommends me to install Jekyll locally and try things out,
which, I dig. I see I have a version of `gem` installed, let's do it (I wasn't
expecting that!). Then, of course, my version is super old because it has been
shipped with the dev tools of my MacOS. Okay, so `gem update --system`. Now it
complains my **ruby** version is old. Side quest 3.2 it is.

https://www.ruby-lang.org/en/documentation/installation has some pretty good
detailed info, but it doesn't tell me a crucial piece of information: do I need
to support multiple versions? Or can I just go the Homebrew [5] route and call
it a day? I'm wary that I'm gonna some obscure thing that uses the system
version. https://mac.install.guide/faq/change-ruby-version confirms my
suspicion. Let's pick up RVM and do a combo installation [6]. Which in turn
requires gpg2 for keys, so I ended up using homebrew anyway.

And now, to cap this post about side quests:

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

gpg: keyserver receive failed: No route to host
```

To be continued...

---
[1] Because remember, the blog itself is not the main project, Minesweeper is.
But I want to write about Minesweeper, and now I want a blog to do it so, here
we are.
[2] It's my current belief that no design decision
survives the stress test of platform evolution, be it scale, usability, new
features, etc etc.
[3] I also get side tracked by the fact my domains don't have adequate
protections, so I get on to fixing that as well.
[4] https://github.com/royalsflush/breakpoint/issues/1 and
https://github.com/royalsflush/breakpoint/issues/2
[5] I decided to install Homebrew anyway, which I used to have and I don't in
this machine.
[6] Here if you need: http://rvm.io/
