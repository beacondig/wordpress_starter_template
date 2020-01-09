# Continuous Integration Template for Wordpress

## Initial wordpress setup

_if wpengine_

1.  Login to [wpengine](wpengine.com).
2.  Navigate to the backup point of the production branch on wpengine
3.  create a backup and download full version of it
4.  Unzip the backup and place this repo in the themes folder. We will not be tracking anything outside of the theme we are developing

## Gulp setup

## [Github Action](https://github.com/features/actions) setup

_All Github Action settings will be housed in `./github/workflows` directory. There will be up to three workflows depending on how many environments we have. For example wpengine will have 3 -- 1 for production, 1 for staging and 1 for development. The git branch names will coordinate with the environment._

### WPEngine Setup

For each of the wpengine site branches (production, staging and development), navigate to the Git push page and enter ssh public key.  
From Terminal type `pbcopy < ~/.ssh/id_rsa.pub`
If a key exists, this will copy it to your clipboard. You can then paste it into wpengine/

Open the github repository associated with this project and navigate to settings - secrets. URL will end with `/settings/secrets`
You will be creating 3 secrets
1st Secret:
name = `SSH_PUBLIC_KEY`
value = the same key that you entered for wpengine
2nd Secret:
name = `SSH_PRIVATE_KEY`
value = Your ssh private key which can collected by using this command `pbcopy < ~/.ssh/id_rsa`
3rd Secret:
name = `KNOWN_HOSTS`
value = the server key. this can be collected by using this command in terminal `ssh-keyscan -H git.wpengine.com` where `git.wpengine.com` would be substituted with whatever server you are attempted a connection if not wpengine. Presently, the key for wpengine is

```
|1|gfyaEw5lW9KCfgllS0USygOEaL4=|yOzCaQMtVM3RfD/iLGEIr/6yu8Y= ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEApRVAUwjz49VKfuENfyv52Dvh3qx9nWW/3Gb7R9pwABXUNQqkipt3aB7w2W6jOaEGFmzSr/4qhstUv0lvbeZu/1uRU/b6WrqULu+9bAdt9ll09QULfMxAIFWDwDS1F6GEZT+Yau/wLUI2VTZppxSVRIPe20/mxgXk8/Q9ha5tCaz+dQZ9lHWwk9rbDF+7LSVomLGM3e9dwr6mS4p37Qkje2cFJBqQcQ+RqEOTOD/xiFU0DH8TWO4R5yibQ0KEZVACkwhaAZSl81F7YZrrLEfsFS/llgpV3YZHQGvFi0x/ELAUJMFE9umdy9EwFF7/lTpV8zOGdiLW+v8svweWJJJ00w==
# git.wpengine.com:22 SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
|1|IPROQpQm20A8ZFByhYD8jimWF4w=|voIUejN6PhUhVX7w+a2AzWxPJ9M= ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKPFgZ9SUnEqp6yVjT4plVEADyyO7/LQuVqAvOAKF24X1JDgQwT7Fge8daPQYiXZN6vN+UaPIyEGy8fY3xkYbhA=
```

For more info on setting up a ssh key, see [here](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
