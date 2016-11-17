---
layout: post
title:  "Teach Protocols"
date:   2016-11-17 13:15:00
categories: wisdom
---

> Teach protocols, not languages.
>
> -- <cite>[Joe Armstrong](https://de.wikipedia.org/wiki/Joe_Armstrong)</cite>



This was said in the context of fitting things together:

    Old timer here ...
    
    When I learnt programming (1967) ,
    I could choose between FORTRAN and (it was rumoured, Algol)
    but nobody knew anything about Algol so it was FORTRAN.
    
    The turn round time for a program was three weeks
    
        week 1 - write code on paper forms - send to computer center to be turned into punched cards
        week 2 - review punched cards, if ok send to machine
        week 3 - results
    
    The compiler helpfully stopped at the first syntax error which got you back
    to week 1 -
    so if you had say ten errors in your program it would take 30 weeks to get
    it running.
    
    This is a pretty good environment - teaches you not to make mistakes and to
    think first.
    
    By about 1970 I was at university and turn round times were down to 4 hours
    and you could punch your own cards - it was still FORTRAN
    
    By 1974 I got access to a computer -- a honywell DDP516 - with a colossal
    32 KB memory.
    So the 474 pass FORTRAN compiler could compile a hundred line program in
    less than a week
    (or so ...)
    
    Things improved - I went to CERN and used the CRAY1 this could compile 100K
    lines of
    FORTRAN in 1 picosecond (ie about a zillion times slower than my mobile
    phone today)
    
    Still Fortran.
    
    In 1974 (ish) I got to play with a DEC10 - Now I could write FORTRAN,
    Basic, assembler
    and it had time-sharing (wow) turn round times of seconds. If I'd been In
    the USA I'd be Bill Gates,
    but this was Edinburgh.
    
    In 1976 I got a job programming a NORD10 in FORTRAN/Assembler and it was
    really fast
    turn round times of seconds.
    
    In 1980 ish I was still programming in FORTRAN - I forget the name of the
    machine
    all files were in one directory, no full-screen editor, no revision control
    system,
    I wrote about 150K lines of FORTRAN for it.
    
    1985 I joined Ericsson - wow a VAX11/750 - new languages to learn. Bye bye
    FORTRAN
    
    I learnt (with various degrees of proficiency) Lisp, Prolog, awk, bash,
    smalltalk, TCL,
    and became proficient in Prolog (aggghhh - the beauty ....)
    
    I also played with just about any language I could get my hands on (ML,
    forth, ...)
    
    Then I (1986) got into my Erlang Phase (I couldn't really learn Erlang,
    'cos it didn't exist,
    so I invented it) - it was really an outgrowth of Prolog+Smalltalk with a
    bit of error recovery
    concurrency and distribution throw in.
    
    Then I learnt (badly) C - But Mike Williams said my C was crap and looked
    like Fortran so he
    binned my C ... (why use malloc and free and pointers anyway ...)
    
    I saw C++ coming and read the book - or at least tried to read the book -
    there's a dent
    in the wall behind my piano, where the book hit the wall - Improvements to
    C should make things
    easier not more complicated, I thought.
    
    Time passed.
    
    I tried Java (not impressed, ok it's better than C++, but oh so verbose, I
    used to get
    programmers "white fingers" when programming FORTRAN you have to write
    hundreds of lines
    to do the smallest thing - Java seemed similar - so verbose) - I also
    (later) tried
    Python (ok), Ruby (ok), Lua(better), Javascript(I like :-)
    
    It's actually taken me quite a long time to learn all these languages, and
    they didn't
    all come at once. I had a good 15 years of FORTRAN - long enough to get
    good at it,
    10 years of Prolog, 20 years of Erlang etc.
    
    I also had a long time to assimilate the new ideas - the ideas in
    programming come pretty slowly
    - once every twenty years or so somebody has a really good idea,
    programming
    today hasn't improved much in the last 20 years - it was mess then and it's
    still a mess.
    
    IDE's and revision control systems have just made matters worse - now you
    have all the
    old versions of the mess as well as the mess itself, and the IDE means you
    can't even see the mess.
    
    The best IDE in the world is your BRAIN - it's a zillion times better than
    these
    clicky things.
    
    What's this got to do with education?
    
    Suppose you're starting off.
    
    You can choose between twenty odd languages (all of them good for one
    reason or another)
    what took me 40 years to learn, you must try to understand in 2-3 years,
    this is just not possible.
    
    What languages should a beginner learn, what languages should a school
    teach?
    
    Now we get to the paradox of choice - because there are so many
    alternatives it becomes
    impossible to choose.
    
    Old timers say "choose the language appropriate to the problem" when you
    know 20 odd languages (with varying degrees of proficiency) this is easy to say - but If you know two languages Java and C then this isn't much help.
    
    There are literally problems where the solution in a CLP language is a few lines
    and is thousands of lines in C.
    
    What would I recommend learning?
    
        - C
        - Prolog
        - Erlang (I'm biased)
        - Smalltalk
        - Javascript
        - Hakell / ML /OCaml
        - LISP/Scheme/Clojure
    
    A couple of years should be enough (PER LANGUAGE).
    
    Notice there is no quick fix here - if you want a quick fix go buy "learn
    PHP in ten minutes"
    and spend the next twenty years googling for "how do I compute the length
    of a string"
    
    The crazy think is we still are extremely bad at fitting things together -
    still the best
    way of fitting things together is the unix pipe
    
        find ... | grep | uniq | sort | ...
    
    and the *fundamental* reason for this is that components should be separated
    by well-defined protocols in a universal intermediate language.
    
    Fitting things together by message passing is the way to go - this is basis
    of
    OO programming - but done badly in most programming languages.
    
    If ALL applications in the world were interfaced by (say) sockets + lisp S
    expressions
    and had the semantics of the protocol written down in a formal notation -
    then we could
    reuse things (more) easily.
    
    Today there is an unhealthy concentration on language and efficiency and
    NOT on how things fit together and protocols - teach protocols and not
    languages.
    
    And teach ALGORITHMS.
    
    Cheers
    
    /Joe
    
    (The dates in the above are approximate)
