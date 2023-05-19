---
layout: post
published-on: March 27th 2023
author: Josh Patterson
title: Appendix A - What is Artificial Intelligence
subtitle: O'Reilly - Deep Learning - A Practitioner's Approach
description: In this post we'll .....
keywords: snowflake, snowpark, automl, AutoGluon, pandas, dataframe, whl, pip, anaconda, dependency
meta_og_image: pct_autogluon_dep_og_card.jpg
---

::: {#appendix_ai .section data-type="appendix" xmlns="http://www.w3.org/1999/xhtml"}
What Is Artificial Intelligence?
================================

> Cooper: Hey TARS, what\'s your honesty parameter?
>
> TARS: 90 percent.
>
> Cooper: 90 percent?
>
> TARS: Absolute honesty isn\'t always the most diplomatic nor the
> safest form of communication with emotional beings.
>
> Cooper: Okay, 90 percent it is.
>
> Scene from the movie *Interstellar*

Artificial [ ]{#artint10} Intelligence (AI) is a discipline as old as
the study of philosophy itself. It has evolved over time, yet we still
struggle to find its place in society, let alone the existential
implications for the human race itself. One of the most salient written
lines about the beginnings of AI was by author Pamela McCorduck when she
wrote that AI began with "an ancient wish to forge the gods."[McCorduck.
2004. *Machines Who Think* (2nd ed.).]{contenteditable="false"
data-type="footnote"}

While McCorduck had high-minded prose for the topic, much of marketing
today plays on such aspirational themes yet is actually promoting far
simpler functions in terms of business results. Deep learning comes up
in the context of discussion of AI regularly, and it becomes difficult
to have a directed conversation on the topic.

We added this appendix because the practitioner commonly needs to have a
grounded conversation with customers, executives, and managers about
what deep learning can do for them and how it fits into the AI
landscape. The themes in this appendix are a mixture of a history of the
discipline of AI (for context) and discussions we have had with
customers and industry peers. We seek to provide you, the practitioner,
with the tools to reset the narrative around deep learning, communicate
realistic expectations with stakeholders in projects, and to put them on
ground that will better support their deep learning efforts going
forward. Simply put, the narrative around AI has become overhyped and
eventually the market will correct.

This appendix is also meant to be fun and thought provoking in a way
that stokes the imagination of the researcher or practitioner such that
we can still dream but with our feet on the ground. We\'ll work through
some basic definitions, provides a short history of the topic of AI, and
then look forward to where this all could go. Hopefully we\'ll help
folks avoid the pitfalls of previous cycles of AI interest and better
support their deep learning projects to be more successful through
responsibly setting goals and expectations.​

::: {.section data-type="sect1"}
The Story So Far
================

The main topic of this book, deep learning, is constantly attached to
the term "Artificial Intelligence" in media and marketing. Definitions
are fluid at best and make it difficult to have a discussion on the
topic with other practitioners or stakeholders. Marketing departments
run with the theme of the current hype cycle. Here are some themes from
the not-too-distant past:

-   Smart grid
-   The cloud
-   Big data

When we work in domains like these or in deep learning, as practitioners
we need to ​delineate what is real from what is marketing hype. That
begins with understanding the history of a subject and having solid
definitions from which to build. Let\'s begin by reviewing what we
consider to be deep learning, and then we\'ll dive into the topic of
defining AI.

::: {.section data-type="sect2"}
Defining Deep Learning
----------------------

In   Chapters [\#review\_of\_ml](#review_of_ml) and
[\#fundamentalls\_of\_deep\_networks](#fundamentalls_of_deep_networks),
we laid out a working definition for deep learning that is described as
neural networks with the following properties:

-   More neurons than previous neural networks
-   More complex ways of connecting layers
-   "Cambrian-like" explosion of computing power to train
-   Automatic feature learning

These networks perform the same modeling functions as other machine
learning models (regression, classification) but have also been shown to
be good at tasks such as the following:

-   Generative modeling (e.g., generating art and text)
-   Speech-recognition technology
-   Image-recognition technology

Another key driving feature of deep learning is that it is able to
automatically learn features (as opposed to hand-engineering features)
from data in a domain-agnostic fashion. These capabilities of deep
learning are driving many of the new technology applications and have
stimulated the imagination of many folks beyond technology circles. By
itself, however, deep learning does not have higher-level functions such
as \"automatically understanding the most interesting question to ask a
dataset,\" let alone any type of sentient operation.
:::

::: {.section data-type="sect2"}
Defining Artificial Intelligence
--------------------------------

The   history of AI is fraught with myths, stories, and overzealous
marketing departments trying to tap into the latest technology
narrative. To define AI, we need some context around the history of the
study of intelligence, modern arguments, and how the discipline has
evolved over time.

Using that line as our embarkation point, let\'s explore how the
discipline got its start and then evolved as an industry over the past
60 years.

::: {.section data-type="sect3"}
### The study of intelligence

The  study of intelligence was formally initiated in 1956 at Dartmouth
yet is at least 2,000 years old. The field is based on understanding
intelligent entities and studying topics such as these:

-   Seeing
-   Learning
-   Remembering
-   Reasoning

These topics are components of what we\'d consider intelligent function
to the capacity we have to understand intelligence (and this is a
relative perspective). We can find the study of intelligence throughout
history if we look for it. The list that follows presents a few of the
building blocks of intelligent study over time:

Philosophy (400 BC)

:   Philosophers began to suggest the mind as a mechanical machine that
    encodes knowledge in some form inside the brain.

Mathematics

:   Mathematicians developed the core ideas of working with statements
    of logic along with the groundwork for reasoning about algorithms.

Psychology

:   This field of study is built on the ideas that animals and humans
    have a brain that can process information.

Computer science

:   Practitioners came up with hardware, data structures, and algorithms
    to support reverse engineering basic components of the brain.

The study and application of AI techniques we see today are based on
these fundamentals. We typically see the study of AI broken into a focus
on either behaving or thinking in simulated intelligent systems. We see
these applied in areas such as machine learning applications, basic
knowledge systems, and game playing (e.g., Chess and Go).

However, there are limitations to our implementations of intelligent
study. There are still no good models of higher-order brain functions
such as consciousness. Science has also yet to determine where in the
brain consciousness resides. This leads some to question if
consciousness is even a real function of the brain, but we\'ll leave
that to the philosophers and computer scientists to debate.

::: {data-type="note"}
For Further Study
=================

One of the best books written on the subject of AI (if not the best) is
Stuart Russell and Peter Norvig\'s [*Artificial Intelligence: A Modern
Approach*](http://aima.cs.berkeley.edu/). We can\'t recommend this book
enough for you to get a more complete idea of the depth and history of
AI.
:::
:::

::: {.section data-type="sect3"}
### Cognitive dissonance and modern definitions

When [ ]{#AImodern10}we\'re dealing with a topic such as AI that ties
into so many core definitions society depends on, we naturally find
dissonance around setting ground truth to work from. [Beau Cronin
writes](http://oreil.ly/2sODKk2):

> Like the Internet of Things, Web 2.0, and big data, AI is discussed
> and debated in many different contexts by people with all sorts of
> motives and backgrounds: academics, business types, journalists, and
> technologists. As with these other nebulous technologies, it's no
> wonder the meaning of AI can be hard to pin down; everyone sees what
> they want to see.

Part of the problem with viewpoints and defining intelligence is that we
weave liberally into defining consciousness and then by extension more
philosophical (e.g., \"what is consciousness\") and religious topics
(e.g., \"what is a soul?\"). We\'re touching on some complex territory
at this point and any discussion about the definition of the soul is
fraught with complications. Our best maps today for the definition of
intelligence are covered in regions of "Here Be Dragons." Given that we
don\'t understand natural intelligence, it is even more difficult to
define the artificial variant.

[Dr. Jason Baldridge wrote](http://bit.ly/2tUwIt5) on the topic of AI
and machine learning and talked about how there are conflicting meanings
in play around the topic:

> Regardless of any nuanced technical definition of AI, I\'m pretty sure
> that when the public hears \"artificial intelligence,\" they think of
> conscious nonbiological entities that interact with humans much as we
> interact with each other.
>
> They don\'t think of an expert system that can analyze a complex
> domain-specific problem and provide interesting courses of action, or
> machine learning algorithms that find fascinating patterns in heaps of
> data.
>
> Despite this, the general public seems to find it all to easy to
> mentally close the gap between these two very different levels of
> technological and scientific accomplishment on the spectrum of
> AI-related work.

Dr. Baldridge goes on to define the difference between deep learning and
a full artificial model of the biological brain:

> Despite all this progress, and for better or for worse, these are
> still far from sentient machines. Deep learning is inspired by the
> functioning of human neurons, but as far as I\'m aware, artificial
> neural networks as yet have nothing like the architecture of
> meat-based intelligence

So, we struggle with these definitions because they are complicated and
touch on many topics from many viewpoints. Let\'s take a step toward a
better definition by segmenting the topic and breaking these segments
down into simpler topics.

Francois Chollet recently made the following [salient comment on
Twitter](http://bit.ly/2tUsJNl):

> \[A\]rtificial intelligence is a poorly defined thing, to which many
> people attribute wildly unrealistic abilities. It\'s a recipe for
> trouble.

And then a further [tweet](http://bit.ly/2uz6vhF):

> Part of the problem is that some companies and journalists are hyping
> it up, blurring the line between sci-fi and reality. Because it sells.

Chollet goes on to say that [we should \"define\" what we\'re
talking](http://bit.ly/2u05jXA) about:

> When you talk about \"AI\", \*define\* what you are talking about.
> Make explicit what it can do, and what it can\'t do. Avoid brain
> analogies.

This is sound advice and the industry needs to do a far better job of
locking down these definitions.

::: {.section data-type="sect4"}
#### What AI is not

Folks   who claim machine learning to be AI do the entire computer
science industry a disservice. Machine learning is classification and
regression and in no way matches up to ephemeral aspirations of an
all-knowing, self-aware system that can help the reader with their
marketing problem. As Francois Chollet mentioned earlier, it\'s just
best (for now) to avoid brain analogies.

Many times AI is marketed as an application with all of the answers. It
will not, at least not anytime soon.
:::

::: {.section data-type="sect4"}
#### Moving the goal posts

Psychologists habitually have had disdain for the metaphor of the human
brain as a computer. [In a 2016 article](http://bit.ly/2tABWqX), Robert
Epstein states:

> No matter how hard they try, brain scientists and cognitive
> psychologists will never find a copy of Beethoven's 5th Symphony in
> the brain---or copies of words, pictures, grammatical rules or any
> other kinds of environmental stimuli.

Unfortunately Dr. Epstein has not seen the renders in
[\#major\_architectures\_of\_deep\_networks](#major_architectures_of_deep_networks)
of Convolutional Neural Network (CNN) filter renders. His central
argument in the article is stated as:

> Your brain does not process information, retrieve knowledge, or store
> memories. In short: your brain is not a computer.

This isn\'t a new sentiment and has been echoed, by and large, by the
disciplines outside computer science for the past 60 years. As stated in
Russell and Norvig\'s book on AI:

> The intellectual establishment, by and large, preferred to believe
> that a "machine can never do X."

They go on to demonstrate examples in which AI researchers have
systematically responded by demonstrating one X after another. Thus, the
study of AI and definitions for the discipline have long suffered from
the industry \"moving the goal posts\" with respect to what they really
mean by \"Artificial Intelligence.\"
:::

::: {.section data-type="sect4"}
#### Segmenting the definitions of AI

It\'s useful to break down the different viewpoints of how folks talk
about AI today and list them. [A good writeup](http://oreil.ly/2sODKk2)
by Beau Cronin uses the following four major segmented definitions of
AI:

-   AI as interlocutor
    -   HAL, Siri, Cortana, Watson
    -   Conversational intelligence
    -   Limited reasoning
-   AI as android
    -   Machine in the form of a humanoid
    -   AI as mechanically embodied
    -   Examples would be The Terminator or C3PO
    -   Similar to the interlocutor but in a humanoid body
-   AI as the reasoner
    -   Early AI pioneers were drawn to more refined and high-minded
        tasks---playing chess, solving logical proofs, and planning
        complex tasks
    -   Still struggle with tasks simple for children
-   AI as the big data learner
    -   More recent definition
    -   Seeing many people talk about building \"AI models\"

Let\'s now look at these segmented definitions with a critical eye.
:::

::: {.section data-type="sect4"}
#### Critical commentary on segments

AI as the interlocutor and AI as the big data learner are both recent
definitions due to the incorporation of many machine learning techniques
into engineered commercial products. AI as the interlocutor can perform
basic functions based on voice recognition. It\'s the combination of
voice-to-text machine learning (or deep learning) and Natural Language
Processing (NLP) technology to determine what the user wants to
accomplish. AI as the interlocutor has limited reasoning capabilities
because it typically relies on a separate system to send the
voice-to-text and NLP-processed results as input. This separate system
is many times as basic as a classic rule-base system or \"expert
system.\"

Even though users might be initially entertained with conversation by
the system and even fooled by its \"intelligence," they quickly realize
the limitations of the interactions. Ultimately, AI as the interlocutor
is a well-engineered combination of machine learning techniques that
over time became just good enough to progressively be wired further into
useful consumer products.

AI as the android is an interesting embodiment of the concept yet is
ultimately dependent on a network of machine learning subsystems just as
the interlocutor is. AI as the reasoner is a classical implementation of
AI yet has plateaued in recent years with respect to levels of industry
product integration interest. It continues to be a core component in
intelligent systems that wire together multiple components to produce
value, as in the interlocutor example.

\"AI as the big data learner\" is a troublesome use of the term that has
gained popularity in the past few years (2010--2015). Many times, a
marketing department will rebrand a product\'s use of a basic machine
learning technique over customer data as \"Artificial Intelligence.\"
Worse, other times the product is doing basic business intelligence
functions and is also lumped into this category. The practice of machine
learning (or deep learning) alone should not be considered a type of AI.
It is, however, a useful subsystem of an intelligent system.

::: {data-type="note"}
Showing Restraint When Marketing Deep Learning
==============================================

You should show restraint in labeling a machine learning model---deep
learning model or not---as \"Artificial Intelligence.\" Overselling
capabilities early might attract funding but will hamper your project in
the longer term.
:::
:::

::: {.section data-type="sect4"}
#### A fifth aspirational definition of AI

Another way to frame the question of \"What is Artificial
Intelligence?\" is to ask another question. If we look at this question
from the viewpoint of \"what would definitively end the debate of \'What
is AI\'?\"

If we were presented with a transcendent, conscious, self-aware
intelligence that understood our world (and data) far better than any
human, we\'d probably call it \"true Artificial Intelligence.\" Or, an
alien.

Unfortunately chasing the mirage of AI is what brings on the unrealistic
expectations that always crash down on the industry no matter how much
tangible progress was made. 
:::
:::

::: {.section data-type="sect3"}
### The AI winters

The  AI industry has experienced multiple periods of up and down
interest and funding. These down periods of interest have been the
result of the sector being unrealistically overhyped followed by a cycle
of predictably underwhelming results. This down period is referred to as
an \"AI winter\" and involves cuts in academic research funding, reduced
venture capital interest, and stigma in the marketing realm around
anything connected to the term \"artificial intelligence.\"

The result of these cycles is that the good technical advances (e.g.,
voice recognition or optical character recognition) is rebranded and is
integrated into other products.

::: {.section data-type="sect4"}
#### AI Winter I: (1974--1980)

The lead-up to the first [AI
winter](https://en.wikipedia.org/wiki/AI_winter) saw machine translation
fail to live up to the hype. Connectionism (neural networks) interest
waned in the 1970s, and speech understanding research overpromised and
underdelivered.

In 1973, DARPA cut academic research in the AI domain. The Lighthill
report in the United Kingdom harshly criticized the field and research
funding was further curtailed.
:::

::: {.section data-type="sect4"}
#### AI Winter II: Late 1980s

In the late 1980s and early 1990s, there was overpromotion of
technologies such as expert systems and LISP machines, both of which
failed to live up to expectations. The Strategic Computing Initiative
canceled new spending at the end of this cycle. The fifth-generation
computer also failed to meet its goals.
:::
:::

::: {.section data-type="sect3"}
### The common patterns of AI Winters

The common patterns of these winters see the industry being overhyped by
a series of promising successes. After conditions percolate enough we
see the hype reach a nadir and the money for academic and industrial
research pour into the AI domain. A few real projects based on solid
technology reach at least part of their goals and solve real problems.
Most of the marketed promises go unfulfilled, however, and the Trough of
Disillusionment looms.

Winter kills the weak.

A few interesting applications slowly emerge from the trough, are
rebranded (\"voice recognition\"), and are integrated into other
projects as features, generally under the \"latent intelligence\" class
of improvements. We\'ve seen this with the following:

-   Informatics
-   Machine learning
-   Knowledge-based systems
-   Business rules management
-   Cognitive systems
-   Intelligent systems
-   Computational intelligence

The name change might be partly because they consider their field to be
fundamentally different from AI. It is also true that the new names help
to procure funding by avoiding the stigma of the false promises attached
to the name \"Artificial Intelligence.\"

Here\'s an interesting note from an AI meeting in the 1980s:

> At the meeting, Roger Schank and Marvin Minsky---two leading AI
> researchers who had survived the \"winter\" of the 1970s---warned the
> business community that enthusiasm for AI had spiraled out of control
> in the \'80s and that disappointment would certainly follow. Three
> years later, the billion-dollar AI industry began to collapse.
:::
:::
:::

::: {.section data-type="sect1"}
What Is Driving Interest Today in AI Today?
===========================================

Three  major contributors are driving interest in AI today:

1.  The big jump in computer-vision technology in the late 2000s
2.  The big data wave of the early 2010s
3.  Advancements in applications of deep learning by top technology
    firms

In 2006, Geoff Hinton and his team at the University of Toronto
published a key paper on Deep Belief Networks (DBNs).[Hinton, Osindero,
and Teh. 2006. ["A fast learning algorithm for deep belief
nets."](https://www.cs.toronto.edu/~hinton/absps/fastnc.pdf)]{data-type="footnote"}
This provided the industry with a spark of creativity on what could
possibly improve the state of the art. We\'ve seen a tsunami of deep
learning publications at top journals over the succeeding decade. These
publications began improving top scores for accuracy in many areas
beyond just computer vision, and deep learning took over the applied
machine learning landscape in short order.

Large web firms such as Google, Facebook, and Amazon all watch top
journals for the best ideas. These firms saw the developments by Yann
LeCun, Hinton, and others and began implementing these ideas in their
own pipelines. These new applications (e.g., better face detection, or
Alexa at Amazon) were widely recognized in the technology media.

In the mid-2000s much of the storage and ETL technology developed on the
West Coast by the large web firms began to be open source as projects
such as Hadoop and MongoDB.

Just as these web firms (Google, Yahoo!, etc.) had ramped up their
storage and ETL systems, they were then building out new machine
learning and deep learning techniques to better take advantage these new
and larger datasets.

Traditional *Fortune 500* enterprise companies were bringing online
large distributed systems in the early 2010s to hold their growing
transactional datasets. These enterprise companies tend to follow what
the West Coast web firms do by about 5 to 10 years. This has given rise
to an interest in deep learning in the *Fortune 500* and in systems that
allow the traditional enterprise to better exploit their investments in
big data.

If we combine the aforementioned three factors and then mix in the very
public successes of projects such as Watson (winning *Jeopardy*),
AlphaGo (winning Go), and Google\'s self-driving cars, we create an
environment in which enthusiasm outstrips the reality of the road ahead.

It\'s high tide in coverage and enthusiasm around AI. Unfortunately, in
these types of cycles, we also see the tide go back out eventually.
There are real applications using complex datasets for deep learning.
Here are just some of these applications:

-   Healthcare (e.g., predicting patient length of stay)
-   Retail (e.g., analyzing the shopping experience)
-   Telecom/Financial Services (e.g., analyzing transactions for
    fraudulent patterns)

We\'ve touched on some of the aforementioned use cases (and more) in
this book. When you, as practitioner, promote deep learning and AI we
recommend finding real use cases such as these and standing on \"solid
ground." We mention solid ground here metaphorically because eventually
the tide will go out and we hope our fellow practitioners will have
something to stand on when it does.
:::

::: {.section data-type="sect1"}
Winter Is Coming
================

Deep learning in and of itself has been grounded in reality over the
course of this book. It is a framework for performing industry-leading
neural network modeling on complex data types. Deep learning, by itself,
would not fulfill our aforementioned fifth aspirational definition of
AI, so we don\'t have much to worry about on that front.

We are seeing systems marketed in 2016 as \"Artificial Intelligence for
X,\" which are plainly using basic machine learning. AlphaGo was a
tremendous advancement in game playing, but as we saw with DeepBlue and
Chess, game-playing advances do not always translate easily to business
use cases.[*Jeopardy* does seem to be a \"solved problem,\"
however.]{contenteditable="false" data-type="footnote"}

Marketing departments are setting up similar scenarios as occurred in
the previous two AI winters, unfortunately. The coals of the real
advances in the domain, as in previous winters, will keep the true
enthusiasts and hardcore researchers warm during the cold of the coming
third AI winter. 
:::
:::
