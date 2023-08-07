# GenericModule
The GenericModule class is the base class for all modules.

To create a module, you must extend it.

### Extending GenericModule
The GenericModule superclass's initialization function has 3 params:
- title - The title of the module displayed in the ClickGUI
- description - The description of the module
- category - The category the module appears in (creates a new one if there is no category with that name)

It also comes with a `client` field, so use that when needing to do anything that interacts with the minecraft client.

You also likely want to use the `this.registerSettings` function provided if you are using [Custom Settings](settings/introduction.md)
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

### Generic Events
It also has `onEnable`, `onDisable`, and `onTick` methods that you can override:
```java
~package org.tungsten.client.feature.module.modules;
~
~import org.tungsten.client.Tungsten;
~import org.tungsten.client.feature.module.GenericModule;
~
public class ExampleModule extends GenericModule {
    ~public ExampleModule() {
        ~// super(title, description, category);
        ~super("Example", "Example module description.", "Default");
~
        ~// make sure settings are valid
        ~this.registerSettings();
    ~}
~
    @Override
    protected void disable() {
        // always run when the module is disabled
        System.out.println("Module Disabled.");
    }

    @Override
    protected void enable() {
        // always run whenthe module is enabled
        System.out.println("Module Enabled.");
    }

    @Override
    protected void tickClient() {
        // always run every tick
        System.out.println("A tick has passed.");
    }
}
```