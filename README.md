# Fade

A menu bar to-do list for macOS. Finished tasks delete themselves after a delay
you choose -- that's the whole point of it.

## What it does

Click the menu bar icon, type a task, hit Return. Click the circle to check it
off -- it slides into **Completed** with a countdown showing how long until it
disappears on its own.

Settings, from the gear menu:

- **Finished tasks disappear** -- never / 1 hour / 6 hours / 24 hours / 3 days / 1 week
- **Show count in menu bar**
- **Open at login**

Hovering an unfinished task reveals a **flag** to set priority and **✕** to
delete it now. Unfinished tasks can be dragged to reorder within their
priority level.

## Priority

Three levels. High rises to the top with an orange stripe, low sits at the
bottom in dimmer text, normal shows nothing at all.

## How the auto-delete works

Each task records when it was checked off. Every 30 seconds Fade drops any
completed task past its limit and rewrites its JSON file. No daemon, no
scheduler -- if the app isn't running nothing is deleted, and it catches up next
launch. Un-checking a task clears its completion time, so it stops counting
down.

Tasks are plain JSON, readable and editable by hand.

## Installing

Download the zip from the [**Releases page**](../../releases/latest), unzip it,
and drag **Fade.app** into your Applications folder.

macOS will then refuse to open it, most likely claiming the app **"is damaged
and can't be opened."** It isn't damaged. That is what macOS says about any app
not signed with a paid Apple developer certificate. To clear it, run this once
in Terminal:

```
xattr -dr com.apple.quarantine /Applications/Fade.app
```

That removes the "downloaded from the internet" flag. It's a standard macOS
command and worth looking up rather than taking my word for it. After that the
app opens normally for good.

**Apple silicon only** (M1/M2/M3/M4). It will not run on an Intel Mac.

## Updates

Fade does not update itself. Watch this repo to hear when a new version lands.

## Source

The source is in a private repo. This one holds the builds.

## Bugs

Open an [issue](../../issues). This has run mostly on my own Mac, so real
reports are useful.
