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

### Git Setup
Required since git 2.0, it defines how the pushing mechanism works. This is the most intuitive option.
```bash
git config --global push.default simple
```

### Creating, Committing, and Pushing
Choose a partner to start this project off.

Agree on who is partner #1 and partner #2
#### Do WITH partner on partner #1's computer

1. In your home directory, create a new folder named `cs190lab7_<your_username>`.  Ex. I would create a folder `cs190lab7_sopell`.

  ```bash
  mkdir ~/cs190lab7_$USER
  ```

2. You will then `cd` into the directory created above and `init`ialize a new git repository.

   ```bash
   cd ~/cs190lab7_$USER
   git init
   ```

3. Download this template file [`calc.py`](./calc.py) into the repository you just created

  ```bash
  wget -O ~/cs190lab7_$USER/calc.py https://github.com/purduecs190/lab7/raw/master/calc.py
  ```

4. `add` this file to the repo

  ```bash
  git add <filename>
  ```

5. Log in to github (upper right hand corner of this page)

6. Create a new repository
  ![new repo button](http://i.imgur.com/Lhj1dUJ.png)

7. Enter in a repository name and do **not** check the box that says initialize with README.

8. Copy the https url from github

  ![click the copy button](http://i.imgur.com/O33PcIU.png)

8. Add this as a remote and push your commits

  ```bash
  git remote add origin <url from github>
  git push -u origin master
  ```

  > Notice that these are the exact commands from github!
  > Ask your TA about the -u if you're curious

8. Go to the repository settings
  ![settings location](http://i.imgur.com/qJAv62R.png)

9. Add your partner as a collaborator.


## Move to Partner #2's computer
Partner 2 needs a copy of this repo. If you remember from lecture, this is exactly what `clone` does.

  ```bash
  git clone <remote url>
  cd <repo name>
  ```

For the rest of this lab, pay attention to which section you're supposed to do.


## **Both** partners independently
### Run the Script

To run the calculator script, run the command `$ python calc.py`. The program will prompt you to enter input. Notice that there are 4 functions defined, `+, -, * and /`

### Implement New Operations
By the time you're done, you'll have two new operators, modulus division and exponentiation.  One partner will do each.

> Note: If you have any questions about Python syntax, ask your TA. It should be very straightforward.

> Be sure to test your code to make sure your functions work the way that they should.


1. Open up `calc.py` in your text editor (`$ pluma calc.py &`)

### Partner 1 only
2. Implement modulus division operator (%)

  > hint: what you're doing is very very similar to the div operator, but instead of using `/` to do regular division, you can use the `%` operator to do modulus division.

### Partner 2 only
2. Implement the exponent operator (**)
  > hint: what you're doing is very very similar to the multiplication operator, but instead of using `*`, you can use the `**` operator.

3. When you are done with your implementation, commit your changes

    > Remember `git add` and `git commit`. Be sure to check `git status` and `git log` afterward to make sure you successfully committed the changes.

4. Do a git pull to check for any changes. Run `$ git pull origin master`

    * If you are the second partner to finish your implementation, you will get a merge conflict. Don't panic. Skip to the next section and fix it together with your partner.

    * If you are the first partner to finish your implementation, move on to step 5.

5. Do a git push to publish your changes to Github so your partner can see them. Run `$ git push`

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

5. Run `$ git push` to publish your changes to Github so your partner can pull them down.

6. Your partner should now run `$ git pull origin master` on his/her computer to see that you fixed the conflict.

Now both of you should be able to run `$ python calc.py` on your separate computers and have a fully functioning
calculator CLI.

### Grading

* Run `$ git log -3` and show it to your TA

* Show your TA the open source project that you forked.

### Bonus: Setting up SSH keys

You may have noticed that every time you pull or push to Github, you have to enter your username and password. This is because
you are using the HTTPS protocol to connect to Github as a remote. This has a few advantages:

* It's easier and faster to set up
* It will still work on strict firewalls and proxies such as those restricting all ports but port 80

The downside is that you don't want to have to enter your credentials everytime you push and pull. There is another way. You
can set up the remote to use SSH instead of HTTPS. SSH uses RSA encryption which you can set up to be passwordless using
public keys. There is a great tutorial by Github on how to set up and use this method [here](https://help.github.com/articles/generating-ssh-keys/).
Note that you will need to add an SSH key for every different machine you want to clone on.
