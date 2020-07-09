---
title: upgrade3-4
description: 
extends: _layouts.documentation
section: content
---

# Move from version 3.1 to 4.0 {#upgrade3-4}

## Introduction {#introduction}
On purpose we call this not an upgrade but a move. To make this clear: There is no possible way to 'in place' upgrade your 2.0, 3.0 and 3.1 telegram bot to 4.0. Telegram-bot-sdk 4.0 is a complete new package with a ton of new functionalities. To move from an older version to this new 4.0 version we need to remove the old package and install the new package. After that we need to change the config file and change some code. This chapter will tell you all about it.

Let's assume you have a working Laravel app with Telegram bot sdk 3.x integrated. You have some Telegram Commands in place and you send out messages from different classes in your app.

Before you begin. Please make a backup of your complete project folder or use git to keep track of changes and undo changes.

## Removing the 3.1 version {#remove3.1}
Remove your current installation of the Telegram Bot SDK by running the following command inside your Laravel project folder:

```
composer remove irazasyed/telegram-bot-sdk ^3.1
```

After this command has completed you can check your vendor folder and make sure that the folder 'irazasyed/telegram-bot-sdk' is gone.

## Rename old config file {#renameconfig}
In your project config folder there is still your old 'telegram.php' config file. Rename this file to 'telegram_old.php'. We might need some information from that config in the new config.

```
mv config/telegram.php config/telegram_old.php
```

## Install the new 4.0 SDK {#install4.0version}

Now we are ready to install the new 4.0 version of Telegram bot SDK:

```
composer require telegram-bot-sdk/laravel ^4.0
```

##Publish new Telegram configuration file {#publishnewtegramconfig}

Publish the Telegram config file to the Laravel config folder:

```
php artisan vendor:publish --provider="Telegram\Bot\Laravel\TelegramServiceProvider"
```

We now have a new telegram.php config file and the old renamed telegram_old.php config file.


