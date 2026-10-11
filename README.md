# VinTPChest — Fabric client mod source

Target: Minecraft Java 1.21.11, Fabric Loader 0.18.4, Java 21.

## What it does
- Press **P** to open a black/red GUI.
- Search field sends a configurable server command.
- Refresh button sends a configurable server command.
- It does **not** scan hidden storage, bypass permissions, spoof server data, or teleport the client on its own.
- It is a client-side command GUI, not a hack; it uses the normal Minecraft chat-command channel.
- **It cannot be supported by every server automatically.** Each server must already provide a chest/shulker teleport or search command and allow the player to use it. Servers with no such command will not gain this feature from the mod.

## Important: configure commands first
The included command names are examples, not universal Minecraft commands. Ask the server staff which command is supported, then edit:
`config/vintpchest.properties`

Example:
```properties
searchCommand=chesttp {query}
refreshCommand=chesttp list
```

Replace these with the *actual* commands your server supports. `{query}` is replaced with the text entered in the GUI. If the server has no chest-teleport command/plugin, this GUI cannot create that capability.

## Build the mod JAR
Requires a computer or a cloud IDE with JDK 21 and internet access for Gradle dependencies.

If Gradle is installed in the build environment:
```sh
gradle build
```

This ZIP does not include the Gradle Wrapper scripts/JAR, so `./gradlew build` will not work until you generate/add the wrapper first.

Output:
`build/libs/vintpchest-1.0.0.jar`

The `-sources.jar` is not the playable mod; use the normal `.jar`.

## Building from an Android phone
An APK is **not** the right output: Minecraft Java mods are `.jar` files, not Android APKs.
On Android, use a browser-based cloud IDE that supports Java 21 + Gradle (for example, a GitHub Codespace if available to your account), upload/import this project, ensure JDK 21 and Gradle are available, then run `gradle build`. Download the resulting `build/libs/vintpchest-1.0.0.jar` and put it in the `mods` folder used by your Fabric/PojavLauncher instance. Keep Fabric API installed too. Building happens in the cloud environment; the phone does not need to compile Minecraft itself.

## Version/dependency note
The Minecraft/Fabric ecosystem updates frequently. If Gradle says a Loom, Yarn mapping, or Fabric API version cannot be found, use versions published for Minecraft 1.21.11. This source project has not been compiled in this environment, so treat it as a starter source project and verify it with a build before installing.
