# Pair Programming Practice

_Last review: May 28th 2018_

> Pair programming is an agile software development technique in which two programmers work together at one workstation. One, the driver, writes code while the other, the observer or navigator,\[1\] reviews each line of code as it is typed in. The two programmers switch roles frequently.
>
> While reviewing, the observer also considers the "strategic" direction of the work, coming up with ideas for improvements and likely future problems to address. This frees the driver to focus all of their attention on the "tactical" aspects of completing the current task, using the observer as a safety net and guide.

-- [Wikipedia](https://en.wikipedia.org/wiki/Pair_programming)

## Benefits

* Two heads are better than one
* More efficient
* Fewer coding mistakes \(on-going peer review\)
* Effective way to share knowledge and learn
* Develop interpersonal skills

Pairing is appropriate when:

* Implementing complex features
* Fixing a bug
* Refactoring
* Onboarding a new member
* Live code review (one member reviews code implemented but the other member)

Pairing is not appropriate for:

* Easy and simple implementation
* Chores
* Research/investigations
* Code review of a PR that does not belong to the pair

## Local Pairing Setup

To make pair programming as efficient and as enjoyable it is important to have a common set of tools with the same configurations.

* [Atom](https://atom.io/); editor
* [iTerm2](https://www.iterm2.com/); terminal
* [SourceTree](https://www.sourcetreeapp.com/); Git GUI - optional

If you and your pair have negotiated a different setup, you're welcome to use it.

### Atom Configuration

#### Themes

The default themes used for applications are "light":

* MacOS: Light
* Atom: Atom Light (UI) / One Light (Syntax)
* iTerm: Solarize

If the pair wants to change the themes, this may be negotiated.

### Screen Configuration

Pair programming is done in [full-screen, split-mode](https://support.apple.com/en-ca/HT204948) with the editor on the left hand-side and the terminal on the right-hand side. It is helpful to be familiar with [Mission Control](https://support.apple.com/en-ca/HT204100) to work with fullscreens gracefully.

## Remote Pairing Setup

Remote pairing is done using a cloud pairing station. We use Cloud9. A pairing instance must first be provisioned for the project. See [guide here](https://github.com/civilcode/cloud9-bootstrap).

Both pair members access the Cloud9 instance using their Amazon IAM account. The pair use Zoom for audio. If need be, the pair can use Zoom to share a window or screen, like for instance look at the Github issues together.

* [Cloud9](https://aws.amazon.com/fr/cloud9/); pairing station in the cloud
* [Zoom](https://zoom.us/); screen sharing and/or audio

It is responsibility of one of the pair members to prepare the cloud pairing station for the pairing session.

## Getting Started

Before starting a new pairing session

1. one of the members prepares the workstation
2. negotations are completed, e.g. themes; when to take breaks and lunch

*Note: breaks are very important to take. Try to take a break every 1.5 hours for 15 mins.*

### Git user

For pulling and pushing to Github, we use our CivilCode pairing account \(`civilcode-pairing`\). The first time a repo is pulled through the `https` handle, git asks for the username and password. By default, the credentials are cached in OSX keychain.

When committing code, the pair uses the [multiple co-authors](https://help.github.com/articles/creating-a-commit-with-multiple-authors/) feature of GitHub. The dotfiles have a list of possible co-authors in the `~/.gitmessage` file.

1. Update the ~/.gitmessage file (uncomment/comment co-author lines)

### New branch

1. Prepare the editor and terminal with the recommended screen configuration
2. Fresh master has been pulled
3. Test suite is green

### Existing branch

1. Prepare the editor and terminal with the recommended screen configuration
2. The branch has been checked-out
3. The branch is rebased with master
4. Test suite is green

## Etiquette

Good etiquette translates into efficient pair programming.

1. Agree on the physical environment beforehand
2. When talking about code, always refer to line number and file name
3. When disagreeing, talk in terms of benefits
4. When feeling ill at ease, say so
5. Bestow as many compliments as possible

More details [here](https://blog.rapid7.com/2017/01/27/5-rules-of-pair-programming-etiquette/).

## Pair Programming Ping Pong Pattern

This technique is based on the [red/green/refactor agile pattern](https://sites.google.com/site/agilepatterns/home/red-green-refactor).

The developer having the keyboard and mouse is considered the _driver_, while the other developer is the _watcher_.

A significant part of the _watcher_ role includes continually reviewing the work of the driver, pointing out spelling and syntax errors at the right moment, and providing feeback when the _driver_ asks for it.

The watcher is **not** a _navigator_ \(concept from another pair programming technique, as described [here](https://www.sourceallies.com/2011/03/pair-programming-101/)\).

The overall flow is simple:

1. Pair discusses the next problem to solve
2. Developer A becomes the driver
3. Developer A refactors an existing test module (if applicable)
4. Developer A writes a failing test
5. Developer B becomes the driver
6. Developer B refactors existing production code (if applicable) - not the tests!
7. Developer B makes the test pass writing only enough code to make it pass
8. Developer B makes a commit (if it makes senses - highly suggested)
9. Pair discusses the next problem to solve
10. Developer B refactors the previous test or other tests (if applicable)
11. Developer B writes a failing test
12. Goto 2
13. Continue until Developer A and Developer B both agree that there are no more tests for the unit they are currently working on

Things to watch-out for to prevent breaking the loop:

- Watcher should not move the mouse, unless asking for permission to do so.
- Watcher should not touch the keyboard, unless asking for permission to do so. If permitted, this is not considered a role switch.
- While making a test pass, if the test code needs tweaking, it is up to the driver to do the changes (not the person who wrote the test, in this case the watcher).

**The driver can refactor the code in which modifications are about to happen only when all tests are passing.**

If the pair is performing long refactoring, the role switching can happen after each refactoring or group of small refactoring. The driver should watch for not keeping control for too long, otherwise the watcher may "lose interest".

### Guidelines

For the pair:

1. First, before either writing a test or implementing the code, a **clear shared understanding has to be established**. Otherwise, the watcher will have a hard time following the driver and disagreements may arise quickly.
2. If research is required at some point, don't hesitate to split and regroup at some point.

   When writing code to make a test pass, the goal is to get something quick and dirty working. Then the pair can discuss and improve the code. If the driver had the keyboard for a while, the watcher can then take over and do some refactoring before writing a new test.

3. If the pair disagrees on design or implementation and cannot come up with an agreement, the pair needs to determine if the issue is the technical lead or another team member should be brought in and a discussion should happen.  If no-one is available, a solution **that leaves options open**  should be adopted so progress can be made; the issue can then be discussed when the technical lead or another member becomes available. It maybe determined that the issue is not project specific, i.e. is a general design issue and requires R&D. At this point, an issue will be created in our reference repository and scheduled for investigation.
4. The code is shared by the development team, therefore use _we_ instead of _you_ or _I_ when referring to the code.
5. Be proud of what you achieved as a pair. Take time to admire and feel good about the code.
6. Be mindful of your hygiene.

For the driver:

1. Be willing to be vulnerable, do not be afraid to ask for help. This triggers a discussion and the driver can then resume. It is a great opportunity to learn.
2. The driver must communicate the intentions. Otherwise, it is difficult for the watcher to follow the thought process of the driver.
3. The driver regularly asks the watcher for feedback \(errors? spelling mistakes? opinions?\)
4. The driver should not keep the keyboard for too long. Big refactoring can be split into smaller ones and each member in turn refactors portions of the code.

For the watcher:

1. The watcher should try to **limit interruptions** to prevent the driver loosing focus. The watcher should wait for a moment where an intervention is "à propos" and is absolutely required (i.e. the driver started something on a wrong path).
2. The watcher should not tell the driver what to do, unless the driver asks for it.
3. If the watcher wants to use the keyboard/mouse, it must first ask the driver.
4. When pairing remotely, as a watcher, avoid distractions and stay in the same file as the driver, as if you were pairing in person.

## References

* [Ping Pong Pair Programming](https://anthonysciamanna.com/2015/04/18/ping-pong-pair-programming.html)
* [5 Rules of Pair Programming Etiquette](https://blog.rapid7.com/2017/01/27/5-rules-of-pair-programming-etiquette)
* [Pair Programming for Introverts](https://codeburst.io/pair-programming-for-introverts-dab230879c84)
* [Compare 6 Different Pair Programming Styles](https://stackify.com/pair-programming-styles/)
* [Pair Programming Ping Pong Pattern](http://wiki.c2.com/?PairProgrammingPingPongPattern)
* [How to Pair Program](https://www.youtube.com/watch?v=YhV4TaZaB84) - Video
