There are two kinds of changes that can be made - core changes and database changes. A core change is a modification to any of the source code included in the repository, that basically means changes to any of the "_.cpp_" and "_.h_" files. In order to edit the core's source code you'll need to be fluent in the [C++](https://en.wikipedia.org/wiki/C%2B%2B) programming language. Database changes are done by creating new "_.sql_" files called migrations which contain SQL statements that alter the data or structure of database tables. In order to make changes to the database you need to be familiar with the [SQL](https://en.wikipedia.org/wiki/SQL) database management language.

## Making database changes.
To create a migration, navigate to the "_sql_" directory and use the batch script there. The newly created migration can be found in "_sql/migrations_". The name of the migration consists of the date and time when it was created and the database to which it should be applied. By default any migrations created with the batch script are for the world database, but you can change that by just renaming the migrations. Here are a few examples.

- `20171101091800_world.sql`

This is a migration for the world database, you can tell by it's name that it was created on the 1st of November 2017 at 9:18:00.

- `20171030141951_logon.sql`

This migration is intended for the logon database and was made on the 30th of October 2017 at 14:19:51.

The names of the migrations determine the order in which they are applied, so make sure you use the batch script to create your migration instead of giving it an arbitrary name yourself. Having migrations executed out of order can cause them to fail to apply or lead to unintended consequences.

An empty migration looks like this:

![empty migration](https://i.imgur.com/dRGqKnI.jpg)

That code is generated automatically by the batch script used to create new migration files. It's a procedure that checks if the migration has already been applied to the world database, and if it has not it executes the SQL queries contained within it. You are meant to paste your SQL queries in the middle of it, as implied by the comments.

## Making core changes.
If you are going to be making core changes, then you are already at least somewhat experienced in programming and won't need to have your hand held all the way through, but there are some rules specific to this project that you need to remember.

- Code must be C++14 compliant, no C++17 yet.

The currently targeted version of Visual Studio is 2015 Update 2, so any code must be able to compile on that. This is also the minimum version supported, so if you are using an older version you'll need to upgrade.

- We use spaces, not tabs.

Make sure you use 4 spaces for indentation in your code, not tabs. If you overlook this, you will be asked to replace all the tabs with spaces before your pull request is merged. By default Visual Studio uses tabs, but you can change this by going to _Tools->Options->Text Editor->All Languages->Tabs_.

![visual studio options](https://i.imgur.com/LY6rHnN.jpg)

- If it can be done in the database, do it there.

When scripting something, it is preferable that you do it using the database scripting engine if possible. ScriptDev is for complex encounters that cannot be done any other way.

- No magic numbers.

When you need to use IDs of spells, creatures, texts or something else in your core script make sure to add it to an _enum_ so that your code is readable by humans.

- No hardcoded texts.

Do not define string literals for commands or scripts, instead either find the text in the `broadcast_text` table if it is a blizzlike text, or add it to `mangos_string` in the case of system texts. All in-game texts need localization, and there is no way to do that outside of the database.

## Creating a branch and making pull requests.
_This section is intended for people who have not used git before, you may skip it otherwise._

In order to contribute your changes back to the public repository you will need to make a pull request, and to do that you need to make a separate branch on your own fork. Open up a command prompt and navigate to the directory where you'd like to clone the repository, then type the following sequence of commands to create a new branch based on the latest development revision:

`git clone http://github.com/<your_user_name>/<fork_repo_name>`

`cd <fork_repo_name>`

`git remote add upstream https://github.com/vmangos/core.git`

`git fetch upstream`

`git checkout upstream/development`

`git checkout -b <new_branch_name>`

`git push --set-upstream origin <new_branch_name>`

You may delete the "server" folder that was downloaded at the end, as that is **not a copy of the new branch** you created, but the default branch of your fork. To clone the newly created branch type this:

`git clone -b <new_branch_name> http://github.com/<your_user_name>/<fork_repo_name>`

You can now start working on your fix using the local copy of the new branch. When you are done and want to push the changes back to github, navigate to the cloned "server" folder with the command prompt and use the following commands.

- `git status`

This command will show you a list of files that have been changed. In order to include any of the changes to those files in your commit, you need to use the command below.

- `git add --all`

Adding --all will include all changed files in your commit, including any new files. If you don't want to include all changed files, only specific ones, then instead of "--all" type the name and path to the file. You can verify that it has been included by typing "git status" again, where the included files should appear in green.

- `git commit -m "short name describing the changes"`

This creates a new commit with the name specified and all the files you chose to include. It does not upload the commit to github, to do that use the command below.

- `git push`

Uploads all local commits to github.

You may now open a pull request from the website. Remember to give it a good name and a detailed description of what you changed. If it is a solution to an already existing issue on our github repository, then you can just link to the issue it fixes.