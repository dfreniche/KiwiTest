# Using Kiwi 2.3 with Xcode 5 on OS X 10.8.5

I've run into troubles using Kiwi with Xcode 5. I launched the tests, got no errors, but no tests were running (0 tests running)

The problem is described [here](https://github.com/allending/Kiwi/pull/366)

TL;DR; :Xcode 5 uses Xctest unit testing instead of OCUnit (SenTesting kit framework). To get Kiwi working you need to use the "version" of Kiwi that uses Xctest. Instead of having multiple Kiwi versions, the smart guys behind it give us some git subrepositories. You need to select the right Kiwi subrepo. To do that, I'm using Cocoapods with this podfile:


    platform :ios, '6.0'

    xcodeproj 'KiwiTest/KiwiTest.xcodeproj'

    target :KiwiTestTests, :exclusive => true do
        pod 'Kiwi/XCTest'
    end

As you can see, a regular podfile but the trick is the Kiwi/XCTest part :-D 

To use this, you need to [setup Cocoapods](http://cocoapods.org)

---

## My environment

- Xcode 5 build 5A1412
- OS X 10.8.5
- Cocoapods 0.25.0
- Kiwi 2.2.2 (installed by Cocoapods)