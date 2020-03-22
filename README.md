# Automatic RoamResearch backup

This script help you backup your [RoamResearch](https://roamresearch.com/)!

This script automatically
- Download a markdown archive of your RoamResearch workspace
- Download a json archive of your RoamResearch workspace
- Unzip them to your git directory
- Commit and push the difference

# Why to use it

- You have a backup if RoamResearch lose some of your data.
- You have a history of your notes.
- You can browse your Github repository with a mobile phone.

# How to use it

## Setup

- Clone this repository locally: `git clone https://github.com/MatthieuBizien/roam_to_git.git`
- [Create a (private) Github repository for all your notes](https://help.github.com/en/github/getting-started-with-github/create-a-repo)
- Clone it into a `notes/` directory,
at the root of this repository. 
`git clone git@github.com:GITHUB_USERNAME/GITHUB_REPO notes`
- Create a `.env` file for storing your secrets (RoamResearch email and password):
`cp env.template .env`
- Fill the .env file: `vi .env`
- Install the required packages: `pip3 install -r requirements.txt` 
(python>=3.6 required, use [conda](https://www.anaconda.com/)  if needed)

## Manual backup

- Run the script: `./rr_download.py`
- Check your Github repository, it should be filled with your notes :)

## Automatic backup

One-liner to run it with a [cron](https://en.wikipedia.org/wiki/Cron) every hours: 
`echo "0 *  *  *  *  PATH=$(dirname $(which python)):\$PATH PYTHONPATH='$(pwd)' python3 -m roam_to_git" | crontab -`

# Task list

## Backup all RoamResearch data

- [x] Download automatically from RoamResearch
- [x] Create Cron
- [x] Write detailed README
- [x] Publish the repository on Github
- [ ] Download images (they currently visible in Github, but not in the archive so not saved in the repository 😕)

## Format the backup to have a good UI

### Link formatting to be compatible with Github markdown
- [x] Format `[[links]]`
- [x] Format `#links`
- [ ] Format `[[ [[link 1]] [[link 2]] ]]` 
- [ ] Format `((link))`

### Backlink formatting
- [x] Add backlinks reference to the notes files
- [x] Integrate the context into the backlink
- [ ] Manage `/` in file names

### Other formatting
- [x] Format `{{TODO}}` to be compatible with Github markdown
- [ ] Format `{{query}}``

## Make it for others
- [x] Push it to Github
- [ ] Add example repository
- [x] Make the backup directory configurable
- [ ] Add it to Pypi
- [ ] Publicize it
    - [ ] [RoamResearch Slack](https://roamresearch.slack.com/)
    - [ ] [RoamResearch Reddit](https://www.reddit.com/r/RoamResearch/)
    - [ ] Twitter

## Add features
- [ ] Add automatic Google Keep retrieval

## Some ideas, I don't need it, but PR welcome 😀
- [ ] Test it/make it work on Windows
- [ ] Pre-configure a CI server so it can run every hour without a computer
