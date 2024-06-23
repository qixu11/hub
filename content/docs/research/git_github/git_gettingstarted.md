---
title: "Getting Started with Git & GitHub"
summary: " "
weight: 1
---

## Setting Up Git & GitHub on HiperGator

To get started with Git on HiperGator for our collaborative projects, follow these detailed steps:
1. **Create a GitHub.com account**:
   - Navigate to [GitHub.com](https://github.com/) and click the Sign up button.
   - Enter the requested information to create your account.
2. **Log in to HiperGator**: Open a terminal and login to HiperGator using your gatorlink credentials.
3. **Generate SSH Keys**:
   - Generate a new SSH key pair using the following command in the terminal:
     ```
     ssh-keygen -t ed25519 -C "your_github_email@example.com"
     ```
     Replace `your_github_email@example.com` with your actual GitHub email address. Create a passphrase when prompted (note: this is not compatible with Jupyter Lab).
   - Retrieve the public portion of your SSH key with:
     ```
     cat ~/.ssh/id_ed25519.pub
     ```
   - Copy the SSH key and add it to your GitHub account by following the steps in [this tutorial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).
4.**Test the SSH Connection**:
   - Ensure that GitHub is recognized by your machine:
     ```
     ssh -T git@github.com
     ```
     Follow the prompts to add GitHub to your known hosts.
5. **Configure Git**:
   - Set your username and email in Git with the following commands:
     ```
     git config --global user.name "John Doe"
     git config --global user.email "johndoe@example.com"
     ```
     Replace `John Doe` and `johndoe@example.com` with your name and email.
   - Set the default editor to vim (or your preferred editor):
     ```
     git config --global core.editor vim
     ```
   - Ensure you have two-factor authentication and SSH keys set up for GitHub to secure your account.
6. **Setting up Two-factor Authentication**:
   - As a best practice, it's highly recommended to enable two-factor authentication whenever possible. GitHub supports this feature and it can be configured under the [Security](https://github.com/settings/security) section in your account settings.
  
## Creating a Repository

1. To create a new repository, start by navigating to GitHub. Click the `+` icon in the top right corner and select `New repository`. Name your repository (e.g., _planets_) and leave the other settings at their defaults before clicking `Create repository`.
2. If you've set up your GitHub account to use SSH keys, make sure to select the SSH option. If you haven't, stick with the HTTPS option. 
3. Once your repository is created, it will be empty. To begin adding content, you can follow the steps provided by GitHub under "…or create a new repository on the command line." Here’s a streamlined approach that you can follow on your local machine or a remote server like HiPerGator:
   1. Log into your server or open your terminal: `ssh gatorlink@hpg.rc.ufl.edu`
   2. Create a directory named `planets`: `mkdir planets`
   3. Navigate into this directory: `cd planets`
   4. Initialize a git repository: `git init`
   5. Create a README file and add initial content: `echo "# planets" >> README.md`
   6. Track changes to the README file: `git add README.md`
   7. Commit the changes: `git commit -m "first commit"`
   8. Set the default branch name to 'main': `git branch -M main`
   9. Link your local repository to GitHub: `git remote add origin git@github.com:your_username/planets.git` (replace `your_username` with your actual GitHub username)
   10. Push the changes to GitHub: `git push -u origin main`

If SSH keys are not set up, you will be prompted for your GitHub username and password during the push command.


## Basic Git Commands

To make changes in your repository, you can use a command line or a text editor. For example, to create a new file named `mars.txt`, you might use Nano:
```
nano mars.txt
```
Add some text to the file, save, and exit the editor. You can check the contents of your directory with:
```
ls
```
This will show the files in your directory, including `mars.txt` and any others like `README.md`.

To check the status of your repository, use:
```
git status
```
This command will show any untracked or changed files. For example, `mars.txt` will appear as an untracked file. To track changes to this file, use:
```
git add mars.txt
git status
```
This will update the status to show `mars.txt` as a staged file ready for committing. You can commit these changes with:
```
git commit -m "Start notes on Mars as a base"
git status
```
After committing, if you check the status, you'll see a message indicating that your branch is ahead of 'origin/main' by one commit, suggesting you might want to push your changes to the remote repository on GitHub:
```
git push
```
This command transmits your local changes to the GitHub repository. Refreshing your GitHub page will show the new `mars.txt` file and the commit message.

Next, we further modify `mars.txt` and check the changes:
```
git status
git diff
```
`git diff` will display the exact changes made since the last commit. To include these new changes in the repository, run:
```
git add mars.txt
git commit -m "Add concerns about effects of Mars' moons on Wolfman"
git push
```
This final push will update the remote repository with all recent changes.


## Additional Resources and Guides

There are numerous excellent tutorials available for learning both Git and GitHub. Below is a list of resources that I have found particularly useful in developing this training:

| Source | Notes |
| ------ | ----- |
| [Software Carpentry Version Control with Git](http://swcarpentry.github.io/git-novice/) | A well-regarded module from the Software Carpentry curriculum, designed for a 3-hour instructor-led session but also suitable for self-study. |
| [GitHub Learning Lab](https://github.com/apps/github-learning-lab) | Offers a variety of lessons that guide users through hands-on exercises to learn Git and GitHub functionalities directly on the platform. |
| [Try GitHub](https://try.github.io/) | Provides additional GitHub tutorials. |
| [GitHub Education](https://github.com/edu) | Contains information on educational discounts and benefits, which are updated regularly. |
| [GitHub Classroom](https://classroom.github.com/) | An excellent resource for instructors using Git in the classroom. It facilitates the management of both individual and group assignments and offers classroom tools and freebies like stickers. |
| [GitHub Pages](https://pages.github.com/) | Guides on using GitHub to host websites. |
| [Bitbucket](https://bitbucket.org/product) | Another popular Git repository hosting service, offering an alternative to GitHub. |
| [GitLab](https://about.gitlab.com/) | Provides additional options for Git hosting, with comprehensive features for collaboration. |
