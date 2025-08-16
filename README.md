# IoTMining Platform Build (Parent + BOM)

This repo provides the **centralized build policy** and **version policy** for all IoTMining services.

- **`iotmining-bom`**: pins dependency versions (Spring Boot/Cloud, Testcontainers, Jackson, etc.)
- **`iotmining-parent`**: centralizes pluginManagement, quality/security gates, CI profiles.

## Versions
- Java: 21
- Boot: 3.4.4
- Cloud: 2024.0.3
- Platform line: `2025.08.x` (stable)

## How services use it

In each service `pom.xml`:
```xml
<parent>
  <groupId>com.iotmining.build</groupId>
  <artifactId>iotmining-parent</artifactId>
  <version>2025.08.1</version>
  <relativePath/>
</parent>
