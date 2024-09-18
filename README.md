# Swift installation action

Supported runners:

- macOS
- Linux

If the action completes successfully, it sets the environment variable `SWIFT_INSTALLATION` to the path to the toolchain resources. This is the directory that would normally be named `usr` in a Swift installation.

### Configuration

Other GitHub actions that install the Swift toolchain tend to suffer from deployment lag when new versions of Swift are released. This action is designed to be more flexible and to allow installing toolchains by speculatively building a URL.

The action requires two inputs, `swift-prefix` and `swift-id`. Their values should be destructured from the URL of the Swift toolchain download like this:

#### macOS

```bash
'https://download.swift.org/' swift-prefix '/' swift-id '-osx.pkg'
```

#### Linux (all distributions)

```bash
'https://download.swift.org/' swift-prefix '/' swift-id '.tar.gz'
```


## Usage examples

### Ubuntu 24.04 with Swift 6.0

```yaml
linux:
    runs-on: ubuntu-24.04
    name: Ubuntu 24.04

    steps:
        -   name: Install Swift
            uses: tayloraswift/swift-install-action@master
            with:
                swift-prefix: "swift-6.0-release/ubuntu2404/swift-6.0-RELEASE"
                swift-id: "swift-6.0-RELEASE-ubuntu24.04"

        -   name: Check Swift
            run: swift --version
```

### macOS with Swift 6.0

```yaml
macos:
    runs-on: macos-14
    name: macOS

    steps:
        -   name: Install Swift
            uses: tayloraswift/swift-install-action@master
            with:
                swift-prefix: "swift-6.0-release/xcode/swift-6.0-RELEASE"
                swift-id: "swift-6.0-RELEASE"

        -   name: Check Swift
            run: swift --version
```

Please note, on macOS, the `swift-id` does not include a distribution name.
