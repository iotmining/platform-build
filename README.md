# IoTMining Build (BOM + Parent)

Central **BOM** and **Parent POM** for all IoTMining services, published to **GitHub Packages (Maven)**.

## Modules
- `bom/` → `com.iotmining.build:iotmining-bom:2025.08.16`
- `parent/` → `com.iotmining.build:iotmining-parent:2025.08.16`

## How to Release
1. Push a tag: `git tag v2025.08.16 && git push --tags`
2. Workflow `release-publish` sets versions and deploys to GitHub Packages.

## Snapshots
- Push to `main` → `snapshot-publish` deploys `*-SNAPSHOT`.

## Consume in a Service
```xml
<parent>
  <groupId>com.iotmining.build</groupId>
  <artifactId>iotmining-parent</artifactId>
  <version>2025.08.16</version>
</parent>

<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>com.iotmining.build</groupId>
      <artifactId>iotmining-bom</artifactId>
      <version>2025.08.16</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
```
Dev machine ~/.m2/settings.xml (for local mvn deploy if needed)
```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0">
  <servers>
    <server>
      <id>github</id>
      <username>${env.GH_ACTOR}</username>
      <password>${env.GH_TOKEN}</password>
    </server>
  </servers>
</settings>

```

Export env vars:
```cql
export GH_ACTOR=<your-gh-username>
export GH_TOKEN=<PAT with write:packages>

```

## GitHub Required Setting

Repo → Settings → Actions → General → Workflow permissions → Read and write permissions.

```cql

---

That’s everything you need. Drop these files into a repo like `iotmining/iotmining-build`.  
- Push to `main` ⇒ **SNAPSHOTs** publish.  
- Tag `v2025.08.16` ⇒ **Release** publishes.  

If you want, I can also add **GPG signing**, **SBOM attestation**, or a **version matrix** job.

```