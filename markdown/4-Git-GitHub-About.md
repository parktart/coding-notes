# Git and GitHub - About

## Naming Files

for files you will use in web development like .html, image files, text files, folders/directories, anything really - there are some good practices for **naming**:
~ no spaces or underscores (use hyphens) as hyphens are better for SEO
~ only lowercase letters
~ avoid special characters
~ keep file names short
~ keep file names descriptive
~ don't include dates or version control numbers
~ remember your file names will show up in the URL at some point - make them appropriate and helpful to any visitors of your site



## Git and Version Control

**Local Version Control** (RCS system) used 'patch sets' which were a special file format - each file recorded the differences between your versions - and could therefore re-create what any version looked like at any point in time by adding up all the patches

**Centralized Version Control System** (CVCS) - used a shared folder to store all the versioned files - but it wasn't necessarily backed up, so while it did allow for collaboration, you also risked losing everything if it was destroyed

**Distributed Version Control System** (DVCS) - such as Git - instead of copying (opening) just the file you want to edit, your michine fully mirrors the repository, including its full history, to your machine - thus if the server dies, each client might have a copy of the full repository as backup

How Git Works:

most other version control systems store information as a list of file-based changes - they recognize a set of files and the changes made to each file over time (sometimes referred to as delta-based version control)

Git, on the other hand, stores an entire snapshot of the project for each version - and if any file in the project hasn't changed from the last version, it uses a link, rather than a copy, of that file

so Git is more like a filesystem with some powerful tools built on top of it

and many of the operations in Git need only local files and resources to operate - since the 'filesystem' is stored locally - most operations do not experience network latency - and you can work offline, writing to your local copy of the repository, and just upload (push) to the cloud/shared repository when you regain connection

when you save (commit) a file with Git, the new file version is **checksummed**, meaning a 40-character string (using 0-9 and a-f) is produced via algorithm based on the contents of the file (or structure of a directory) - the algorithm will produce this exact string if you give it the same input (file/directory) again - in this way Git can check whether files are corrupted - Git uses SHA-1 hash checksumming, a hash may look like..

24b9da6552252987aa493b52f8696cd6d3b00373

Git actually stores everything in its database not by file name but by the hash value of its contents

Anything you do in Git will probably **add** data to your Git database - the system really isn't designed to erase data in any way

the only things you can lose are files that have not been pushed when your computer bricks



## Using Git

Git has three main states for files..

**modified** \- you have changed the file but not moved it to the staging area

**staged / index** - you have marked a modified file to be used in your next commit snapshot

**committed** \- means the data is safely stored in your local Git directory

so there are three main sections of a Git project:

**Working Tree** \- a single checkout of **one version** of the project - these files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify

**Staging Area** \- is a file, generally in your Git directory, that stores info about what will go into your next commit. It's technically called "the index", but “staging area” is the more common term

**Git Directory** \- is where Git stores the metadata and object database for your project. This is the most important part of Git, and is what is copied when you clone a repository from another computer

![Git Diagram](https://git-scm.com/book/en/v2/images/areas.png "Git diagram")



## Git Commit Messages

Remember a commit is a 'snapshot' of your code - actually a snapshot of the entire project at that point

it is best practice to **commit every time you make a meaningful change to your code**

that is.. every time you get a piece of code working how you want, or fix a typo, or fix a bug

When working with a team, you should define the team's convention to use for commit messages with regards to..
**Style** \- grammer, capitalization, punctuation, etc
**Content** \- what info should be included - not included?
**Metadata** \- should issue IDs, pull request numbers, etc be included?

or follow the well-established conventions of past programmers..



<u>The Seven Rules of a Great Commit Message</u>:

Limit the subject line to 50 characters if you can - summarize the changes made

Capitalize the first word of the subject line - just a common convention

Do not end the subject line with a period - just a common convention

Use the imperative mood in the subject line - aka write as an instruction - ex "Move metadata for readability" "Update intro documentation"

Separate subject from body with a blank line - this is necessary for certain Git commands to work properly

Wrap the body at 72 characters - you must wrap text manually - VSCode displays the column number

Use the body to explain what and why, not how - because the *code* explains how already - explain what changed and why to establish context for future developers - and if the *code* is complex it should have enough source comments to explain it

A properly formed Git commit `subject line` should make sense in the following sentence:

If applied, this commit will `subject line`




