# Items API
Tungsten Client provides an items API that allows creative mode players to spawn in items with custom NBT data.

Currently, this is the only approach to creating an item:
```java
class SomeItem extends GenericItem {
    public SomeItem() {
        super(new ItemStack(Items.IRON_INGOT, 1), "{display:'Name:{\"text\":\"Tungsten Ingot\"}'}"); // super(itemstack, nbt)
    }
}
```
We recommend that you use something like [MCStacker](https://mcstacker.net) to create NBT strings.

Items are registered via `ItemRegistry.addItem(new SomeItem())` during module initialization phase (**not** onEnable).