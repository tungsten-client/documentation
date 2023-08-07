# TextboxSetting
The TextboxSetting class allows you to accept string values in your module.

### Defining the setting
The TextboxSetting class has 3 fields:
- default - The placeholder text for the box
- title - The title of the setting
- prompt - The prompt for the text box (same functionality as description field on other settings)

```java
// new TextboxSetting(title, description, defaultValue)
TextboxSetting textboxSetting = new TextboxSetting("Example", "TextboxSetting", "Example textbox.");
```