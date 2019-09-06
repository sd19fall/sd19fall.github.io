---
title: Reading Journal
permalink: reading-journal/
---

{% include toc %}

## Get the Reading Journal

We will be using GitHub to distribute and collect pre-class reading exercises.
To get started, perform the steps below to setup your personal `ReadingJournal` repository.

1. Click on the invitation link <{{ site.data.github.reading_journal_invite }}>
2. Click the green button “Accept this assignment”.
3. Follow the remaining instructions until you get to your repository page. It will looks something like <https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname>, except with your GitHub user id instead of `myname`.
4. Clone the repository to your computer by typing the following into your Terminal program. Replace `myname` with your GitHub user id.

```bash
$ git clone https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname.git ReadingJournal
```

Now you have a copy of the ReadingJournal folder (directory) on your drive. Use the terminal{::comment}, macOS Finder, Windows Explorer,{:/comment} or Ubuntu File Manager to verify that it is present.

Next, you can fire up Jupyter notebook and load the reading journal for day X.

```bash
$ cd ReadingJournal
$ jupyter notebook reading-journal-01.ipynb
```

If all goes well, this should bring up a web-browser with the reading questions.


## Submitting Completed Readings

Once you have completed your reading journal (not just the reading exercises, but also your notes as well as any comments you want to give to us), you can turn in your work by running the following commands. First, make sure you have saved the notebook by clicking "Save and checkpoint" in the browser window. Then, run the following. (Change “reading journal 1” to the day that you have completed.)

```bash
$ cd ReadingJournal
$ git add reading-journal-01.ipynb
$ git commit -m "Completed reading journal 1"
$ git push origin master
```

You will then be prompted to enter your GitHub username and password.  Assuming you followed all of the instructions outlined above, that's it!

## Downloading Future Notebooks

We will continue adding reading notebooks to the original upstream class repository. These will not show up in your forked copy unless you explicitly pull them in.

When the instructors have uploaded new reading assignments, you can pull them into your repository.

### One Time Setup: Add Upstream Remote

On your laptop, you should have a cloned copy of the ReadingJournal repository from your GitHub account. You can verify this by checking its remote repositories:

```bash
$ cd ReadingJournal
$ git remote -v

origin	https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname.git (fetch)
origin	https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname.git (push)
```

(Depending on how you set up your reading journal, you may see `https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname.git` instead of `git@github.com://{{ site.data.github.organization }}/ReadingJournal-myname.git`. Either is acceptable.)

We want to keep `origin` (the cloned copy in your GitHub account) for you to push completed work to, but we also want to add the original upstream class master repository for you to pull new assignments from. We can add this additional remote by running:

```bash
$ git remote add upstream https://github.com/{{ site.data.github.organization }}/ReadingJournal.git
```

If you run `git remote -v` now, you should see both `origin` and `upstream` listed.

### Pull New Notebooks from Upstream

Each time you want to grab the latest assignments, you should first first make sure all your recent work is committed. This is just to form good habits - each new reading journal assignment will be its own `.ipynb` file, so there should not be any conflicts.
Then:

1. In a terminal window in your ReadingJournal directory, run the following:
  ```bash
  $ git pull upstream master
  ```
  This should pull in the latest assignment notebook. It may trigger a merge process between the work you've previously done and the new notebook from the upstream repo. This will launch an editor with a merge message; save it to continue.
2. Run `jupyter notebook`.
3. You will see a list of files that includes the new notebook file. Click on the new notebook file to open and edit it.
4. When you are done editing the notebook, click the floppy disk icon <i class="fa fa-floppy-o" aria-hidden="true"></i>, or select the “File > Save and Checkpoint” menu item, to save your work to disk.
5. Follow the usual instructions to submit your work (add, commit, push to your `origin` repository).

## Checking that you've submitted your homework

Here’s how you can check your that you've submitted your Reading Journal:

* In a terminal in the `ReadingJournal` directory, type `git remote -v`. This reports the URL of your repository; for example: `https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname`.

* Open `https://github.com/{{ site.data.github.organization }}/ReadingJournal-myname` in a browser. Now there are several places you can verify that you’ve uploaded your work:
  * Right above the list of files, it says “{your name} Completed reading journal 1” and “Latest commit f080636 7 hours ago”
  * Next to `reading-journal-1.ipynb`, it says “7 hours ago”.
  * Click on `reading-journal-1.ipynb`, and you will see a (non-interactive) display of the notebook itself. This is verifies both that `git push` works, and that the file you pushed has the content you intended.
  * Above the list of files and above “{your name} Completed reading journal 1", there’s a row of icons “3 commits  1 branch  0 releases  1 contributor”. Click “3 commits”, and you’ll see a list of commits, most recent first.
