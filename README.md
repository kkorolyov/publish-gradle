# publish-gradle

Publishes versioned build artifacts and documentation for a gradle project.

The project's packaging task is invoked to build (and potentially push) artifacts using the [`reckon`](https://github.com/ajoberstar/reckon) plugin for versioning.

The project's documentation task is invoked to generate documentation that is then pushed to Github Pages.

## Usage

```yaml
steps:
  - name: publish-gradle
    uses: kkorolyov/publish-gradle@0.2.0
    with:
      java-version: ${{ matrix.version }}
      token: ${{ secrets.GITHUB_TOKEN }}
```

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
| package-task      | Artifact generation task                                                    | publish              |
| docs-task         | Documentation generation task                                               | javadoc              |
| docs-dir          | Documentation output directory                                              | ./build/docs/javadoc |
| token             | Token for Github maven repository read/write and pushing to gh-pages branch |                      |
