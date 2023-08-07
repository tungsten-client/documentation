# GenericSetting (defining special setting types)
The GenericSetting class allows you to define custom setting types.

### Inheriting from GenericSetting
GenericSetting accepts a generic type `V`, which stands for the type of the value that the setting returns.

This means you want to use `class SomeSetting extends GenericSetting<SomeType>`

#### Overriding toHTML
Tungsten's ClickGUI system utilizes [Ultralight](https://github.com/LabyMod/ultralight-java), which means it uses HTML to render things like modules and settings.

Generally, the easiest way to convert your setting to an HTML object is to use `String#format`

### Example
```java
class ColorSetting extends GenericSetting<Integer> {
    public ColorSetting(int defaultVal, String name, String description) {
        super(defaultVal, name, description);
    }

    @Override
    public String toHTML() {
        return String.format(
            "<input type=\"color\" value=\"%s\">",
            this.value
        );
    }
}
```

---

You can see the [GenericSetting](https://github.com/tungsten-client/tungsten/blob/main/src/main/java/org/tungsten/client/feature/module/config/GenericSetting.java) class for more info.