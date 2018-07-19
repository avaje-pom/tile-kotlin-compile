# kotlin-compile maven tile

Maven tile for performing Kotlin compile. It defaults to use src/main/java and src/test/java but you can configure that and the Kotlin version to use.

## Example use

In your project pom under build / plugins add the tiles-maven-plugin with the following configuration. Note that the java-compile tile is there if your project also uses Java.

```xml
      <!-- maven build / plugins -->

      <plugin>
        <groupId>io.repaint.maven</groupId>
        <artifactId>tiles-maven-plugin</artifactId>
        <version>2.11</version>
        <extensions>true</extensions>
        <configuration>
          <tiles>
            <tile>org.avaje.tile:kotlin:1.1</tile>
          </tiles>
        </configuration>
      </plugin>

```

## What it does

Effectively the kotlin-compile tile brings in the *kotlin-maven-plugin* with configuration for compiling *main* and *test* code.

```xml

  <!-- defaults, override in your project pom if needed -->

  <properties>
    <kotlin.version>1.2.51</kotlin.version>
    <kotlin.compiler.jvmTarget>1.8</kotlin.compiler.jvmTarget>
  </properties>
  
  <!-- brought into build / plugins -->

  <build>

    <sourceDirectory>src/main/kotlin</sourceDirectory>
    <testSourceDirectory>src/test/kotlin</testSourceDirectory>

    <plugins>
      <plugin>
        <groupId>org.jetbrains.kotlin</groupId>
        <artifactId>kotlin-maven-plugin</artifactId>
        <version>${kotlin.version}</version>
        <executions>
          <execution>
            <id>compile</id>
            <phase>compile</phase>
            <goals>
              <goal>compile</goal>
            </goals>
            <configuration>
              <jvmTarget>${kotlin.compiler.jvmTarget}</jvmTarget>
            </configuration>
          </execution>
          <execution>
            <id>test-compile</id>
            <phase>test-compile</phase>
            <goals>
              <goal>test-compile</goal>
            </goals>
            <configuration>
              <jvmTarget>${kotlin.compiler.jvmTarget}</jvmTarget>
            </configuration>
          </execution>
        </executions>
      </plugin>

    </plugins>

  </build>

```
