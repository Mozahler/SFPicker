## A Segmented Controller in SwiftUI

This sounds like a fun project to me, let me know what you think

[link to the issues page of the site](https://github.com/Mozahler/SFPicker/issues)

## SFSymbols

SFSymbols have been around for 3 generations and the symbols number in the thousands.

>With over 3,100 symbols, SF Symbols is a library of iconography designed to integrate seamlessly with San Francisco, the system font for Apple platforms. Symbols come in nine weights and three scales, and automatically align with text labels. They can be exported and edited in vector graphics editing tools to create custom symbols with shared design characteristics and accessibility features. SF Symbols 3 features over 600 new symbols, enhanced color customization, a new inspector, and improved support for custom symbols. -- <https://developer.apple.com/sf-symbols/>

## A Graphic Interface For User Choice
When I'm working with a form (for me this typically means a screen interface to a database object) I'm often faced with the problem of how do I give the user multiple choices without it taken the whole screen to do so. For the past couple of years I've been using a hand-rolled SwiftUI View based on a UIKit multisegment controller:

[MultiSelectSegmentedControl](https://github.com/yonat/MultiSelectSegmentedControl)

### Pictures Instead of Words
I'm a big fan of pictures over words on the phone screen, so instead of the traditional text labels, I have been using emoji as images for the segment content. `A picture's worth a thousand words`, and all that... 

But I've never been particularly happy about it. Emojis are fun, but in general they are informal, and a bit casual for my ususal purposes. With the advent of the third release of SFSymbols, I'm ready to take the plunge and design my own picker that piggybacks on Apple's hard work. A picker which uses SFSymbols instead of text labels or any other types of images.

In order to accomplish this I will be using a package published by Patrick Stein (Jolly) at:

[SFSymbolEnum](https://github.com/jollyjinx/SFSymbolEnum)  

**A swift package providingSF Symbols as via an enum instead of using  verbatim strings.**

He mentions the primary benefits of his package in the Readme:

* Compiler error when you mistype a SFSymbol name
* Autocompletion and suggestion for all SFSymbols

### When In Doubt, There's Autocompletion!
The `SFSymbolEnum` package makes our lives easier by making the compiler check the validity of the symbol names at build-, rather than run- time. If you've ever waited through a long compile time only to have your app blow up at launch, you will appreciate this statement. It's also great to have autocompletion show you the list when you type the inital dot/period/full stop.

## Swift Composable Architecture

The other package I will use is a workhorse.  Using the principles of functional programming to build a programing environment that is easy to test, the guys at PointFree have been supporting this package (which they OpenSourced) for a while now:

[Swift Composable Architecture on GitHub](https://github.com/pointfreeco/swift-composable-architecture)

## A Gentle Introduction to TCA
In my introductory tutorials, which includes this one, I will not spend a lot of time explaining the philosophies behind TCA. I would like you to see it in action, and get comfortable with having it around.  When the time is right I can start a deep-dive into why it works. But for now I just want you to see and recognize the patterns:

* We create a Store (a struct) that tracks everything
* We pass the store on to other parts of the app, as it should be in charge of the functionality of the app 
* The store has access to a `State` object, a set of `actions` (represented by an enum), an `environment` (a struct for executing side effects like API calls to remote sites) and a `reducer` (a pure function responsible for executing actions that update the `state`
* Any time you wish to add functionality to the app you will add an action case to the `Action` enum, and the compile will remind you that you also have to add a case to your reducer (which switches over all cases of the `Action` enum). The new functionality is handled in this case statement in the reducer, or a call is made to the `environment` or `state` for further processing.

## Time to Get Your Feet Wet
I feel like I've presented a lot on this page, and it's time for you to start getting familiar with how everything fits together. Take a few minutes to load Version 0.1 of the Swift Package.

Here's what you need to do to get things running:
In Xcode you should `add a package` [package name], and make sure you specify the `exact` version of 0.1 to get the simplest, most basic version available.
In your ContentView.swift file you should:

.bb[make sure to import the package `import PackageName`
[copy and paste the ContentView.swift file here]
]

Thats it!!

Run the code, modify the code, make it better, make it fail (and pay attention to the error messages, so that in the future you can recognize what may have caused them to show up again).

## Summary
In this unit I have:

* Introduced SF Symbols
* Introduced Swift Composable Architecture (TCA)
* Introduced SFSymbolEnum
* Touched on one aspect of programming with the Combine Framework
* Provided a working version of the code we will be tackling in the next unit
* Explained how to integrate the package with your Xcode project.


I am going to tackle this job in phases:

* A selection bar you send the array of images you want included - allows a single selection only
* Add closures instead of hard-coding the class in the reducer based on an index tapped
* Allows multiple selection - good to use to filter data, or perform a search on a union of selected segment indexes

.pct 85

