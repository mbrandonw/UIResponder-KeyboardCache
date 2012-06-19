UIResponder+KeyboardCache
=========================

There is a small problem in iOS that causes a pretty significant delay between the first time the keyboard is requested and when it actually appears. It is only the first time, and seems to be related to the OS trying to cache various properties of the keyboard.

On my iPhone 4S running iOS 5.1 (as of June 19th, 2012) it can take anywhere between .5 and .9 seconds. It can create a frustrating user experience, and most users will try to tap the activation area multiple times, sometimes leading to accidental dismissal of the keyboard.

Plenty of people have asked about this issue on sites like [Stackoverflow](http://stackoverflow.com/questions/9357026/super-slow-lag-delay-on-initial-keyboard-animation-of-uitextfield), but it seems the best solution is from 2009 and it seems pretty risky (sifting through subviews of `UIWindow` looking for the keyboard view).

This category on `UIResponder` gives you a simple method `+cacheKeyboard` so that you can control when this caching work is done. For example, if you are loading some data from a server, then you could invoke this during that downtime. There is another method `+cacheKeyboard:` that takes an optional `BOOL` value. Passing YES to this method causes the cache invocation to happen on the *next* runloop. So, if you performed an animation just before calling this method it would not interrupt that animation.

##Installation

We love [CocoaPods](http://github.com/cocoapods/cocoapods), so we recommend you use it.

##Author

Brandon Williams  
[@mbrandonw](http://www.twitter.com/mbrandonw)  
[www.opetopic.com](http://www.opetopic.com)

## License

UIResponder+KeyboardCache is available under the MIT license. See the LICENSE file for more info.
