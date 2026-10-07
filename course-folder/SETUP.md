# Set up a CPSC 1710 course folder

*These instructions are written for an AI coding agent (Codex or Claude Code). A student has asked you to follow them. The student-facing guide is at https://cpsc1710.github.io/labs/course-folder/.*

You are helping a student keep everything for CPSC 1710 in one folder on their computer, so that they and their agent can see the whole course in one place. The student may be new to code. As you work, say what you are doing in one plain sentence per step.

Work only inside the current folder.

## Before you start

Check where you are. The current folder should be empty, or already be a course folder from an earlier run of these instructions. If it is the student's home folder, Desktop, Downloads or Documents folder, or it holds unrelated files, stop. Ask the student to make a new folder called `cpsc1710`, open it, and ask again.

Keep everything that is already there. Do not delete, move or overwrite the student's files. The one exception is `course/labs/`, which is a copy of the public labs site and is replaced on every update.

You do not need Git, and you should not install any software. If downloading is blocked, tell the student that you need permission to download from github.com, and wait.

## Steps

1. **Make the folders,** if they are missing:

   ```text
   course/handouts/     handouts the student downloads from Canvas
   course/slides/       lecture slides the student downloads
   work/                the student's own homework and lab work
   notes/               the student's notes, and notes you write for them
   projects/            the final project and other experiments
   ```

2. **Download the labs site.** Get `https://github.com/cpsc1710/labs/archive/refs/heads/main.zip`, unpack it, and put its contents in `course/labs/`, replacing what was there. The archive unpacks to a folder named `labs-main`; its contents are what belong in `course/labs/`. Remove the downloaded zip file and any temporary folder when you are done.
   - macOS or Linux: `curl -L -o labs.zip <url>` then `unzip -q labs.zip`
   - Windows PowerShell: `Invoke-WebRequest <url> -OutFile labs.zip` then `Expand-Archive labs.zip`

3. **Install the practice skill** for both agents, replacing any older copy:
   - copy `course/labs/skills/grill-me/` to `.agents/skills/grill-me/` (read by Codex)
   - copy `course/labs/skills/grill-me/` to `.claude/skills/grill-me/` (read by Claude Code)

4. **Add the folder's instructions,** only if they are not there yet:
   - `AGENTS.md` from `course/labs/course-folder/template/AGENTS.md`
   - `CLAUDE.md` from `course/labs/course-folder/template/CLAUDE.md`
   - `README.md` from `course/labs/course-folder/template/README.md`

   If one of these already exists, leave it as it is and tell the student.

5. **Report back** in a few lines:
   - the folders that now exist, two levels deep
   - what was downloaded, and today's date as the "last updated" date
   - where to put things: Canvas handouts in `course/handouts/`, slides in `course/slides/`, their own work in `work/`
   - how to start practising for the midterm: type `$grill-me` in Codex or `/grill-me` in Claude Code, or just say "grill me on week 4 for 15 minutes". If the skill does not appear, close and reopen the app.

## Updating later

When the student says "update my course folder", repeat steps 2 and 3. Do not touch `AGENTS.md`, `CLAUDE.md`, `README.md`, `work/`, `notes/` or `projects/`.

*Drafted by Claude (Anthropic), based on the direction of Xiuye Chen.*
