# CheckboxSetting
The CheckboxSetting class allows you to have boolean settings in your module.

### Defining the setting
The CheckboxSetting class has 3 fields:
- default (bool) - Whether the checkbox starts out checked
- title - The name of the checkbox
- description - The description of the checkbox

```java
// new CheckboxSetting(default, title, description)
CheckboxSetting checkboxSetting = new CheckboxSetting(true, "CheckboxSetting", "Example checkbox.");
```