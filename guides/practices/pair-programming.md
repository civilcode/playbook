# Pair Programming Practice

> Pair programming is an agile software development technique in which two programmers work together at one workstation. One, the driver, writes code while the other, the observer or navigator,[1] reviews each line of code as it is typed in. The two programmers switch roles frequently.

> While reviewing, the observer also considers the "strategic" direction of the work, coming up with ideas for improvements and likely future problems to address. This frees the driver to focus all of their attention on the "tactical" aspects of completing the current task, using the observer as a safety net and guide.

-- [Wikipedia](https://en.wikipedia.org/wiki/Pair_programming)

## Setup

To make pair programming as efficient and as enjoyable it is important to have a
common set of tools with the same configurations:

- [Atom](https://atom.io/); editor
- [iTerm2](https://www.iterm2.com/); terminal
- [SourceTree](https://www.sourcetreeapp.com/); Git GUI - optional
- [Zoom](https://zoom.us/); screen sharing - remote only

If you and your pair have negotiated a different setup, you're welcome to use it.

## Atom Configuration

### Shell commands

Install shell commands from the menu: `Atom > Install Shell Commands`.

### Packages

Use this script to install all of the required packages:

```
apm install Sublime-Style-Column-Selection atom-elixir language-elixir
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

Remote pairing requires a certain amount of preparation. Before starting the pairing session,
determine who will be the "host". This is the developer who will be sharing their screen.
It is the host's responsibility to ensure the following before the guest comes online:

### New branch

1. prepare the editor and terminal with the recommendation screen configuration
2. fresh master has been pulled
3. test suite is green

### Existing branch

1. prepare the editor and terminal with the recommendation screen configuration
2. the branch has been checked-out
3. the branch is rebased with master
4. test suite is green
