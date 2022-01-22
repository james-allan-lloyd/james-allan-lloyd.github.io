Title: Story Development
Date: 2021-09-17
Category: Agile
Slug: story-development
Status: draft

Stories and the writing thereof are right at the pointy end of software
development, the interface with between business and development. In every
company I have ever worked with it has been a point of contention or neglect.
The classical refrains when the software is actually "inspected" by stakeholders
are: developers saying "but they didn't specify this behavior" while the
business says "this is not what I asked for".

There are many approaches to this thorny problem and what follows is mere my own
humble take on the situation.

# Story vs PBI
Do you use Jira? If so, how do you use it? Is it a big list of things that you
shouldn't forget to do? This is how I've seen most development teams use it.

Instead think of Jira's primary role as a communication mechanism between the
business and development. Hell, not even communication: collaboration. We're not
doing waterfall here people and requirements do not simply flow down.

This is of course easier said than done. Getting anyone in the business to look
at Jira is battle in and of itself. But that doesn't mean we shouldn't try, and
we shouldn't be putting up barriers that lose that battle before its even
fought.

Get into the habit of making your stakeholders look at the backlog, and if
they're not engaging, then obviously your backlog is probably not structured in
the right way.

The backlog is a list of things that have not been done yet, in an order that
you anticipate them being finished. For the developers, it is enough that the PO
says this is so, but for the PO: it is your job to get stakeholder buy in for
this plan. That doesn't mean they have to sign off on it - you're not going to
get it, stakeholders all have their own priorities - but they need to at least
understand the ordering and have given you all the information required to make
sure that ordering delivers the most value over a continuous time-frame.

*The PO is not the business* : they are proxy, but they're naturally going to
understand a lot more than the stakeholders do.

To this end, make sure that the titles of your *stories* have business relevant
titles, and the initial words of the summaries are for your stakeholders.

Ensuring this happens is a lot easier if you stay on the right foot from the
moment of creation.

# Features vs Stories
Features are not stories! This has been a constant struggle not only in the
companies I've worked with, but within myself. It's so damn hard not to jump to
the implementation, or name the problem as a feature. But resist! Every story
should be a statement of a problem to be solved, first and foremost, where a
problem could be affecting a customer, end user, the business or even the
development team.

What happens if we rush to this "feature driven" thinking? We can easily start
constraining the problem to the feature, ignoring other possibilities. You're
essentially coupling your solution (or your interface) to your implementation
details. It wouldn't be great software design, and it's not great story design
either.

But where do we record the features, the design decisions, etc? It's not in the
stories, that's for sure. One option is acceptance tests. Another option is a
design page on your wiki of choice. Maybe it even references back to the
motivating story.

Remember: the product backlog is a communication mechanism between the
stakeholders and the team. Traditionally stakeholders don't give a hoot about
implementation details, and if they do, it's usually the wrong ones.

Keep your team-stakeholder interface clean and stay away from implementation
details until absolutely necessary. When is it absolutely necessary? It's when
you're asking the PO if a given solution is acceptable to them. That doesn't
have to be baked into the story before the sprint starts.

# Creation
Stay in the problem domain as long as possible. Don't get bogged down in
solutions. The most important thing when creating the story is getting the why
are we doing this, why should we do this now, why should we do it in preference
to anything else. Ie, the value.

Once you have the value clarified, then you can start looking at the details.

Certainly don't start worrying about implementation. The implementation ->
sizing cycle takes place later, where we start refining the value.

Odds on, this initial story will probably be huge. Resist the urge to estimate
it. Resist the urge to create a Jira epic for it just because of its hugeness.
Why do this? Isn't this what Jira epics are for? Kind of.

What I've seen when you use the Epics are big, business case level items is that
it tends to lead down a path over-specification. People like architects want to
"own" the Epic rather than collaborate around it. It also becomes hard to
prioritize and finish these epic level features. It also means that your product
backlog isn't a priority to ... ahem... -prioritize. The business and POs end up
trying to prioritize the big things (which is really hard) while leaving the
teams to prioritize the little things in isolation.

# Refinement and Slicing
So you've got your big, business goal story with some acceptance criteria
written down about how you're going to tell if it's successful and worth doing
at all. Maybe you've taken a look and reckon that it might be 2-3 sprints of
work.

How do you even start?

# Taking a Bite
You take your first bite. If it's bigger than a sprint, what's a part of it that
can be done in a sprint. Make that a sprint goal

Actually, don't treat stories in isolation. The first priority is getting your
backlog in order. Suppose you have 3 "top stories" (you lucky dog, normally I
have 10 and they're all equal and top priority!). Probably your PO and
stakeholder discussions aren't yielding a way to prioritize them. Listen. Find
out what the subset of importance is in them.

# Who Should be Involved
Who should be involved in Agile specification? Everyone if possible, all the
disciplines if that's not practical. Why?

Agile specification is agile planning.

I guess this separation of planning and specification is also a leave over from
the waterfall times, where people pretended they knew everything about a
software project before they started implementing, so specification was
something that was done in the plan, or was required before the plan could
start.

In an Agile mindset, we are instead asking, "What should we plan to do next
sprint? What should come after that?" without requiring the need to specify
everything. Does this scare you? Maybe. But what scares me more is the thought
of producing detailed specifications that are destined to be thrown out once the
real work begins.

You don't know what you will need to specify and more than you will know how
long the code will take. You probably know the most important things though, so
trust in yourself on that and trust that you will be able to respond to
discovering new important things.

1. Order your big items. If you can't choose between some items, note them down
   as a group (maybe with a label in Jira)
2. Look at the first big item. What is the most important part of this? What's
   the biggest bang for buck? What is urgent to be done in the next sprint?
   Split this into a story on its own, and update the original story to be along
   the lines of "And the rest"

For example, suppose you want to use two factor authentication for login. The
story reads as "Users are required to use two factor authentication" with a list
of the common authentication methods being supported as acceptance criteria.

    Story: Users are required to use two factor authentication when logging in
    Acceptance criteria:
    - Users can use email as their second factor
    - Users can use SMS as their second factor
    - Users can use Google Authenticator as their second factor

Maybe you determine that email is the easiest to implement first. So we split it
like this:

Split story:

    Story: Users are required to respond to an email when logging in
    Acceptance criteria:
    - Users can use email as their second factor

Remainder story:

    Story: Users are able to use other common forms of two factor authentication
    Acceptance criteria:
    - Users can use SMS as their second factor
    - Users can use Google Authenticator as their second factor

If you're an engineer like me, you're probably already starting to specify other
acceptance criteria for the email story, like timeouts and error conditions,
etc. These are probably fine to add to this new story, but don't spend too much
time on it - we still don't know when or even if we're going to implement this
thing. There are many other stories to refine, or even this story may be broken
if it's determined to be too big to implement in a sprint.

Process:

1. Ensure the Product Backlog is ordered such that the immediate goals are at
   the top.
    1. If you can't choose between two or more items, you will need to make a
       split on value. What is actually important in each story? If you split
       out the important parts, does that make it easier to prioritize?
    2. If you find prioritization is dependent on how long something will take,
       ask the engineers for an order of magnitude estimate, or a comparative
       estimate (which of these stories will take longer?)
2. Once you have a product backlog that is nominally ordered on value, or where
   you're getting to the point where you're trying to prioritize or split beyond
   a 3 sprint horizon, stop.

# An even more radical approach to Sprint Planning
Plan your sprints first. As in, come up with a goal for the next 3 sprints. Then
look into the backlog, which you've prioritized, and figure out what to pull in
from each of those stories in order to meet these goals.

# Over-specification is Waste
Sometimes I feel I'm crazy, banging heads with more detailed oriented
developers. How can we possibly estimate things unless we know all the details?
An understandable position, if scope was fixed, but in an agile way of working
it is not. This is what I believe the agile estimating approach should be:

1. Look at the goal-oriented acceptance criteria
2. Estimate a gut feeling for how big the time-box is to achieve that acceptance
   criteria, or the spirit there of.
3. Try to get the maximum value into that time-box to achieve the most of that
   acceptance criteria, possibly taking some extra time if you think it's worth
   it.
4. Note the stuff that you haven't done. Document as known issues. Plan that for
   next time.

Contrast with the normal flow of trying to detail everything and form an
estimate, and then still being wrong, but you've "promised" the details, maybe
you didn't even focus on the most important details because they were all
equally important since they were all required.

Why do we do this? The worst feeling as a developer is being accused of not
thinking of something, I suppose. That terrible, gut wrenching feeling of being
accused of not knowing everything in advance. And yet we repeat the same pattern
of trying to detail everything in the hope that this time we will be right.

That time is better used making sure we do the most important things and
trusting that we'll get to the other details later, if we really need them at
all.

Oh, I actually didn't relate this back to the lean waste of inventory: having
too much specification sitting on a shelf (in this case the product backlog) is
also a waste. Its actually a sub-optimal situation to have detail on items
further down in the backlog. The effort spent putting these requirements on a
shelf would be better spent any other way: say, checking that the implementation
is sufficient and looking for edge cases to implement.

# Mistrust is Waste
I was listening to a podcast the other day about relationships, and the host
referenced a study about how one of the biggest drains on efficiency in the
modern workplace is a lack of trust. The overhead of having to specify
everything because you can't trust your workers to do anything more than exactly
specified, or do it in the wrong way.

Even worse, lack of trust is often responded to with a feeling of helplessness:
the inability to decide things unless they're specified.

As a manager, you should be aiming to trust your developers. Give them the
information they need, be available, and occasionally correct when you see them
going off course. What you lose in a given sprint will be paid back by increased
self-organization and empowerment in the following sprints.

# Sizing and Estimating

# Days vs Points

# No Estimates and Right Sizing

# Acceptance Criteria