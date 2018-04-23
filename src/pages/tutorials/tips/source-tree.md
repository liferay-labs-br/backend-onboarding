---
title: "Source Tree"
description: "This section shows some tips related with Source Tree."
layout: "tips"
icon: ""
weight: 2
---

###### {$page.description}

<article id="1">

## New Bug?

1. Access the SourceTree.
2. Update main branch (pull).
3. Create a local branch only to work on the bug fixes.
    - Remotes -> Upstream -> Master -> Checkout
4. Nomeie a nova branch pelo código do bug.
    - **E.g.:** LPS - 1234.

</article>

<article id="2">

## Do you want to commit?

1. Check for inconsistencies in the changed code.
2. Run testes.
3. Save the work.
    - Save as Stache.
4. Update master branch (pull).
5. Commit
    - Your changed code will be in 'File status'
6. Perform push (enable 'force push').
    - If the checkbox is not showing, enable it via: SourceTree -> Preferences -> Advanced -> Allow force push.
7. Run the pull request through the terminal.
    ```
    'gh pr -s liferay' 
    ```

</article>

<article id="3">

## Confusion after committing?

###### Did you commit any separate commit that should have gone next to another or missed the message of a commit? You can solve the problem by:
- **Interactive Rebase**

 1. Identify the commit that generated the problem. 
 2. Select the commit just below it and choose the 'Rebase children of XXX interactively' option.
 3. Pop-up will open and a list of commits will be displayed. Identify the one you want.
 4. To edit the message of a commit, select it and click 'Edit message'.
 5. To join two separate commits, drag the desired commit one position above the other desired one and click 'Squash with previous'.

- **Reset Master**

1. Identify the commit that generated the problem.
2. Select the commit just below it and choose the option 'Reset master to this branch'.
3. Any modifications made by you before this commit will return to the file status.
4. Reorganize your commits.

</article>


