![minecraft-hologram](https://socialify.git.ci/VincentZyu233/minecraft-hologram/image?description=1&font=JetBrains+Mono&forks=1&issues=1&language=1&logo=https%3A%2F%2Fassets.streamlinehq.com%2Fimage%2Fprivate%2Fw_300%2Ch_300%2Car_1%2Ff_auto%2Fv1%2Ficons%2Flogos%2Fspigotmc-6n76dhb21bm15t2i8wr3rei.png%2Fspigotmc-feqcixjzc5qm0dm8in5erj.png%3F_a%3DDATAiZAAZAA0&name=1&owner=1&pulls=1&stargazers=1&theme=Light)

> **[📖 English](README.md)**

# 🌍✨🧊🧩 minecraft-hologram

> 🧩 A Spigot/Paper plugin for rendering 3D holograms, globes, meshes, and marching cubes in Minecraft using text displays

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/VincentZyu233/minecraft-hologram)
[![Gitee](https://img.shields.io/badge/Gitee-C71D23?style=for-the-badge&logo=gitee&logoColor=white)](https://gitee.com/vincent-zyu/minecraft-hologram)

[![Paper](https://img.shields.io/badge/Paper-1.21.4-F8C12D?style=for-the-badge&logo=paper&logoColor=white)](https://papermc.io)
[![Spigot](https://img.shields.io/badge/Spigot-1.21.4-ED8106?style=for-the-badge&logo=spigotmc&logoColor=white)](https://www.spigotmc.org/)

[![Kotlin](https://img.shields.io/badge/Kotlin-2.1.20-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org)
[![Maven](https://img.shields.io/badge/Maven-3.x-C71A36?style=for-the-badge&logo=apachemaven&logoColor=white)](https://maven.apache.org)
![Java](https://img.shields.io/badge/Java-8%2B-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)

---

## 🌟 Features

| Feature | Description |
|---------|-------------|
| 🌍 **Globe Hologram** | Interactive 3D Earth globe with rotation, presets, and sound effects |
| 🧊 **Static 3D Models** | Load & display OBJ meshes (Utah Teapot, Suzanne, Mountain Ray) |
| 📈 **3D Grapher** | Real-time mathematical function visualization |
| 🧩 **Marching Cubes** | Volume rendering with configurable isovalue and optimization |
| 🎨 **Custom Textures** | Earth satellite imagery, basketball texture, custom emission maps |

> ⚠️ This plugin is very experimental and untested in multiplayer. Use at your own risk.

### 📺 Video Series

[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/ae_Gns9ZBqY) [Working Globe Hologram in Minecraft](https://youtu.be/ae_Gns9ZBqY)

[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://youtu.be/RnLWLQsh9mw) [3D Meshes with Text Displays in Minecraft](https://youtu.be/RnLWLQsh9mw)

---

## 🗺️ Version Support

| | |
|---|---|
| 🧱 **Server Software** | [![Paper](https://img.shields.io/badge/Paper-1.21.4-F8C12D?style=flat-square&logo=paper&logoColor=white)](https://papermc.io) [![Spigot](https://img.shields.io/badge/Spigot-1.21.4-ED8106?style=flat-square&logo=spigotmc&logoColor=white)](https://getbukkit.org/download/spigot) |
| 🎯 **Minecraft** | **1.21.4** |
| ☕ **Java Runtime** | 21+ (server) / 8+ (compile target) |

---

## 🛠 Tech Stack

| | |
|---|---|
| 🧱 **Server API** | [![Spigot API](https://img.shields.io/badge/Spigot_API_1.21.4-ED8106?style=flat-square&logo=spigotmc&logoColor=white)](https://hub.spigotmc.org/nexus/content/repositories/snapshots/) |
| 📝 **Language** | [![Kotlin](https://img.shields.io/badge/Kotlin-2.1.20-7F52FF?style=flat-square&logo=kotlin&logoColor=white)](https://kotlinlang.org) |
| 🏗 **Build** | [![Maven](https://img.shields.io/badge/Maven_Shade-3.5.2-C71A36?style=flat-square&logo=apachemaven&logoColor=white)](https://maven.apache.org) |

---

## 📦 Installation

1. Download the JAR from the [releases page](https://github.com/VincentZyu233/minecraft-hologram/releases).
2. Set up a [Paper](https://papermc.io/downloads) or [Spigot](https://getbukkit.org/download/spigot) server.
3. Add the JAR to the server `plugins` folder.
4. Restart the server.

### 🚀 Running a Server

```bash
java -Xmx1024M -Xms1024M -jar server.jar nogui
```

> 💡 It is recommended to use the Java runtime bundled with your Minecraft installation to avoid version conflicts.
> In Modrinth, you can find the Java runtime location inside the profile options menu.

---

## ⌨️ Commands

### 🎮 Items
Get control items:
```
items
```

### 🌍 Globe
Summon a globe:
```
summon minecraft:marker ~ ~1 ~-1 {Tags:["globe"],Rotation:[0f,0f]}
```

Remove with transition:
```
tag @e[tag=globe] add globe_close
```

Toggle with sound effects (Run in sequence):
```
tag @n[tag=globe] add globe_close
execute unless entity @e[tag=globe_close] unless entity @e[tag=globe] run summon minecraft:marker ~ ~ ~ {Tags:["globe"],Rotation:[-90f,0f]}
execute as @e[tag=globe] unless entity @s[tag=globe_close] at @s run playsound minecraft:block.beacon.activate block @a ~ ~ ~ 1 1
execute as @e[tag=globe_close] at @s run playsound minecraft:block.beacon.deactivate block @a ~ ~ ~ 1 1
```

Load preset (Autocomplete shows available options):
```
globe_preset <name>
```

Read / set options (Autocomplete shows available options):
```
globe_settings <name>
globe_settings <name> <value>
```

### 🧊 Static Models
```
summon minecraft:marker ~ ~ ~ {Tags:["mountainray"]}
summon minecraft:marker ~ ~ ~ {Tags:["mountainray_juvenile"]}
summon minecraft:marker ~ ~ ~ {Tags:["utah_teapot"]}
summon minecraft:marker ~ ~ ~ {Tags:["suzanne"]}
```

### 📈 3D Grapher
```
summon minecraft:marker ~ ~ ~ {Tags:["3d_grapher"]}
```

### 🧩 Marching Cubes
```
summon minecraft:marker ~ ~ ~ {Tags:["marching_cubes"]}
data modify entity @n[tag=marching_cubes] BukkitValues merge value {"hologram:optimize":true}
data modify entity @n[tag=marching_cubes] BukkitValues merge value {"hologram:render_debug":true}
data modify entity @n[tag=marching_cubes] BukkitValues merge value {"hologram:isovalue":.5f}
```

---

## 🔧 Build

### 📦 Local Build

```bash
mvn package
```

The resulting JAR will be in the `target/` folder.

### 🤖 GitHub Actions CI

[![CI Status](https://img.shields.io/github/actions/workflow/status/VincentZyu233/minecraft-hologram/build.yml?branch=main&style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/VincentZyu233/minecraft-hologram/actions)

Pushing to `main` or `for-*` branches triggers CI when the commit message contains specific keywords:

| Keyword | Action |
|---------|--------|
| `build action` | 🏗 Build and upload artifact |
| `build release` | 🏗 Build + 🚀 Create GitHub Release with changelog |

Example:
```bash
git commit -m "fix: globe rotation bug; build action"
git commit -m "feat: add new preset; build release"
```

PRs to `main` or `for-*` branches always trigger a build.

The CI workflow:
1. 🔍 Parses commit message for `build action` / `build release` keywords
2. 🏗 Builds the plugin with `mvn package` (Java 21, Maven cache)
3. 📤 Uploads the fat JAR as a build artifact
4. 🚀 If `build release`: deletes old release/tag, generates release notes from template (`.github/release_template.md`), and publishes a new GitHub Release with the JAR attached

> ℹ️ For convenience, set up a symlink to auto-copy the JAR to your server's `plugins` folder:
> - **Windows:** `mklink /D newFile.jar originalFile.jar`
> - **Mac/Linux:** `ln -s originalFile.jar newFile.jar`

---

## 🙏 Attribution

| Asset | Source |
|-------|--------|
| 🛰 Satellite images | [NASA Visible Earth](https://visibleearth.nasa.gov/collection/1484/blue-marble-next-generation?page=4) — [Black Marble](https://visibleearth.nasa.gov/images/144898/earth-at-night-black-marble-2016-color-maps) |
| 🏀 Basketball texture | [Robin Wood](https://www.robinwood.com/Catalog/FreeStuff/Textures/TexturePages/BallMaps.html) |
| 🫖 Utah Teapot model | Martin Newell — [Wikipedia](https://en.wikipedia.org/wiki/Utah_teapot) |
| 🐵 Blender Monkey model | [Blender Foundation](https://www.blender.org/) |
| 🧊 Marching Cubes algorithm | [Nihal Jain](https://github.com/nihaljn/marching-cubes) |

Some assets have been modified.

---

## 📄 License

3rd party assets are under their respective licenses.

You may use the plugin and source code for both commercial or non-commercial purposes.

Attribution is appreciated but not due.

Do not resell without making substantial changes.
