# DTOnboarding

<a href="https://developer.apple.com/swift"><img alt="Swift5" src="https://img.shields.io/badge/language-Swift5-orange.svg"/></a>
<a href="https://swift.org/package-manager"><img alt="Swift Package Manager" src="https://img.shields.io/badge/SwiftPM-compatible-yellowgreen.svg"/></a>
![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/demianturner/dtonboarding?sort=semver)
![GitHub](https://img.shields.io/github/license/demianturner/dtonboarding)
![macOS](https://img.shields.io/badge/macOS-10.12-green.svg)

A macOS onboarding component.

- creates a window containing a configurable number of screens
- use buttons or gestures to navigate
- component size, layout and content easily are configurable

![](https://i.imgur.com/sJb69GE.gif)


## Installation
Install using Swift Package Manager.  Use master branch.

## Dependencies
- [https://github.com/demianturner/DTPageControl](https://github.com/demianturner/DTPageControl)

## Requirements
- OS X 10.12+
- Xcode 11.0 or above

## Demo/Example
Either compile and run the demo from the [example repo](https://github.com/demianturner/OnboardingExample-Mac) or see it used in [Crypto Tools](https://apps.apple.com/gb/app/crypto-tools/id1345035239?mt=12).

## Usage

For this example, ensure 3 pngs exist in the project's asset catalog, in this case `1.png, 2.png, 3.png`

Use the following code in your `AppDelegate.swift` or similar.

```swift
let config = OnboardingConfig(
    windowWidth: 350,
    windowHeight: 430,
    windowTitle: "my sample title",
    pageCount: 3,
    pageControlWidth: 200,
    pageControlHeight: 20,
    pageControlVerticalDistanceFromBottom: 20
)

let pages = [
    DTOnboardingViewController(controllerId: "1"),
    DTOnboardingViewController(controllerId: "2"),
    DTOnboardingViewController(controllerId: "3")
]

let pageController = DTPageController(config: config, pages: pages)
let frame = pageController.view.bounds
let myWindow = NSWindow(
    contentRect: .init(origin: .zero, size: frame.size),
    styleMask: [.closable, .miniaturizable, .resizable, .titled],
    backing: .buffered,
    defer: false
)
myWindow.title = config.windowTitle
myWindow.center()

mainWindowController = NSWindowController(window: myWindow)
mainWindowController?.contentViewController = pageController
```

## License
This software is Open Source under the MIT license, see LICENSE for details.
