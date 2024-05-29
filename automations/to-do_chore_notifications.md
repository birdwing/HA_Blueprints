# 🔔 To-do List Chore Notifications

## 📗 F.A.Q

### 1. What to-do / task tracking integrations work with this Blueprint?
Any integration that makes use of Home Assistants [To-do entities](https://www.home-assistant.io/integrations/todo) should work with this blueprint.
Integrations I have tested myself are:
- Home Assistants built in [Local To-do](https://www.home-assistant.io/integrations/local_todo/) integration.
- [Google Tasks](https://www.home-assistant.io/integrations/google_tasks/)
  - Google Tasks has the advantage of being able to create recurring tasks that will automatically "uncheck" themselves and update their due date after they are marked done.

### 2. What notify services work with this Blueprint?
This blueprint was designed to work with the notification services provided by the Home Assistant [Companion App](https://companion.home-assistant.io/).
It works for both Android and IOS.

### 3. IOS Notifications aren't showing the "Mark Done!" notification action, whats wrong?
Apple devices running IOS do not show the notification actions automatically. On IOS you must *tap and hold* on the notification then the "Mark Done!" action will be displayed.
Simply tapping on the notification, or swipping it away will *not* mark the task as done.
This is a limitation of IOS, and there is no way to change this functionality.
> [!TIP]
> If this is an issue I recommend putting a note in the task name or description, on each to-do list item, to remind you to tap and hold on the notification in order to mark it as done.

## 📃 *When Chore is Completed* - Custom Actions After Task is Marked Done
> [!IMPORTANT]
> These actions will only run *if the task was marked done through the notification*!
> If the task is marked done directly through the Home Assistant To-do list screen, or from the integration screen these actions will not run.

### Example Use Cases:
> [!TIP]
> A variable named **todo_item** is created when a task/chore is marked complete, this can be used within your custom actions along with Home Assistants [Chose](https://www.home-assistant.io/docs/scripts/#choose-a-group-of-actions)
> action along with the [Template Condition](https://www.home-assistant.io/docs/scripts/conditions/#template-condition) to specify different actions for each task/chore.

#### 1. Use a Counter Helper to Keep Track of an Item in Stock
If you have a task/chore that requires having something in stock, such as Air filters or Chlorine Tablets, you can create a Home Assistant [Counter Helper](https://www.home-assistant.io/integrations/counter/)
to keep track of how much you have in stock.
Then when your "Replace Air Conditioner Tablets" task/chore is marked complete on your to-do list, you can call the [counter.decrement](https://www.home-assistant.io/integrations/counter/#service-counterdecrement) service
for that Counter Helper to keep automatically update how much is left in stock.

*Yaml put into the "When chore is completed" blueprint input.*
```yaml
choose:
  - conditions:
      - condition: template
        value_template: "{{ todo_item == 'Replace Air Conditioner Tablets' }}"
        alias: "Make sure name is: Replace Air Conditioner Tablets"
    sequence:
      - service: counter.decrement
        target:
          entity_id: counter.ac_tablets_in_stock
        data: {}
```
The important part is the *template condition's* **value_template** where we compare the **todo_item** variable, which is the task/chore that was just marked done, with the name of the chore we want to perform that
specific action for:
```yaml
value_template: "{{ todo_item == 'Replace Air Conditioner Tablets' }}"
```
