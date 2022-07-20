# publish-gradle

Builds and publishes versioned build artifacts for a gradle project.

Uses the [`reckon` plugin](https://github.com/ajoberstar/reckon) to determine version.

## Usage

```yaml
steps:
  - name: publish-gradle
    uses: kkorolyov/publish-gradle@0.3.0
    with:
      java-version: ${{ matrix.version }}
      token: ${{ secrets.GITHUB_TOKEN }}
```

When `publish-task` is run, also outputs the `version` reckoned, to optionally use in subsequent workflow steps.

## Customization

By default, simply builds the project.

If the last commit message contains any of the terms `[MAJOR, BREAKING]`, a major version is published.  
If the last commit message contains any of the terms `[MINOR]`, a minor version is published.  
If the last commit message contains any of the terms `[PATCH, HOTFIX]`, a patch version is published.

### List of action options:

| Input             | Usage                                                                                                                            | Default |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------- |
| java-version      | Java version to run against                                                                                                      |         |
| java-distribution | Java distribution to run against ([more options](https://github.com/actions/setup-java#supported-distributions))                 | temurin |
| build-task        | Basic build task                                                                                                                 | build   |
| publish-task      | Artifact publishing task                                                                                                         | publish |
| publish-branch    | If set, name of distinct branch on which 'publish-task' can run. Execution from other branches / PRs will only run 'build-task'. |         |
| token             | Token for Github maven repository read/write                                                                                     |         |
