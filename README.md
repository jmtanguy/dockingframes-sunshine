# DockingFrames Sunshine

![Java](https://img.shields.io/badge/Java-17%2B-orange?logo=openjdk)
![License](https://img.shields.io/badge/License-LGPL--2.1-blue)
![Version](https://img.shields.io/badge/Version-2.0.0-green)
[![Maven Central](https://img.shields.io/maven-central/v/io.github.jmtanguy/docking-frames-base?logo=apachemaven&label=Maven%20Central)](https://central.sonatype.com/artifact/io.github.jmtanguy/docking-frames-base)


This is a modernized fork of the DockingFrames project, updated to support JDK 17+ and Maven Central deployment.

## What's Changed in This Fork

### 🔧 Technical Updates
- **JDK 17+ Support**: Updated to compile and run with Java 17 and later versions
- **Maven Modernization**:
  - GroupId changed: `org.dockingframes` → `io.github.jmtanguy`
  - Version: `2.0.0`
  - Updated plugins for JDK 17+ compatibility
  - Removed obsolete `tools.jar` dependency (removed in JDK 9+)

### 📦 Active Modules (15 modules - BUILD SUCCESS)
- **Core & Common**:
  - `docking-frames-core` - Basic drag and drop framework
  - `docking-frames-common` - High-level API for fast development
- **Extensions**:
  - `docking-frames-ext-toolbar`
  - `docking-frames-ext-toolbar-common`
  - `docking-frames-ext-css-theme`
  - `docking-frames-ext-glass` - Additional Eclipse theme tabs
- **Demos**:
  - `docking-frames-demo-app-ice` - Demo framework interfaces
  - `docking-frames-demo-chess` - Custom DockStation example
  - `docking-frames-demo-layouts` - Persistent layout storage
  - `docking-frames-demo-notes`
  - `docking-frames-demo-paint`
  - `docking-frames-demo-size-and-color`
  - `docking-frames-demo-tutorial` - Code snippets and examples
  - `docking-frames-ext-toolbar-tutorial`

### ⚠️ Removed Modules
The following modules were removed due to incompatibility with JDK 9+ (use of deprecated Javadoc API):
- `docking-frames-demo-help` - Uses removed `com.sun.javadoc` API
- `docking-frames-demo-app` - Depends on demo-help
- `docking-frames-dist` - Distribution packaging
- `docking-frames-glass-dist` - Glass theme distribution

## Building the Project

### Requirements
- JDK 17 or later (tested with JDK 21)
- Maven 3.6+

### Build Commands
```bash
# Build all modules
mvn clean install

# Build without running tests
mvn clean install -DskipTests

# Build specific module
cd docking-frames-core
mvn clean install
```

## Using in Your Project

### Maven Dependency (Local Repository)
After building, add to your `pom.xml`:

```xml
<dependency>
    <groupId>io.github.jmtanguy</groupId>
    <artifactId>docking-frames-common</artifactId>
    <version>2.0.0</version>
</dependency>
```

For the core module only:
```xml
<dependency>
    <groupId>io.github.jmtanguy</groupId>
    <artifactId>docking-frames-core</artifactId>
    <version>2.0.0</version>
</dependency>
```

---

## Original Project Information

The original versions of this project are published on http://docking-frames.org

To learn how the framework works:

* read the guides
* visit http://forum.byte-welt.net/forumdisplay.php?f=69 if you have any questions
* for non-technical support you can also contact me directly: benjamin_sigg@gmx.ch

Each directory represents an own project:

* **docking-frames-core**: The basic project containing the core drag and drop mechanism. All other projects depend on this one.
* **docking-frames-common**: Project for fast development of applications, a layer to hide the complexity of dockingFrame
* **docking-frames-ext-glass**: An additional set of tabs for the EclipseTheme
* **docking-frames-tutorial**: A set of small code snippets demonstrating aspects of the projects.
* **docking-frames-demo-app-ice**: public interfaces of the demonstration framework
* **docking-frames-demo-app**: demonstration framework
* **docking-frames-demo-help**: a client of the demonstration-framework, shows JavaDoc.
* **docking-frames-demo-notes**: a client of the demonstration-framework, shows some notes
* **docking-frames-demo-chess**: a client of the demonstration-framework, creates a new type of DockStation
* **docking-frames-demo-paint**: a client using the common project
* **docking-frames-demo-size-and-color**: a client using the common project
* **docking-frames-demo-layouts**: a client allowing to play a bit with persistent storage of layouts.

The projects have these dependencies:

    docking-frames-core:
    - no dependencies

    docking-frames-common:
    + docking-frames-core

    docking-frames-ext-glass:
    + docking-frames-core
    + docking-frames-common (optional during runtime)

    docking-frames-tutorial:
    + docking-frames-core
    + docking-frames-common

    docking-frames-demo-app-ice
    + docking-frames-common

    docking-frames-demo-app
    + docking-frames-demo-app-ice
    + docking-frames-core
    + docking-frames-common
    + docking-frames-demo-help
    + docking-frames-demo-notes
    + docking-frames-demo-chess
    + docking-frames-demo-paint
    + docking-frames-demo-size-and-color
    + docking-frames-demo-layouts

    docking-frames-demo-help
    + docking-frames-demo-app-ice
    + docking-frames-core
    + docking-frames-common
    + lib/tools.jar, can be found in the JDK

    docking-frames-demo-notes
    + docking-frames-demo-app-ice
    + docking-frames-core

    docking-frames-demo-chess
    + docking-frames-demo-app-ice
    + docking-frames-core

    docking-frames-demo-paint
    + docking-frames-demo-app-ice
    + docking-frames-core
    + docking-frames-common

    docking-frames-demo-size-and-color
    + docking-frames-demo-app-ice
    + docking-frames-core
    + docking-frames-common

    docking-frames-demo-layouts
    + docking-frames-demo-app-ice
    + docking-frames-core
    + docking-frames-common

## Original Maven Repositories (OUTDATED - For Reference Only)

⚠️ **Note**: These original repositories (`org.dockingframes`) are outdated and not compatible with JDK 9+. Use this fork instead with `io.github.jmtanguy` groupId.

<details>
<summary>Click to view original Maven repository information</summary>

### Maven Snapshot Repository (outdated version)

The original project snapshot:
https://oss.sonatype.org/content/repositories/snapshots/org/dockingframes/

Original pom.xml configuration:

```xml
<repositories>
    <repository>
        <id>sonatype-oss-snapshots</id>
        <name>Sonatype OSS Maven Repository for Staging Snapshots</name>
        <url>https://oss.sonatype.org/content/repositories/snapshots</url>
        <releases>
            <enabled>false</enabled>
        </releases>
        <snapshots>
            <enabled>true</enabled>
        </snapshots>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>org.dockingframes</groupId>
        <artifactId>docking-frames-common</artifactId>
        <version>1.1.2-SNAPSHOT</version>
    </dependency>
</dependencies>
```

### Maven Release Repository (outdated version)

Original stable release from maven central:
http://search.maven.org/#artifactdetails|org.dockingframes|docking-frames-common|1.1.1|jar

Original pom.xml configuration:

```xml
<dependencies>
    <dependency>
        <groupId>org.dockingframes</groupId>
        <artifactId>docking-frames-common</artifactId>
        <version>1.1.1</version>
    </dependency>
</dependencies>
```

</details>

