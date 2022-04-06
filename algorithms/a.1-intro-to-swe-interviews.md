# A.1: Intro to SWE Interviews

## Introduction

SWE interviews \(like all interviews\) are subjective. There are times when an interviewee may get the right answer but be rejected. There are times where an interviewee may not get the right answer but be accepted. When preparing for interviews, know that the outcome of the interview may not be in your control, but what we can control is our familiarity with common interview questions and patterns such that we can succeed with as many interview problems as possible.

## Common SWE Interview Types

### Take-Home Interview

Many companies start the interview process with a take-home interview. This helps them screen coders from non-coders efficiently without spending man-hours. These take-home interviews typically ask candidates to build an app over a few days, which could be frontend, backend, or full-stack focused. The type of app is typically related to the company's line of business. For example, an HR software company might ask candidates to create an employee management app, or a banking software company might ask candidates to build a banking app. 

Take-home interviews are typically assessed by engineers for both completion and code quality. Both factors are considered when determining whether to let a candidate continue interviewing. Completion is more simple: does the app do what it is supposed to do. Code quality is a bit more nebulous because the notion of code quality differs across companies and even within companies. Code quality typically refers to communication of code's purpose, and that communication typically boils down to naming, comments, and decomposition. 

Once one passes a take-home interview, one is typically invited on-site \(or over Zoom during COVID\) for several rounds of in-person interviews. These in-person interviews will typically consist of the other interview types below, but there is a good chance at least 1 of the in-person interviews will be to review the take-home interview, to verify that the candidate knows what they were doing and can communicate their decisions clearly. Before going for in-person interviews, please revise the take-home assignment to make sure you are familiar with the technologies and ready to answer questions about your code and decisions.

### Culture Fit

Culture fit interviews are typically the first and/or the last interviews after the take-home interview. Once a company has determined that a candidate can code and thus is worth interviewing for SWE roles, a recruiter may perform an initial screen of the candidate to determine whether this person shows any red flags in terms of soft skills. Such red flags may include a disrespectful attitude, dishonesty, or lack of interest. If the candidate displays any red flags, the recruiter may terminate the interview process. There may also be a final culture fit interview after all other tech interviews, where a senior engineer may interview a candidate for the same purpose.

### Data Structures and Algorithms \(DS&A\)

DS&A interviews are the most common and archetypal interview used by tech companies to hire SWEs. DS&A interviews typically consist of solving 1 contrived coding problem in roughly 45 minutes or less. See [Leetcode](https://leetcode.com/) or [Hackerrank](https://www.hackerrank.com/) for examples of such coding problems. DS&A interviews are popular because of their standard nature: they are a consistent and scalable way to judge many engineers by a similar bar across many interviewers. Most SWE interview processes will include at least 1 DS&A-related interview, and many will include multiple DS&A interviews.

The good news is that DS&A problems follow a set number of standard patterns, and if one is diligent enough to practise for long enough, one will eventually master those standard patterns. DS&A problems are different enough from most SWEs' typical work that most SWEs do not invest significant time in choosing uncommon DS&A problems. This means with enough practise and interviews under one's belt, it's uncommon to encounter DS&A problems one is completely unfamiliar with.

The bad news is that DS&A problems are unlike most programming one does at coding bootcamps \(i.e. building practical projects\), thus most bootcamp graduates are less prepared for D&SA problems than the average university CS grad. Top companies tend to interview more uni grads than bootcamp grads, thus their benchmarks are biased more toward uni grads. Uni CS grads have an additional advantage in that most uni CS curriculums teach DS&A as part of their core curriculum. Stanford requires all CS students to take [CS161](https://www.coursera.org/specializations/algorithms), whose curriculum includes almost all common DS&A interview patterns one would encounter, albeit with additional theory.

In the limited time we have at RA, we will want to strike a balance between practical projects \(which will be more useful for on-the-job work\) and DS&A practice \(mostly useful for interviews\). Neither should be discounted, and depending on the types of companies one wants to work with one might want to emphasise one or the other slightly more.

### Systems Design

Systems Design \(SD\) interviews are less common among junior engineer interview processes and many RA grads may not encounter SD interviews until later in their SWE careers. SD interviews typically consist of designing software architecture, e.g. drawing a diagram of the various frontend and backend components in a software system and how the pieces fit together. Such interviews are crucial for more senior engineers, because senior engineers spend less time writing code and more time designing code architecture, determining how modules will divide responsibilities and interact. SD interviews are also a good way to test knowledge of software systems overall, whether a candidate could be counted on to lead a team that oversees the whole system.

### Language-Specific Questions

Some companies whose core competency is not software may be more dependent on a single, typically older language that may require more niche knowledge that many newer software engineers may not have. Such companies will typically test for such knowledge in their interview process, asking language-specific questions to evaluate experience in that coding language. Common languages that companies look for include Java \(most common\) and occasionally C++ \(for lower-level programming work\).

Such language-specific questions are less common at tech companies because engineers at tech companies are expected to be able to pick up any language they need to, and in the worst case, new features at tech companies can be written in new languages. At "non-tech" companies there is typically less engineering expertise, thus engineers are expected to be familiar with the company's coding language, else risk not being productive. 

