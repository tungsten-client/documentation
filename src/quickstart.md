# Quickstart
A simple demonstration of the modules API.

```java
package org.tungsten.client.feature.module.modules;

import net.minecraft.SharedConstants;
import net.minecraft.text.Text;
import org.tungsten.client.Tungsten;
import org.tungsten.client.feature.module.GenericModule;
import org.tungsten.client.feature.module.config.ButtonSetting;
import org.tungsten.client.feature.module.config.CheckboxSetting;
import org.tungsten.client.feature.module.config.SliderSetting;
import org.tungsten.client.feature.module.config.TextboxSetting;

public class ExampleModule extends GenericModule {

    // new CheckboxSetting(checked, title, description)
    CheckboxSetting checkboxSetting = new CheckboxSetting(true,"CheckboxSetting","Example checkbox.");

    // new SliderSetting(default, min, max, title, description)
    SliderSetting sliderSetting = new SliderSetting(5,1,10,"SliderSetting","Example slider.");

    // new TextboxSetting(title, description, defaultValue)
    TextboxSetting textboxSetting = new TextboxSetting("Example", "TextboxSetting","Example textbox.");

    // new ButtonSetting(title, description, handle)
    ButtonSetting buttonSetting = new ButtonSetting("ExampleButton","Example Button",()->{
        if(Tungsten.client.player != null){
            Tungsten.client.player.sendMessage(Text.of(
                    "CheckBox: " + checkboxSetting.getValue().toString()
                            + "Slider: " + sliderSetting.getValue().toString()
                            + "Text: " + SharedConstants.stripInvalidChars(textboxSetting.getValue())
            ));
        }
    });

    public ExampleModule() {
        // super(title, description, category);
        super("Example", "Example module description.", "Default");

        // make sure settings are valid
        this.registerSettings();
    }

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