---
layout: post
title:  "Flutter animations with Animated Container"
author: kean
categories: [ Flutter, animation, container ]
image: assets/images/flutter-banner.jpg
categories:
  - "flutter"
---
We can implement Flutter animations manually or with Animated Builder, but if we only need to implement animations for Container only, there is a short way to do that with AnimatedContainer widget.

1. Create new AnimatedContainer
```dart
@override
  Widget build(BuildContext context) {
    return AnimatedContainer(
      duration: const Duration( // duration
        milliseconds: 300,
      ),
      curve: Curves.easeIn, // animation
      child: const Center(
        child: Text('Hello World!'),
      ),
      height: triggeredValue ? 500 : 300, // trigger by value
    );
  }
}
```

With this short way, you do not need to explicit animation controller, animation widget and ticker provider mixin.