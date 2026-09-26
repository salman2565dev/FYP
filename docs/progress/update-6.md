## Progress Update — 26 September 2025

### Maven Deep Dive

Continued my exploration of Maven today. Understood the core concepts, file structure, and execution model.

### Topics Covered

**1. Maven Structure & Terminology**
- Understood the file hierarchy (POM, settings.xml, local repository)
- Learned the difference between pom.xml (project-specific) and settings.xml (machine-specific)

**2. pom.xml Structure**
- GAV coordinates (groupId, artifactId, version)
- Parent inheritance
- Properties, dependencies, build, profiles
- distributionManagement for deploy targets

**3. Dependencies vs. Dependency Management**
- `<dependencies>` — libraries actually used (downloaded and added to classpath)
- `<dependencyManagement>` — version control rules (nothing downloaded directly)

**4. Plugins vs. Plugin Management**
- `<plugins>` — plugins actually executed
- `<pluginManagement>` — plugin version and configuration rules

**5. Dependency Scopes**
- `compile` (default, always available)
- `provided` (from runtime environment)
- `runtime` (not needed at compile time)
- `test` (only during testing)

- <img width="1296" height="617" alt="image" src="https://github.com/user-attachments/assets/dcbc8848-daa9-450f-8acd-e03df1187e37" />


**6. Maven Build Lifecycles**
- `default` — the main build lifecycle (23 phases: validate → compile → test → package → install → deploy)
- `clean` — removes previous build output
- `site` — generates project documentation

- <img width="1427" height="678" alt="image" src="https://github.com/user-attachments/assets/76f2cfa0-1853-4eb7-89ad-33b948c8c3c5" />


**7. Local vs. Remote Repositories**
- Local: `~/.m2/repository`
- Remote: Maven Central, company Nexus/Artifactory, vendor repos
- Understood the resolution order: local → mirror → declared remotes → Central

- <img width="1300" height="567" alt="image" src="https://github.com/user-attachments/assets/38461952-925e-40de-bc83-b8ecad386d54" />


**8. Mirrors**
- A mirror caches dependencies for faster builds
- Tools: Nexus, JFrog Artifactory, AWS CodeArtifact, Google Artifact Registry
- `mirrorOf="*"` forces all traffic through the mirror

- <img width="1302" height="757" alt="image" src="https://github.com/user-attachments/assets/f1fd0dc0-43d2-4343-9909-d54f1271849a" />


**9. Resolve vs. Deploy**
- **Resolve (download)**: fetches dependencies from remotes to local cache
- **Deploy (upload)**: publishes built artifacts from local to remote repo
- Understood the two-way flow and how IDs must match between pom.xml and settings.xml

**10. settings.xml vs. pom.xml**
- **pom.xml**: project-specific (dependencies, plugins, build config)
- **settings.xml**: machine-specific (mirrors, servers, proxies, credentials)

### Next Target
- Explore the **Super POM** — the built-in parent that all POMs inherit from
- Understand Maven's default inheritance hierarchy
- Learn how effective POMs are computed
