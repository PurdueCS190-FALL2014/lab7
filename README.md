# CS 190 Lab 7 - Basics of Git Part 2: Remotes and Github

The purpose of this lab is to become comfortable and fluent with projects using Github.
By the end of the lab, you should know how to create and fork repos, add collaborators, clone, push, pull,
and fix minor merge conflicts.

__For quick reference on the git commands we covered, see the cheat sheet [here] (https://github.com/PurdueCS190/lab7/blob/master/cheat_sheet.md)__

## The Lab

In this lab, you will work together with a partner to implement a piece of software. Your job is
to implement a simple command line interface (CLI) for a four function calculator in Python. The skeleton
for this is in `calc.py` of this repo.

### General Setup

This command sets your default editor (just for today's lab) to be pluma for merge messages.

```bash
export EDITOR="pluma"
```
> This only lasts as long as the terminal window you ran it within. As soon as you close the window, this setting is lost.

### Repository Setup
#### Do WITH partner on ONE computer

1. Fork this repository
    
    > Forking a repo

    > ![*Creating a Repo*](https://github.com/PurdueCS190/lab7/blob/master/res/fork_repo.jpg)

    > Note: This time we are forking, but you can also create a brand new repository by clicking the
      plus button at the top of your screen and following the instructions.

2. Add your partner as a collaborator

    > Go to the repo settings

    > ![*Go to the repo's settings*](https://github.com/PurdueCS190/lab7/blob/master/res/repo_settings.jpg)

    > Add your partner as a collaborator

    > ![Add your partner](https://github.com/PurdueCS190/lab7/blob/master/res/add_collab.jpg)

### Clone the Repository
#### Do on both computers

1. Copy the clone URL from Github to your clipboard. There is a special button that makes it very simple to do this.
Make sure that the HTTPS protocol is selected *(Bonus: See end of lab for instructions to set up SSH keys)*

2. Navigate to your home directory

3. Run the command `$ git clone <clone URL>` pasting in the URL you just copied

4. Navigate into the repository

### Run the Script

To run the calculator script, run the command `$ python calc.py`. The program will prompt you to enter input. Notice
That addition works, but all the other operations return 0. You will implement them today.

### Implement the Calculator

Now it is time to implement. Follow these instructions carefully.

1. Open up `calc.py` in your text editor (`$ pluma calc.py &`)

2. Implement the functions that do subtraction, multiplication, and division.

    > __Partner 1__: Implement __*sub(a, b)*__ and __*mult(a, b)*__.

    > __Partner 2__: Implement __*mult(a, b)*__ and __*div(a, b)*__.

    > Notice that you will both be implementing __*mult(a, b)*__.

    > Note: If you have any questions about Python syntax, ask your TA. It should be very straightforward.

    > Be sure to test your code to make sure your functions work the way that they should.

3. When you are done with your implementation, commit your changes

    > Remeber `git add` and `git commit`. Be sure to check `git status` and `git log` afterward to make sure you
      successfully commited the changes.

4. Do a git pull to check for any changes. Run `$ git pull origin master`

    > If you are the second partner to finish your implementation, you will get a merge conflict. Don't panic. Skip to the
      next section and fix it together with your partner.

    > If you are the first partner to finish your implementation, move on to step 5.

5. Do a git push to publish your changes to Github so your partner can see them. Run `$ git push origin master`

    > When done with this part, wait for your partner to finish his/her implementation.

### Merge conflict
#### Do WITH partner on ONE computer

If you were the second partner to finish your implementation, you will have gotten merge conflict when you tried to pull.
This is because both of you implemented the __*mult(a, b)*__ function. Let's fix this conflict.

1. Open up `calc.py` in your text editor (`$ pluma calc.py &`)

2. Look for the pattern of `<<<<<<<<` and `>>>>>>>>` in the code. This is where the merge conflict exists.

    > Notice how your changes are marked by HEAD and your partner's changes are marked by a commit hash from the remote.

3. Edit the code to be implemented how you want it. You can either keep your implementation, or your partner's implementation
   or mix the two. It's your choice how you want to fix the conflict. Do this with your partner.

4. When you are done editing, git add the file and commit.

5. Run `$ git push origin master` to publish your changes to Github so your partner can pull them down.

6. Your partner should now run `$ git pull origin master` on his/her computer to see that you fixed the conflict.

Now both of you should be able to run `$ python calc.py` on your separate computers and have a fully functioning
calculator CLI.

### Grading

Show your git log to your TA

### Bonus: Setting up SSH keys
