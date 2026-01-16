# Code Format

A collection of opinionated code formatting configurations for Java development tools.

## Releases

Current release `1.0.24`

## Supported Tools

- **Spotless**: A code formatting plugin for Gradle and Maven.

## Installation

### Direct File Usage
```bash
# Download the Eclipse formatter configuration
curl -o formatter.xml \
  https://raw.githubusercontent.com/raduking/code-format/main/src/main/resources/java-code-style.xml
```

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