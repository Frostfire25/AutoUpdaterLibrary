# AutoUpdaterLibrary

### Information
AutoUpdaterLibrary is a Library utilizing the Java Workservice to run methods inside of your JavaPlugin
based on the updating state of files in the config directly.

### Usage
Add folder into project-structure and optionally replace Config.class for your
YMAL Builder.
Inside your JavaProject initilize the following 
```
public class Main extends JavaPlugin implements WSClass {

    @Getter
    private static Main instance;

    @Getter
    private WSM WSM;

    @Override
    public void onEnable() {
        instance = this;
        WSM = new WSM(this, this, true);
    }

    @Override
    public void onDisable() {
        WSM.disableLoop();
    }

    @Override
    public void updateConfig() {
        //Put what you'd like here to manage objects
        //The following reloads the plugin and works
        //In most cases
        reloadConfig();
        //If you have other Config.class files you can optionally reload them
        Bukkit.getPluginManager().disablePlugin(this);
        Bukkit.getPluginManager().enablePlugin(this);
    }

}
```
