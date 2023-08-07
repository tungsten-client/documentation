# SliderSetting
The SliderSetting class lets you recieve integer inputs within a range.

### Defining the setting
The SliderSetting class has 5 fields:
- default - The starting value of the slider
- min - The minimum number that the slider will allow
- max - The maximum number that the slider will allow
- title - The title of the setting
- descripton - The description of the setting

```java
// new SliderSetting(default, min, max, title, description)
SliderSetting sliderSetting = new SliderSetting(5, 1, 10, "SliderSetting", "Example slider.");
```