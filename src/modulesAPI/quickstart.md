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

    CheckboxSetting checkboxSetting = new CheckboxSetting(true, "CheckboxSetting", "Example checkbox.");

    SliderSetting sliderSetting = new SliderSetting(5, 1, 10, "SliderSetting", "Example slider.");

    TextboxSetting textboxSetting = new TextboxSetting("Example", "TextboxSetting", "Example textbox.");

    ButtonSetting buttonSetting = new ButtonSetting("ExampleButton", "Example Button", () -> {
        if(this.client.player != null) {
            this.client.player.sendMessage(Text.of(
                    "CheckBox: " + checkboxSetting.getValue().toString()
                            + "Slider: " + sliderSetting.getValue().toString()
                            + "Text: " + SharedConstants.stripInvalidChars(textboxSetting.getValue())
            ));
        }
    });

    public ExampleModule() {
        super("Example", "Example module description.", "Default");
        this.registerSettings();
    }

    @Override
    protected void disable() {
        this.logger.info("Module Disabled.");
    }

    @Override
    protected void enable() {
        this.logger.info("Module Enabled.");
    }

    @Override
    protected void tickClient() {

    }

    // Example event subscription. To subscribe to an event, apply @MessageSubscription to a method with the parameter being the event you want to subscribe to.
    @MessageSubscription
    void onPlayerMove(PlayerMoveEvent event) {
        this.logger.info(
                "Move type: %s, Requested Delta: %s".formatted(event.getType(),event.getRequestedDelta())
        );
    }
}
```