# ButtonSetting
The ButtonSetting class allows you to run a handle when a button is pressed.

### Defining the setting
The ButtonSetting class has 3 fields:
- title - The title of the setting
- description - The description of the setting
- handle - The `Runnable` called when the button is pressed.

```java
~import net.minecraft.text.Text;
~
// new ButtonSetting(title, description, handle)
ButtonSetting buttonSetting = new ButtonSetting("ExampleButton", "Example Button", () -> {
    if(Tungsten.client.player != null) { 
        Tungsten.client.player.sendMessage(Text.of("Hello world"));
    }
});
```