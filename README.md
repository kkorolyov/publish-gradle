# publish-gradle

Publishes versioned build artifacts and documentation for a gradle project.

The project's [`publish`](https://docs.gradle.org/current/userguide/publishing_maven.html) task is invoked to build and push artifacts using the [`reckon`](https://github.com/ajoberstar/reckon) plugin for versioning.

## Customization

By default, a minor version is tagged and released.

If the last commit message contains any of the terms `[MAJOR, BREAKING]`, a major version is released.

If the last commit message contains any of the terms `[PATCH, HOTFIX]`, a patch version is released.

If the last commit message contains any of the terms `[NOCHANGE]`, no version is released.

Documentation from the project's documentation task is pushed to Github Pages.

| Input             | Usage                                                                       | Default              |
| ----------------- | --------------------------------------------------------------------------- | -------------------- |
| java-version      | Java version to run against                                                 |                      |
| java-distribution | Java distribution to run against                                            | zulu                 |
| docs-task         | Documentation generation task                                               | javadoc              |
| docs-dir          | Documentation output directory                                              | ./build/docs/javadoc |
| token             | Token for Github maven repository read/write and pushing to gh-pages branch |                      |
