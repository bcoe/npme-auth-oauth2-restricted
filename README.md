# npme-auth-oauth2

[![Build Status](https://travis-ci.org/npm/npme-auth-oauth2.png)](https://travis-ci.org/npm/npme-auth-oauth2)
[![Coverage Status](https://coveralls.io/repos/npm/npme-auth-oauth2/badge.svg?branch=master)](https://coveralls.io/r/npm/npme-auth-oauth2?branch=master)

auth strategy for OAuth2 SSO.

# Instructions

> Note: The whitelist file and plugin should both be saved/installed to the Miscellaneous Data Files folder as you've configured it for your npmE instance.

> The default is `/usr/local/lib/npme/data`

## Installation

The change directory command may be different based on your configuration (see note above).

```shell
cd /usr/local/lib/npme/data
sudo npm i @bcoe/npme-auth-oauth2-restricted

```

## Configuration

Go to your npm Enterprise admin console (on port 8800 of your server), select the `Settings` tab and then choose the `OAuth2` option under the `Authentication` section. Fill out the configuration fields for your OAuth provider and click `Save` to apply your setting.


Next, switch to `Custom` for Authentication and populate each of the plugin settings as `/etc/npme/data/node_modules/@bcoe/npme-auth-oauth2-restricted`:

|Config Field           |Config Value|
|-----------------------|------------|
|Authorization plugin  | /etc/npme/data/node_modules/@bcoe/npme-auth-oauth2-restricted  |
|Authentication plugin | /etc/npme/data/node_modules/@bcoe/npme-auth-oauth2-restricted  |
|Session plugin        | /etc/npme/data/node_modules/@bcoe/npme-auth-oauth2-restricted  |

Click `Save` a final time to apply these settings.

## Whitelist

Create the whitelist file, `user-whitelist.txt` in the `Misecellaneous Data Files` directory (ex: `/usr/local/lib/npme/data`).

Each user that you want to have access to npmE must be listed on a separate line, by their email address (Note: The email associated with your github account that you are using for authentication should be [public](https://help.github.com/articles/setting-your-commit-email-address-on-github/) for GitHub protal.)

To restrict package installs within the users that are listed in `user-whitelist.txt` file, visit npm Enterprise's admin console and set `Auth All Installs` to `Yes`.

## Restart Your Instance

Navigate to your instance's dashboard and use the buttons to stop and restart the instance. After the restart, only users in the whitelist file will be permitted to install and publish the packages.