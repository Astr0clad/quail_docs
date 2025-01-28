---
label: Installation
order: 0
icon: download
---

# Installation

## Via Jitpack

### Into an Existing Project

+++ 🐘 Gradle

1. Add JitPack to your build file

```gradle
repositories {
    maven { url 'https://jitpack.io' }
}
```

2. Add the dependency

```gradle
dependencies {
    implementation 'com.github.mineinjava:quail:v1.0.0-RC-1'
}
```

+++ 🪶 Maven

1. Add JitPack to your build file

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
```

2. Add the dependency

```xml
<dependency>
    <groupId>com.github.mineinjava</groupId>
    <artifactId>quail</artifactId>
    <version>v0.2.1-a</version>
</dependency>
```

+++ ❓ Other
Figure it out yourself

[Here is the jitpack link](https://jitpack.io/#mineinjava/quail)
+++


## Via git submodule
This is recommended teams that wish to contribute to Quail, or if the methods above don't work for you.

1. Add the submodule

```bash
git submodule add https://github.com/Mineinjava/quail.git repositories/quail
```

- This will clone a copy of Quail into your project at `repositories/quail`.

2.  Symlink the Quail module into your project

On Windows:

```cmd
 cd src\main\java\com\mineinjava
 mklink /D quail ..\..\..\..\..\repositories\quail\quail\src\main\java\com\mineinjava\quail
```

You may have to make directories.

- This will create a symlink to the Quail module in your project.

To update the module:
```bash
 cd repositories/quail
 git pull
```

## FTC Quickstart

coming soon™
