# tile-kotlin-compile

Maven tile for Kotlin compile. It defaults to use src/main/java and src/test/java but you can configure that and the Kotlin version to use.

## Example use

```xml
      <!-- In maven build / plugins -->

      <plugin>
        <groupId>io.repaint.maven</groupId>
        <artifactId>tiles-maven-plugin</artifactId>
        <version>2.8</version>
        <extensions>true</extensions>
        <configuration>
          <tiles>
            <tile>org.avaje.tile:java-compile:1.1</tile>
            <tile>org.avaje.tile:kotlin-compile:1.1</tile>
            <tile>org.avaje.tile:ebean-enhancement:1.1</tile>
          </tiles>
        </configuration>
      </plugin>

```

## What it does

Effectively the kotlin-compile tile brings in the *kotlin-maven-plugin* with configuration for compiling *main* and *test* code.

```xml

  <!-- defaults, override in your project pom if needed -->

  <properties>
    <kotlin.version>1.0.0</kotlin.version>
    <kotlin.plugin.main.source>src/main/java</kotlin.plugin.main.source>
    <kotlin.plugin.test.source>src/test/java</kotlin.plugin.test.source>
  </properties>

  <!-- brought into build / plugins -->

  <build>
    <plugins>

      <plugin>
        <groupId>org.jetbrains.kotlin</groupId>
        <artifactId>kotlin-maven-plugin</artifactId>
        <version>${kotlin.version}</version>
        <executions>
          <execution>
            <id>compile</id>
            <phase>process-sources</phase>
            <goals>
              <goal>compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <source>${kotlin.plugin.main.source}</source>
              </sourceDirs>
            </configuration>
          </execution>
          <execution>
            <id>test-compile</id>
            <phase>test-compile</phase>
            <goals>
              <goal>test-compile</goal>
            </goals>
            <configuration>
              <sourceDirs>
                <source>${kotlin.plugin.test.source}</source>
              </sourceDirs>
            </configuration>
          </execution>
        </executions>
      </plugin>

    </plugins>

  </build>

```
