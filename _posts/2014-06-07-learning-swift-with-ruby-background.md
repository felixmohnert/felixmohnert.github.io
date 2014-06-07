----
layout: post
title: Learning Swift With a Ruby Background
description: "Things you need to know coming from Ruby learning Swift"
category: stories
tags: [swift, ruby, objective-c, learn]
image:
  feature: header-image-swift.png
  credit: Felix Mohnert
  creditlink: http://www.felixmohnert.eu
comments: true
share: true
---

As soon I heard about the Swift programming language I got curious. I tried
already to look into Objective-C but felt not quite ready yet. My programming
knowledge developed now over about 2 years, with almost no prior knowledge.
In the past 2 years I learned Ruby (on Rails) and of course all the things
related to it. I think the time has come to dig into mobile engineering - what
could be a better moment as the release of Swift.

## Resources

The main resource of knowledge (and of course the only complete resource by now)
is the book "The Swift Programming Language" from Apple and can be found for
free in the
[**iBook Store**](https://itunes.apple.com/us/book/the-swift-programming-language).

To run your code, you will need Xcode 6 beta. This version is for now only
accessible with an enrollment in one of the Apple Developer programs
(80€ a year).

## Coming from Ruby

As explained above, I don't have any knowledge of Objective-C, so this part is
written only from a Ruby's point of view.

### Type safe

Swift is a type safe language. That can actually save you some hassle, because
you find bugs in your code in an early stage. That doesn't mean necessarily
that you always have to define the type of a variable or a constant. It works
in two ways, first explicitly, second via type inference.

{% highlight c %}
let explicitString: String = "I'm explicitly a String"
let implicitString         = "My type is defined by this string"
{% endhighlight %}

What is really important at this point: Both strings are immutable because of
my usage of "let". To define a mutable variable you explicitly have to define
them by "var". Once set, you can't change the behavior anymore.

Another important fact coming from Ruby: Don't mix 1 and 0 with true and false.
Variables from type Boolean can't be assigned a number!

### Optionality

I you define a mutable variable with "var" you really have to be aware, that
the type is not changeable. That means as well, that the **variable can't be nil
anymore!!** Now the optionals become meaning.

{% highlight c %}
var nonOptionalString = "I'm a string"
nonOptionalString     = nil // This result's in a runtime error!

var optionalString: String? = "I'm a optional String"
optionalString              = nil // It just works

// How do I work with optionals?
optionalString  // This gives me false
optionalString! // This gives me nil

optionalString = "I'm a optional String"
optionalString  // This gives me true
optionalString! // This gives me "I'm a optional String"
{% endhighlight %}

If you think about, this is quite nice. If you have a type defined and it is
no optional, you always get back a value. The above described explicit optionals
are a nice way to make another behavior clear. If you don't like all of this
you can use optionals quite the same as variables in Ruby by just defining them
as implicit optionals:

{% highlight c %}
var implicitOptionalString: String! = "I'm optional but don't act like it."
implicitOptionalString // This gives me the string
{% endhighlight %}

### Assertions

Not super interesting but Swift has the option to only raise an assertion with
a specific condition in a nice syntactic way.

{% highlight c %}
assert(hamburg.hasPrefix("be better"), "Hamburg is better!")
/* This assertion is triggered with a condition. When
"hamburg.hasPrefix("be better") is true, the assertion won't be triggered. */
{% endhighlight %}

That's it for now. The next story will be about collection types and the so
called
"[control flow](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/ControlFlow.html)".
