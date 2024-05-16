# An AppSec cat attempts to eat the AppSec dog food: CD edition

![](images/man_eats_dog_food.jpg)

## Abstract

A common refrain in the application security profession these days is to meet developers where they work by embedding security tools into the SDLC. But just how much effort does it take to do this? How confident can you be in recommending a course of action you have not tried? This talk details the path the speaker took in implementing and exercising free and open-source security tools, and will include a basic how-to as well as lessons learned so you can do the same (and yes, that means actual documentation). It will include what is sure to be an entertaining live demo.

This is a sequel to [last year's talk](https://github.com/xenloops/talk-dogfood-pipeline-ci), and focuses on the Continuous Delivery/Deployment side of the pipeline.

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## About the speaker

Nathan Larson has led static analysis teams at two major financial institutions, pen-tested internet-connected industrial devices, performed code review in aerospace, and taught security and programming at the university and grad school levels. He has an MS in software engineering, a BS in computer science, and has held a few security certifications -- all of which show a proficiency in reading textbooks and passing exams. He wrote insecure code in several industries for two decades before catching the AppSec bug, from which he hasn't recovered in 10+ years. 

He works as an AppSec architect and leads the local OWASP chapter, which you can find by typing "OWASP-MSP" in your favorite search engine _(we're always looking for speakers, hint hint)_. He enjoys astronomy, cribbage, raising chickens, and finding silly mistakes in production code.

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

**Disclaimer:** This talk does not necessarily represent the policies or processes of past, present, or future employers -- regardless of how well thought-out and rational the presentation. I am not speaking on behalf of any company during this presentation. I use product names as examples, and do not intend them as endorsements -- except those of OWASP projects, which are awesome and should be checked out by everyone in technology.

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## Agenda

1. What are we trying to fix?
1. Pipeline maturity and the OWASP SAMM
2. Artifact management
3. Secrets management
5. Deployment
1. Tool setup & demo:
   * Development and build environment integration
   * Signature checking
1. The CD pipeline ```as code```
1. Pipeline Visualization
1. Integration with Other Tools

<br />

## Key takeaways
* Automation streamlines software delivery
* Visibility and traceability improve development
* Feedback provides continuous improvement

<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />

## Ground rules
* **Interrupt with questions!**
* The only dumb questions are the unasked ones.
* Discussion is good.
* There are no silver bullets in security.

<br /><br /><br /><br />

[Next slide](rationale.md)
