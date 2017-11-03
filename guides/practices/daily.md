# Daily Practices

There are several daily practices that we have found helpful to keep communication
flowing within the team and our clients. These practices are followed Monday-Friday for
billable and non-billable time.

## Beginning of the day

Within the first hour of starting your day, it's important to check-in to share with your clients
and the team what your intentions for the day are.

### Check-in on Slack

A good check-in highlights three things:

1. Blockers; are you waiting for anyone (mention them) or stuck on something that is preventing you
   to move forward (as required)
2. Work-in-progress; what WIP pull request are you picking up
3. Up next; what is in your back-log, one or more items (optional)

#### Example

```
in:
• blocked: currently waiting on @john for review on _Display 3 most recent tweets_
https://github.com/montrealelixir/website/issues/13
• continue: _Upgrade to Phoenix 1.3.x_ (pair with @jane)
https://github.com/montrealelixir/website/pull/15
• up next: _Display the next/most recent meetup from Meetup.com_
https://github.com/montrealelixir/website/issues/12
```

#### Template

The example and template provide a consistent format across all check-ins, reducing the
cognitive overhead of scanning different formats for the client and other team members. Based on
this example each line of the check-in has:

1. single bullet (Option-8 on a mac)
2. type of check-in line
3. the title of the issue/pull-request
4. optionally the person you are pairing with
5. the link to the issue/pull-request; starting on a new line

As the title of the issue/pull-request is the key component of a check-in line, these titles
need to be descriptive.

#### Options

Check-in's work as an excellent checklist for the day. If you wish to mark things completed in your
checklist throughout the day feel free to replace the `•` with a `✔︎` for completed issues and `➽` for
work in progress.

## During the day

GitHub issues/pull-requests drives our work. When working, we can always reference an issue on
GitHub. Our workflow encourages creating an issue, marking it "in progress" and converting it to a
pull-request when we have our first commit.

## End of the day

To help close out your day, it's worth preparing for this 15 minutes before you would like to
finish. This allows you to plan your exit without feeling rushed and provides some time for
reflection and consider what you would like to accomplish tomorrow. There are two key actions to
complete at the end of your day:

1. Push to GitHub
2. Check-out in Slack

### Push to GitHub

Push all code at the end of the day to GitHub, even if it's a __work in progress__ (commit with a
WIP message). This practice provides:

- a back-up of your work
- you a sense of closure for the day
- the opportunity for another team member to pick-up the pull request if you need to
  take leave unexpectedly (e.g. sick leave; and you won't need to worry about pushing code
  while your unwell)
- an indicator of progress to your client  

Our work goes beyond writing code; often there are activities of research and discovery. These are
documented in issues as well. If the results of these activities haven't been already
documented during your workday, your end of the day wind-down provides an opportunity to do so.

### Check-out on Slack

As we work in different time-zones, it's essential that we check-out on Slack at the end of the
day. The format for a checkout is slightly different from our check-ins.

1. Blockers; are you waiting for anyone (mention them) or stuck on something that is preventing you
   to move forward (as required)
2. Completed; what issue was completed and what state is it in (waiting for review, merged)
3. Work-in-progress; what issue is in progress, _a brief description is required for the work
  done that day_

#### Example

```
out:
• blocked: _Display 3 most recent tweets_; currently waiting on @john for review
  https://github.com/montrealelixir/website/pull/13
• completed: _Upgrade to Phoenix 1.3.x_; waiting review, paired with @jane
  https://github.com/montrealelixir/website/pull/15
• wip: _Display the next/most recent meetup from Meetup.com_; learned how the Meetup.com API works
  https://github.com/montrealelixir/website/issues/12
```

#### Template

Based on this example each line of the check-in has:

1. single bullet (Option-8 on a mac)
2. status
3. the title of the issue/pull-request
4. the status of issue/pull-request
5. optionally the person you paired with
6. optionally description text, required for `wip` issues
7. the link to the issue/pull-request; starting on a new line
