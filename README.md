# SimplexClient API

### Gradle:
````gradle
repositories {
    maven {
        url = "http://tykopvp.com/"
        allowInsecureProtocol(true)
    }
}

dependencies {
    compileOnly("tk.simplexclient:api:1.0")
}
````
### Maven:
````xml
<repositories>
    <repository>
        <id>coins</id>
        <url>http://tykopvp.com/</url>
    </repository>
</repositories>
<dependencies>
    <dependency>
        <groupId>tk.simplexclient</groupId>
        <artifactId>api</artifactId>
        <version>1.0</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
````
### How to use it:

first you need to create a plugin.json file in the resources folder

If you have you .jar file then you need to press Windows+R type %appdata% and go into the folder .simplex\simplex\Mods folder thenn add you .jar file in it!

plugin.json content:
````json
{
  "main": "me.cutenyami.simplex.SimplexTestPlugin",
  "name": "SimplexTest Plugin",
  "version": "1.0"
}
````
SimplexTestPlugin.java content:
````java 
public class SimplexTestPlugin extends Plugin {

    @Override
    public void onEnable() {
        System.out.println("Plugin is now enabled!");
    }

    @Override
    public void onDisable() {
        System.out.println("Plugin is now disabled!");
    }
}
````
### Example with KeyBindings:
````java
public class SimplexTestPlugin extends Plugin {

    private final KeyBinding keyBinding = new KeyBinding("Test Keybinding", Keyboard.KEY_U, "SimplexClient");
    private final Minecraft mc = Minecraft.getMinecraft();

    @Override
    public void onEnable() {
        SimplexClient.getInstance().getSimplexAPI().getSimplexKeybindings().registerKeyBinding(keyBinding);
        EventManager.register(this);
    }

    @EventTarget
    public void onTick(ClientTickEvent event) {
        if (keyBinding.isPressed()) {
            mc.thePlayer.sendChatMessage("This is a Message!");
        }
    }

    @Override
    public void onDisable() {
        EventManager.unregister(this);
    }

    public Minecraft getMc() {
        return mc;
    }
}
````
If you need help the join our Discord Server: https://simplexclient.tk/discord
