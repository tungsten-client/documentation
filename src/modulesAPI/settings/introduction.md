# Settings
The Modules API allows you to define many types of custom setttings, including the following:
- [CheckboxSetting](checkbox.md) - Toggleable checkbox with a boolean value
- [SliderSetting](slider.md) - A slider that works in a limited range
- [TextboxSetting](textbox.md) - A text box that allows for string input
- [ButtonSetting](button.md) - A button that runs a handle on click
- [GenericSetting (defining custom setting types)](generic.md) - The class that all settings extend and use in the ClickGUI

### Registering settings
A function on [GenericModule](../introduction.md) is `this.registerSettings`, which is very important to include when working with custom settings.
This function accepts all defined setting fields of the class, meaning you only have to define them and run the function for them to be registered.
```java
~package org.tungsten.client.feature.module.modules;
~
~import org.tungsten.client.Tungsten;
~import org.tungsten.client.feature.module.GenericModule;
~
public class ExampleModule extends GenericModule {
    public ExampleModule() {
        // super(title, description, category);
        super("Example", "Example module description.", "Default");

        // make sure settings are valid
        this.registerSettings();
    }
~
    ~@Override
    ~protected void disable() {
        ~// always run when the module is disabled
        ~System.out.println("Module Disabled.");
    ~}
~
    ~@Override
    ~protected void enable() {
        ~// always run whenthe module is enabled
        ~System.out.println("Module Enabled.");
    ~}
~
    ~@Override
    ~protected void tickClient() {
        ~// always run every tick
        ~System.out.println("A tick has passed.");
    ~}
}
```

### Reading from a setting
To get any setting's value, simply use `someSetting.getValue()`