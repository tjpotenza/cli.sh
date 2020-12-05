# `cli.sh` - Small shell utilities for better scripts

## Why?

Shell scripts often get a bad repuation for being hastily put together, handling errors and invalid inputs poorly, and just in general feeling more like hacks than proper programs.  There are a handful of small patterns and utilities I've noticed that I implement in pretty much every shell project, and made sense to me to establish a source of truth for 'em so I can make proper iterative improvements.  Right now they're focused on logging, input handling, and output readability, however I hope to toss more `bash`-isms into this repo down the road to keep track of my favorite patterns, reduce toil on shell scripts, and make them just a bit less bad in general.

## What?

They're tidied up versions of a bunch of small helper functions I've noticed I end up implementing in one way or another in almost every shell-based CLI tool I write.  The [best descriptions are found in-line](./cli.sh), however the high-level overview of what's in here so far is:

* `styled <style to apply> <text to style>`: Adds ANSI formatting such as colors or underlining to text, to allow command output to be color-coded for readability.  Only adds the color when in interactive shells by default, to help minimize the change of ANSI characters polluting the output of systmes that don't support 'em.

* `log <level (optional)> <message>`: Logs the message to `STDERR` with a colorized prefix corresponding to levels `debug|info|warn|error|fatal`.

* `prompt <message (optional)> <skip (optional)>`: Prompts the user for confirmation with a message before continuing.  Allows the prompt to be skipped if logic earlier in the script determines it's been pre-approved (ie by implementing an `--auto-approve` style flag).  If an unskipped prompt is reached in a non-interactive shell, automatically rejects it.

## How?

Since shell scripts are often most easily distributed as a single file, `cli.sh` is designed to be either sourced by another shell script or copy-pasted into one inline.  The comments aim to make the boundaries between `cli.sh` content and the rest of the script clear, while also allowing new versions to be easily and confidently swapped in.

## What's next?

Potentially more utilities, potentially non-utility `bash`-isms, potentially tests.  Potentially (and most likely) nothing, but who knows!
