# GitHub Authentication Error on Push

## Problem

Unable to push changes to a GitHub repository using HTTPS. Git asks for username and password, but authentication fails with an error message.

---

## Error Output

```bash
$ git push origin master
Username for 'https://github.com': <your-username>
Password for 'https://<your-username>@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/<username>/<repository>.git/'
```

---

## Cause

GitHub removed password authentication for Git operations over HTTPS in August 2021. Pushing with a GitHub password now fails due to security policy changes.

---

## Solution

There are two recommended authentication methods:

### Option 1: Use a Personal Access Token (PAT)

#### 1. Generate a token:

    - Visit: https://github.com/settings/tokens
    - Click "Generate new token" → "Classic"
    - Set scope to: repo
    - Copy and save the token securely

#### 2. Use the token instead of your password:

    - When prompted by Git:
        - Username → <your GitHub username>
        - Password → (Paste your personal access token)

#### 3. (Optional) Store credentials for future pushes:

```bash
git config --global credential.helper store
```

### Option 2: Switch to SSH Authentication

#### 1. Generate an SSH key (if not already created):

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

#### 2. Add the SSH key to GitHub:

    - Copy the key:

    ```bash
    cat ~/.ssh/id_ed25519.pub
    ```

    - Go to: https://github.com/settings/keys
    - Click "New SSH key", paste it, and save

#### 3.Update the Git remote to use SSH:

```bash
git remote set-url origin git@github.com:<username>/<repository>.git
```

#### 4. Push your changes:

```bash
git push origin master
```
---

## Recommendation

- For simple setups: Use HTTPS with a PAT

- For long-term use or automation: Use SSH authentication