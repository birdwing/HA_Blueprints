# 🌐 This my Home Assistant Blueprint Library

Script Blueprints can be found in the [Scripts](https://github.com/birdwing/HA_Blueprints/scripts) folder and Automation Blueprints can be found in the [Automations](https://github.com/birdwing/HA_Blueprints/automations) folder.
Each Blueprint has it's own folder. Inside that folder is a file with the .yaml suffix with all the code that can be imported into Home Assistant.
Some of the more compliated Blueprints will also have a file README.md file to help with set-up and usage of the blueprint.
Always check The README.md file if it exists because it will contain important information and if you want a successful install, you should read it.

## ⚙ Want to request a new feature request or found a BUG?

[Open an issue on GitHub](https://github.com/birdwing/HA_Blueprints/issues/new/choose).

## ☕ Tips are always welcome, but never required 😉

PayPal one-off donation link: https://www.paypal.me/aronwithana
  
  
# 📃 The Big List 📃

Here is a list of each of my blueprints, a quick description, an import link for import to Home Assistant, and jump links to the files in my GIT Repo...

## 🔃 Automations

### 🔔 To-do List Chore Notifications

This is an automation Blueprint that generates actionable notifications from a Home Assistant To-do list.
These actionable notifications are sent every day at the time you specify, through the notify service that you enter.
It will generate 1 notification for each passed due item, with the ability to mark the item as completed right from the notification.
There is also an optional *When chore is completed* actions section. This allows you to define actions to run when any chore is marked complete (from the notification). There is also a variable called "todo_item" which holds the name of the completed action. Using this variable along with conditions it is possible to run different actions based on the name of the completed chore.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fbirdwing%2FHA_Blueprints%2Fblob%2Fmain%2Fautomations%2Fto-do_chore_notifications.yaml)

#### 📂 Files
* [to-do_chore_notifications.yaml](automations/to-do_chore_notifications/to-do_chore_notifications.yaml)
* [README.md](automations/to-do_chore_notifications/to-do_chore_notifications.md)
