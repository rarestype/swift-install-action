# Swift installation action

Supported runners:

- macOS
- Linux


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
