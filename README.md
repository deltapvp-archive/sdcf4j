# sdcf4j <a href="#"><img src="https://img.shields.io/badge/version-1.1.0-brightgreen" alt="Latest version"></a> <a href="http://ci.ketrwu.de/job/sdcf4j/job/master/javadoc/"><img src="https://shields.javacord.org/badge/JavaDoc-latest-yellow.svg" alt="Latest JavaDocs"></a> <a href="https://github.com/BtoBastian/sdcf4j/wiki"><img src="https://shields.javacord.org/badge/Wiki-Home-red.svg" alt="Latest JavaDocs"></a>

Sdcf4j is a **s**imple **D**iscord **c**ommand **f**ramework **for** **J**ava, supporting [Javacord](https://github.com/BtoBastian/Javacord), [JDA](https://github.com/DV8FromTheWorld/JDA) and [Discord4J](https://github.com/austinv11/Discord4J). It helps you creating commands within seconds in a clean and simple way.

A ping command is as easy as this:
```java
@Command(aliases = "ping", description = "Pong!")
public String onPingCommand() {
    return "Pong!";
}
```

##  Maven
```xml
<repository>
  <id>deltapvp</id>
  <url>https://repo.deltapvp.net/</url>
</repository>
...
<!-- The core module -->
<dependency>
  <groupId>me.powercasgamer.sdcf4j</groupId>
  <artifactId>sdcf4j-core</artifactId>
  <version>%version%</version>
</dependency>
<!-- The module for your preferred lib -->
<dependency>
  <groupId>me.powercasgamer.sdcf4j</groupId>
  <!-- Possible artifact ids: sdcf4j-javacord, sdcf4j-jda3, sdcf4j-jda4, sdcf4j-discord4j -->
  <artifactId>sdcf4j-jda4</artifactId>
  <version>%version%</version>
</dependency>
```
Make sure to replace `%version%` with the latest version number, e.g. `v1.0.0` (don't use this one!).

Latest version: <a href="#"><img src="https://img.shields.io/badge/version-1.1.0-brightgreen" alt="Latest version"></a>
## Support
 
* [JavaCord server](https://discord.gg/0qJ2jjyneLEgG7y3)
* [DiscordAPI #java_javacord channel](https://discord.gg/0SBTUU1wZTVXVKEo)

You can find me in one of these servers/channels. Feel free to contact me if you need help. :)

## Javadocs
The javadocs can be found here: [JavaDocs](http://ci.ketrwu.de/job/sdcf4j/job/master/javadoc/)

Thanks to ketrwu, too.

## Tutorial

Take a look at the [wiki](https://github.com/BtoBastian/sdcf4j/wiki) for a detailed description on how to use the library.

## Examples

Ping command:
```java
public class PingCommand implements CommandExecutor {

    @Command(aliases = {"!ping"}, description = "Pong!")
    public String onCommand(String command, String[] args) {
        return "Pong!";
    }

}
```

Parameters are completely dynamic, so all of this examples would work:
```java
// no parameters (Javacord, JDA and Discord4J)
@Command(aliases = {"!ping"}, description = "Pong!")
public String onCommand() {
    return "Pong!";
}

// DiscordAPI and Message as parameter (Javacord)
@Command(aliases = {"!ping"}, description = "Pong!")
public String onCommand(DiscordApi api, Message message) {
    return "Pong!";
}

// no private messages and async (Javacord and JDA)
@Command(aliases = {"!channelInfo", "!ci"}, description = "Pong!", async = true, privateMessages = false)
public String onCommand(Channel channel) {
    return "You are in channel #" + channel.getName() + " with id " + channel.getId();
}
```

## Register a CommandExecutor

```java
// Javacord
CommandHandler cmdHandler = new JavacordHandler(api);
// JDA3
CommandHandler cmdHandler = new JDA3Handler(jda);
// JDA4
CommandHandler cmdHandler = new JDA4Handler(jda);
// Discord4J
CommandHandler cmdHandler = new Discord4JHandler(client);

// register the command
cmdHandler.registerCommand(new PingCommand());
```
