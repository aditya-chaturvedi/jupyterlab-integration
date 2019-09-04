# Release documentation

## Release process

### 1 Labextension

In case the jupyter labextions has been changed:

1. Commit changes

2. Bump version of *databrickslabs_jupyterlab_statusbar*

    - A new release candidate with rc0

      ```bash
      make bump_ext part=premajor|preminor|prepatch
      ```

    - A new build

      ```bash
      make bump_ext part=prerelease
      ```

    - A new release without release candidate

      ```bash
      make bump_ext version=major.minor.patch
      ```

3. Deploy to npmjs.com

    ```bash
    make upload_ext
    ```

4. Process with **Python package** since labextensions.txt is changed!


### 2 Python package

In case the jupyter labextions and/or the python code has been changed:

1. Run tests

    ```bash
    make tests
    ```

2. Clean environment

    ```bash
    make clean    # delete all temp files
    make prepare  # commit deletions
    ```

3. Commit changes

4. Bump version of databrickslabs_jupyterlab

    - A new release candidate with rc0

      ```bash
      make bump part=major|minor|patch
      ```

    - A new build

      ```bash
      make bump part=build
      ```

    - A new release

      ```bash
      make bump part=release
      ```

    - A new release without release candidate

      ```bash
      make bump part=major|minor|patch version=major.minor.patch
      ```

5. Create distribution

    ```bash
    make dist
    ```

6. Create and tag release

    ```bash
    make release
    ```

7. Deploy to pypi

    ```bash
    make upload
    ```

### 3 Push changes

1. Push repo and tag

    ```bash
    git push --no-verify
    git push origin --no-verify --tags
    ```
