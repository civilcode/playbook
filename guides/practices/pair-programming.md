# Pair Programming Practice

> Pair programming is an agile software development technique in which two programmers work together at one workstation. One, the driver, writes code while the other, the observer or navigator,[1] reviews each line of code as it is typed in. The two programmers switch roles frequently.

> While reviewing, the observer also considers the "strategic" direction of the work, coming up with ideas for improvements and likely future problems to address. This frees the driver to focus all of their attention on the "tactical" aspects of completing the current task, using the observer as a safety net and guide.

-- [Wikipedia](https://en.wikipedia.org/wiki/Pair_programming)

## Benefits

- Two heads are better than one
- More efficient
- Fewer coding mistakes (on-going peer review)
- Effective way to share knowledge and learn
- Develop interpersonal skills

## Setup

To make pair programming as efficient and as enjoyable it is important to have a
common set of tools with the same configurations:

- [Atom](https://atom.io/); editor
- [iTerm2](https://www.iterm2.com/); terminal
- [SourceTree](https://www.sourcetreeapp.com/); Git GUI - optional
- [Cloud9](https://aws.amazon.com/fr/cloud9/); pairing station in the cloud - remote only
- [Zoom](https://zoom.us/); screen sharing - remote only

If you and your pair have negotiated a different setup, you're welcome to use it.

## Atom Configuration

### Shell commands

Install shell commands from the menu: `Atom > Install Shell Integration`.

### Packages

Use this script to install all of the required packages:

```
apm install Sublime-Style-Column-Selection atom-elixir atom-elixir-formatter language-elixir
```

### Settings

With a fresh install of Atom you will have a config file that looks something like this:

```
"*":
  "exception-reporting":
    userId: "your-unique-id"
```

Merge the [atom-config.cson](./atom-config.cson) file using the following command:

`opendiff ~/.atom/config.cson atom-config.cson`

Select "Choose both (left first)" and save the merge to ~/.atom/config.cson

## Screen Configuration

Pair programming is done in [full-screen, split-mode](https://support.apple.com/en-ca/HT204948) with
the editor on the left hand-side and the terminal on the right-hand side. It is helpful to be
familiar with [Mission Control](https://support.apple.com/en-ca/HT204100) to work with fullscreens
gracefully.

## Remote pairing

Rmeote pairing is done using a cloud pairing station. We use Cloud9. A pairing instance
must first be provisioned for the project. See [guide here](https://github.com/civilcode/cloud9-bootstrap).

Both pair members access the Cloud9 instance using their Amazon IAM account. The pair use
the tool they want for the audio (Zoom, slack, ...).

## Git user

For pulling and pushing to Github, we use our CivilCode pairing account (`civilcode-pairing`).
The first time a repo is pulled through the `https` handle, git asks for the username and password.
By default, the credentials are cached in OSX keychain.

When committing code, the pair uses the [multiple co-authors](https://help.github.com/articles/creating-a-commit-with-multiple-authors/) feature of GitHub.
The pairing station has a list of possible co-authors in the `.gitmessage` file.

### New branch

1. Prepare the editor and terminal with the recommended screen configuration
2. Fresh master has been pulled
3. Test suite is green

### Existing branch

1. prepare the editor and terminal with the recommendation screen configuration
2. the branch has been checked-out
3. the branch is rebased with master
4. test suite is green

### Etiquette

Good etiquette translates into efficient pair programming.

1. Agree on the physical environment beforehand
2. When talking about code, always refer to line number and file name
3. When disagreeing, talk in terms of benefits
4. When feeling ill at ease, say so
5. Bestow as many compliments as possible

More details [here](https://blog.rapid7.com/2017/01/27/5-rules-of-pair-programming-etiquette/).

### Ping pong process

The process is simple:

1. A writes a new test and sees that it fails.
2. B implements the code needed to pass the test.
3. B writes the next test and sees that it fails.
4. A implements the code needed to pass the test.

And so on. **Refactoring is done whenever the need arises by whoever is driving**.

## Rules and hints

- First, before either writing a test or implementing the code, a **clear shared understanding has to be established**. Otherwise, the watcher will have a hard time following the driver and disagreements may arise quickly.
- If research is required at some point, don't hesitate to split and regroup at some point.
- When writing code to make a test pass, the goal is to get something quick and dirty working. Then the pair can discuss and improve the code. If the driver had the keyboard for a while, the watcher can then take over and do some refactoring before writing a new test.
- Be willing to be vulnerable, do not be afraid to ask for help. This triggers a discussion and the driver can then resume. It is a great way to learn.
- While writing code to make the test pass, if the test needs some tweaking, it is up to the driver to fix it, not the person who wrote the test (the watcher).
- The driver must continually talk, explaining the intent while typing. Otherwise, it is difficult for the watcher to follow the thought process of the driver.
- The watcher should try to **limit interruptions** to prevent the driver loosing focus. The watcher should wait for a moment where an intervention is "a propos". The watcher is **not** a _navigator_ (concept from another pair programming process).
- The watcher should not tell the driver what to do, unless the driver asks for it.
- The driver regularly asks the watcher for feedback (errors? spelling mistakes? opinions?)
- If the watcher wants to use the keyboard/mouse, it must first ask the driver.
- The driver should not keep the keyboard for too long. Big refactoring can be split into smaller ones and each member in turn refactors portions of the code.
- If the pair disagrees on design or implementation and cannot come up with an agreement, file an issue in the project and bring this up to the team at some point.
- The code is shared by the development team, therefore use _we_ instead of _you_ or _I_ when referring to the code.
- When pairing remotely, as a watcher, avoid distractions and stay in the same file as the driver, as if you were parigin in person.
- Do not forget to take breaks.
- Be proud of what you achieved as a pair. Take time to admire and feel good about the code.
- Be mindful of your hygiene.
