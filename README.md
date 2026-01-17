# Code Format

A collection of opinionated code formatting configurations for Java development tools.

## Releases

Current release `1.0.0`

## Contents

- `java-code-style.xml`: Eclipse formatter configuration file with the `modern-java` profile.

## Supported Tools

- **Spotless**: A code formatting plugin for Gradle and Maven.
- **Eclipse**: An integrated development environment widely used for Java development.
- **IntelliJ IDEA**: A popular Java IDE with built-in code formatting capabilities.

See below for installation instructions.

## Installation

### Direct File Usage
```bash
# Download the Eclipse formatter configuration
curl -o java-code-style.xml \
  https://raw.githubusercontent.com/raduking/code-format/refs/heads/master/src/main/resources/java-code-style.xml
```

This file can be imported directly into Eclipse or IntelliJ IDEA.

Eclipse:
1. Go to `Settings` > `Java` > `Code Style` > `Formatter`.
2. Click `Import...` and select the downloaded `java-code-style.xml` file.
3. Select the imported profile: `modern-java`.
3. Optionally, set it as the default formatter.
4. Apply the changes.

IntelliJ IDEA:
1. Go to `Settings` > `Editor` > `Code Style` > `Java`.
2. Click on the gear icon and select `Import Scheme` > `Eclipse XML Profile`.
3. Select the downloaded `java-code-style.xml` file.
4. Select the imported scheme `modern-java`.
4. Apply the changes.

### Maven

```xml
<dependency>
    <groupId>io.github.raduking</groupId>
    <artifactId>code-format</artifactId>
    <version>1.0.0</version>
</dependency>
```

### Spotless Maven Plugin Configuration

```xml
<properties>
    <spotless.maven.plugin.version>3.1.0</spotless.maven.plugin.version>
    <org.eclipse.jdt.core.version>3.44.0</org.eclipse.jdt.core.version>
    <eclipse.formatter.version>4.38</eclipse.formatter.version>
    <code.format.version>1.0.0</code.format.version>
</properties>

<plugins>
    <!-- ... other plugins ... -->
    <plugin>
        <groupId>com.diffplug.spotless</groupId>
        <artifactId>spotless-maven-plugin</artifactId>
        <version>${spotless.maven.plugin.version}</version>
        <dependencies>
            <dependency>
                <groupId>org.eclipse.jdt</groupId>
                <artifactId>org.eclipse.jdt.core</artifactId>
                <version>${org.eclipse.jdt.core.version}</version>
            </dependency>
            <dependency>
                <groupId>io.github.raduking</groupId>
                <artifactId>code-format</artifactId>
                <version>${code.format.version}</version>
            </dependency>
        </dependencies>
        <configuration>
            <java>
                <eclipse>
                    <file>java-code-style.xml</file>
                    <version>${eclipse.formatter.version}</version>
                </eclipse>
                <removeUnusedImports/>
                <trimTrailingWhitespace/>
            </java>
        </configuration>
        <executions>
            <execution>
                <phase>compile</phase>
                <goals>
                    <goal>apply</goal>
                </goals>
            </execution>
        </executions>
    </plugin>
</plugins>
```