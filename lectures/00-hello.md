---
title: Hello, world!
headerImg: sea.jpg
date: 2017-03-28
---

## Who am I?

![Nadia Polikarpova](https://cseweb.ucsd.edu/~npolikarpova/images/nadia_polikarpova.jpg){#fig:nadia .align-center width=25%}

- Assistant professor at CSE since 2017
- PhD at ETH Zurich
- Postdoc at MIT

### My Research

- Program Verification: how to *prove* the program is doing the right thing?
- Program Synthesis: how to *generate* a program that does the right thing?

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


## The Crew

Teaching assistants:

* [Zheng Guo](https://aaronguo1996.github.io/)
* [Michael James](http://michaelbjames.com/)

Tutors

* Aidan Denlinger
* Darya Verzhbinsky
* Daniel Wang
* Ziteng Wang

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


## Lecture Format

Live lecture over Zoom during scheduled lecture time

- Keep your *mic* off unless you are talking
- Keep your *video* on if you can: it makes it much more fun for me!
- Two ways to ask a question:
    1. "Raise your hand" in zoom and I will call on you
    2. Type into zoom chat
- Please do not use public Zoom chat for random commentary, it's distracting   
- Same if I ask you a question
- I will split you into breakout rooms for small-group discussion
    - Same group throughout the quarter (hopefully)
    - You'll be sent to the room and back automatically    
    - Let's test that!
    
    
Lectures will also be recorded and published on canvas    



<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

## What is CSE 130 **not** about?

Learning... 

- JavaScript in April
- Haskell in May
- C++ in June
- etc. 

### New languages come (and go ...)

There was no

- Python      30 years ago
- Java        25 years ago
- C#          20 years ago
- Rust        10 years ago
- WebAssembly 5 years ago


<br>
<br>
<br>
<br>
<br>
<br>

## What is CSE 130 about?

- Concepts in programming languages
- Language design and implementation


<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>



## A Programming Language

### Two Variables

- `x`, `y`

### Three Operations

- `x++`
- `x--`
- `x = 0 ? L1 : L2`


<br>
<br>
<br>
<br>
<br>
<br>


## Example Program

(What _does_ it do?)

```
L1: x++
    y--
    y = 0 ? L2 : L1
L2: ...
```


<br>
<br>
<br>
<br>
<br>
<br>

## The above language is "equivalent to" every PL!

But good luck writing 

- QuickSort
- Fortnite
- Spotify

<br>
<br>
<br>
<br>
<br>
<br>

## So Why Study Programming Languages?

![Federico Fellini](/static/img/fellini.png){#fig:fellini .align-center width=25%}

> A different language
> is
> a different vision
> of life.


<br>
<br>
<br>
<br>
<br>
<br>


## So Why Study Programming Languages?

> The principle of **linguistic relativity**
> holds that the structure of a language
> affects its speakers world view or cognition.

Or more simply:

> Programming Language
> shapes
> Programming Thought.

Language affects how ideas and computation are expressed



<br>
<br>
<br>
<br>
<br>
<br>



## Course Goals

![130 Brain](https://ucsd-cse130.github.io/wi20/static/img/galaxy-brain-130.jpg){#fig:morpheus .align-center width=40%}

> Free Your Mind.



<br>
<br>
<br>
<br>
<br>
<br>

## Goal: Learn the Anatomy of PL

![Anatomy](/static/img/anatomy.png){#fig:anatomy .align-center width=20%}


- What makes a programming language?
- Which features are **fundamental** and which are **syntactic sugar**? 





<br>
<br>
<br>
<br>
<br>
<br>


## Goal: Learn New Languages / Constructs

![Musical Score](/static/img/music-score.png){#fig:music .align-center width=30%}

New ways to **describe** and **organize** computation,
to create programs that are:

- **Correct**
- **Readable**
- **Extendable**
- **Reusable**



<br>
<br>
<br>
<br>
<br>
<br>






## Goal: How to Design new Languages

New hot languages being designed in industry as we speak:

- Flow, React @ Facebook     
- Rust @ Mozilla, 
- TypeScript @ Microsoft
- Swift @ Apple
- WebAsssembly @ Google + Mozilla + Microsoft

Buried in every large system is a (domain-specific) language

- DB: SQL
- Word, Excel: Formulas, Macros, VBScript
- Emacs: LISP
- Latex, shell scripts, makefiles, ...

If you work on a large system, you **will** design a new PL!



<br>
<br>
<br>
<br>
<br>
<br>

## Goal: Enable You To Choose Right PL

But isn't that decided by

- Libraries
- Standards
- Hiring
- Your Boss?!

Yes.

**My goal:** Educate tomorrow's leaders so you'll make **informed** choices.



<br>
<br>
<br>
<br>
<br>
<br>

## Course Syllabus

- Lambda calculus (2 weeks)
    - The simplest language on Earth
- Haskell (5 weeks)
    - A cool functional language
- Build your own language (3 weeks)
    - How do we implement a new language (in Haksell)?
    - How do we formalize a language and prove things about it?
    

<br>
<br>
<br>
<br>
<br>
<br>


## **QuickSort** in C

```c
void sort(int arr[], int beg, int end){
  if (end > beg + 1){
    int piv = arr[beg];
    int l = beg + 1;
    int r = end;
    while (l != r-1)
       if(arr[l] <= piv) l++;
       else swap(&arr[l], &arr[r--]);
    if(arr[l]<=piv && arr[r]<=piv)
       l=r+1;
    else if(arr[l]<=piv && arr[r]>piv)
       {l++; r--;}
    else if (arr[l]>piv && arr[r]<=piv)
       swap(&arr[l++], &arr[r--]);
    else r=l-1;
    swap(&arr[r--], &arr[beg]);
    sort(arr, beg, r);
    sort(arr, l, end);
  }
}
```



<br>
<br>
<br>
<br>
<br>
<br>

## **QuickSort** in Haskell

```Haskell
sort []     = []
sort (x:xs) = sort ls ++ [x] ++ sort rs
  where
    ls      = [ l | l <- xs, l <= x ]
    rs      = [ r | r <- xs, x <  r ]
```

(not a wholly [fair comparison...](http://stackoverflow.com/questions/7717691/why-is-the-minimalist-example-haskell-quicksort-not-a-true-quicksort))



<br>
<br>
<br>
<br>
<br>
<br>



<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


## Course Logistics

- [webpage](https://nadia-polikarpova.github.io/cse130-web)
    - calendar, lecture notes, programming assignments, ...
- [canvas](https://canvas.ucsd.edu/courses/26587)
    - lecture recordings  
- [piazza](https://www.piazza.com/ucsd/spring2021/cse130/home)
    - announcements and discussions
- [gradescope](https://www.gradescope.com/courses/258033)
    - homework/exam submissions, grades    



<br>
<br>
<br>
<br>
<br>
<br>

## Grading

- 45% Homework assignments
- 25% Midterm
- 30% Final
- 05% Extra credit for Piazza discussion
    - To **top 20** best participants
    
<br>
<br>
<br>
<br>
<br>
<br>    

## Assignments

- 6 programming assignments
- Released [online](https://nadia-polikarpova.github.io/cse130-web/assignments.html), at least a week before due date
- Due on **Wednesday at 11:59pm**
    - no assignment this and next Wednesday
- 8 late days, no more than 4 late days per assignment
    - used atomically (5 mins late = 1 late day)
- Submitted via Gradescope
    - submission instructions in the assignment
- Solve **alone or in groups of two**
    - user this [piazza thread](https://piazza.com/class/kmpjxqrkmzu1kp?cid=5) to find a partner

<br>
<br>
<br>
<br>
<br>
<br>     
    
## Exams    

- Midterm on *May 3*
    - Gradescope multiple choice
    - individual
    - 24h timespan
- Final: *June 10*
    - programming assignment
    - individual
    - 24h timespan
- Formats subject to change!    
- You can use any resources you want, but not ask anyone for help
- The final is cumulative
- Midterm grade is calculated as `midterm > 0 ?  max(final, midterm) : 0`
    - you get a second chance if you don’t do well on the midterm
    - you must turn in both the midterm and the final




<br>
<br>
<br>
<br>
<br>
<br>

## In-class Quizzes

We will do quizzes in class via Zoom polls

  - Make class interactive
  - Help *you* and *me* understand what's tricky
    
**Protocol**

1. *Solo Vote*
    - I show the quiz on my screen and start a poll
    - Think for yourself, select answer

2. *Discuss*
    - Go into your *breakout room*
    - To see the quiz, open the lecture notes from the class website
    - Analyze problem with your groups
    - Reach consensus
    - I will "call you back" from the room when time's up

3. *Group Vote*
    - Everyone in group votes
    - Hopefully the same way but not enforced

4. *Class Discuss*
    - What was easy or tricky?    

<br>
<br>
<br>
<br>
<br>
<br>


## TEST QUIZ

How can you earn 5% extra credit for this class?

- **A**  do all my homework alone

- **B**  answers other students' questions on Piazza

- **C**  submit all my homework on due date (without using late days)

- **D**  post snarky comments on zoom chat during lecture


<br>
<br>
<br>
<br>
<br>
<br>


## Your Resources

- Discussion section: Fri 2pm, same Zoom link as lecture
- Office hours
    - every day, check calendar
- Piazza
    - we answer during work hours
- **No text**        
    - online lecture notes and links



<br>
<br>
<br>
<br>
<br>
<br>






## Academic Integrity

Programming assignments: do not copy from classmates or from previous years

Exams done **alone**

  - Zero Tolerance
  - Offenders punished ruthlessly
  - Please see academic integrity statement


<br>
<br>
<br>
<br>
<br>
<br>


## Students with Disabilites

Students requesting accommodations for this course due to a disability or current functional limitation must provide 
a current **Authorization for Accommodation (AFA)** letter issued by the Office for Students with Disabilities (OSD). 

Students are required to present their AFA letters to Faculty (please make arrangements to contact me privately) 
and to the CSE OSD Liaison in advance so that accommodations may be arranged.

<br>
<br>
<br>
<br>
<br>
<br>


## Diversity and Inclusion

**Goal**

- Create a diverse and inclusive learning environment 
- Where all students feel comfortable and can thrive 
- If there is a way we can make you feel more included, please let one of the course staff know

**Expectations**

- We expect that you will honor and respect your classmates
- Abide by the UCSD [Principles of Community](https://ucsd.edu/about/principles.html)
- Understand that others’ backgrounds, perspectives and experiences may be different than your own
- Help us to build an environment where everyone is respected and feels comfortable.

If you experience any sort of **harassment or discrimination**, please contact the [Office of Prevention of Harassment and Discrimination](https://ophd.ucsd.edu/).
Students may receive confidential assistance at the [Sexual Assault Resource Center](http://care.ucsd.edu) at (858) 534-5793
or [Counseling and Psychological Services](http://caps.ucsd.edu.) (CAPS) at (858) 534-3755.

<br>
<br>
<br>
<br>
<br>
<br>

## COVID-19

- We understand that this quarter will present unique challenges
- And that you might be disadvantaged in new ways
    - Poor Internet connection, different time zone, ...
    
- I will do my best to accommodate your needs, just ask me or one of the course staff!

- Please be patient with us too!


<br>
<br>
<br>
<br>
<br>
<br>




