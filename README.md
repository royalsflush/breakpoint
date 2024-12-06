# Breakpoint

This is a blog, but it's not a tutorial, it's not packed with answers, it's just
a journal-type blog. I want to register my own journey through learning some of 
these technologies. I want someone's experience when reading the blog to be
following the journey as well.

## High level concepts

At its heart, this is a blog. However, as I have described, I want it to read a
lot more like a messy journey of exploration than something that you just 
consult when you're not sure how to solve that particular LeetCode problem, or
how to model your database for a particular functionality.

I have two concepts that I want to initially focus for Breakpoint:

* Learning DAGs
* Tag forests

Let me go over my conceptual idea of each.

### Learning DAGs

This is supposed to be a story. An initial article is going to kick off a
particular theme, and I expect that I'll be referencing it in other articles
related to the same topic. So naturally, they form a DAG. I would like for
readers be able to see the latest updated DAGs.

### Tag forests

Blogs need to be filtered by tags, but I'm also pretty interested in a couple of
things:

1. Can I plot all the articles in my blog and see how the tags cluster?
2. How do the learning DAGs relate to tagging? Is there going to be a lot of 
   overlap?

Maybe this one is just a fancy visualisation of the blog itself...

I still think that the concept of tags is useful and interesting. Perhaps we
want to search for a tag (or an adjacent concept) and get the relevant of each
of the learning DAGs? Okay, so I think now I have a good idea of what I want to
be doing, let me do a brief roadmap

## Roadmap

### Milestone zero: MVP

* MVP is just a blog, no fanciness. In particular, I want:
  * A Jekyll powered blog that is in this GitHub repo
  * It's published to GitHub pages
  * It uses breakpoint.royalsflush.com
  * It has a first post detailing the intention of the blog and mulling over
    some of what I already mentioned here -- I think that, for maximum historic
    coolness, I think I want a frozen version of this README. That seems pretty
    neat.

### Milestone half: Google analytics

* TL;DR: I want to have analytics for my blog. I don't think those will amount
  to anything exciting, but I still want them.
* Then I want some blog posts. I'm still finishing my minesweeper project, I
  think that's the perfect candidate for my second learning DAG (the first being
  breakpoint itself). The reason I'm gonna defer structuring the learning DAG
  idea is because I need to understand a bit more about how posts are even going
  to be structured, and what makes sense.
* I'll add manual tags to the blog posts for now
* When I finish minesweeper (see the milestones in
  https://github.com/royalsflush/minesweeper), I'll go over the posts for that,
  and any other content I have produced in the meantime and try to distill the
  data model for learning DAGs. I'm pretty sure we're going to have an N:N
  relationship for both learning DAGs and tags

### Milestone one: Initial learning DAGs in the home page

For this milestone, I want to define better:

1. What are learning DAGs? Sure, they're graphs, but how do I want the
   experience for the reader to be? Should they suggest an order of posts that
   goes through a particular project? Perhaps a technology?
2. Are those manually curated, or are they auto-generated? I can see that I
   might want to make the first learning DAG manually curated. That's a good fit
   for projects, but I think I also want to have an arc for the technologies
   (React? Express? Node? Etc etc), and for areas (system design? Frontend?
   Languages?). I think it's an interesting experience, but it's definitely a
   challenge to structure the story.
3. How is that going to appear? I think I want a 3D render of the DAG, like a
   Metroidvania level. I don't know, that sounds pretty cool.
4. I think when you click on it, you probably want the flattened graph, with
   the title of the DAG at the top, then each vertex has a header (the title of
   the post itself) and a summary of the article (potentially AI generated? Why
   not?)

Edit: I think I settled on (1) -- I want projects, technologies and topic (which
is a broader categorisation). 
