# Authentication Instructions
Instructions to fix authentication issues with git and GitHub

This README consolidates:

* https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
* https://help.github.com/en/articles/adding-a-new-ssh-key-to-your-github-account
* https://mycyberuniverse.com/how-fix-fatal-authentication-failed-for-https-github-com.html

## Purpose

If you're trying to `git pull` or `git push` and running into an error that looks like this:

```
Username for 'https://github.com': Username
Password for 'https://Username@github.com':
remote: Invalid username or password.
fatal: Authentication failed for 'https://github.com/username/repository.git/'
```

...you've come to the right place!

## Generate an SSH Key and Add it to the SSH Agent on your machine

1. Open Terminal

2. `$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`

3. Press `Enter` approximately 3 times (Once to confirm that you will save your SSH key in `~/.ssh/id_rsa` and two to bypass the password - OR enter a password and confirm it if you so choose)

4. `$ eval "$(ssh-agent -s)"`

5. `$ ssh-add -K ~/.ssh/id_rsa`

6. Now we're going to add SSH to your GitHub account

## Adding a new SSH key to your GitHub account

1. `pbcopy < ~/.ssh/id_rsa.pub` (This command copies the already created SSH key to your clipboard as long as you've saved it in a file called `/id_rsa` in the previous section)

2. Open GitHub at `www.github.com/your-username`

3. Click on your user avatar and go to `Settings`

4. Click on the `SSH and GPG keys` link

5. Click `New SSH key` or `Add SSH key` button

6. In the "Title" field, add a descriptive label for the new key. For example, if you're using a personal Mac, you might call this key "Personal MacBook Air"

7. Paste your key into the "Key" field

8. Click `Add SSH key`

9. Confirm your GitHub password

10. Great! ALMOST THERE... one more set of steps...

## Create a GitHub Personal Access Token

1. In your GitHub's `Settings` page, click the `Developer settings` link

2. Click `Personal access tokens`

3. Click `Generate new token`

4. Give your token a name (Cannot have been used before)

5. Click every box so they're all blue

6. Click `Generate token`

7. Copy your token to the clipboard. **DO NOT exit from this page. Make sure the token is copied onto your clip board. You will not be able to access this token if you navigate away from this page**

8. Open Terminal

9. `cd` into a git repo

10. Run command `git pull` or `git push`

11. It will prompt you for your username: Enter your GitHub username

12. It will prompt you for your passowrd: Right-click and select `Paste` from the drop down. This will paste the previously copied access token into your Terminal. You will not see this token for security reasons. Do not press anything else other than `Paste` and then press `Enter`

13. You should have full `push` and `pull` access from this machine. If it didn't work, go back and copy the access token to your clip board again and try pushing or pulling within a git repository. You might have typed your username incorrectly or maybe the access token didn't copy or paste properly.

14. You're welcome.
