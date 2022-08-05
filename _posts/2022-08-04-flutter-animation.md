---
layout: post
title:  "Flutter animations basic way"
author: kean
categories: [ Flutter, animation ]
image: assets/images/flutter-banner.jpg
---
There are a sereval ways to implement animations in Flutter, today I will show you the basic way to do it. This way will need 2 object, an controller to handle duration of animation, and animation widget handle the begin and end value of animation.

1. First create an animation controller
```dart
AnimationController? _controller;
```
2. And create an animation widget
```dart
Animation<Size>? _heightAnimation;
```
3. Add Ticker Provider mixin to your stateful widget
```dart
with SingleTickerProviderStateMixin
```
4. Initialize animation
```dart
@override
void initState() {
    supper.initState();

    _controller = AnimationController(
        vsync: this,
        duration: const Duration(
            milliseconds: 300,
        ),
    );

    _heightAnimation = Tween<Size>(
        begin: const Size(
            double.infinity,
            260,
        ),
        end: const Size(
            double.infinity,
            320,
        ),
    ).animate(CurveAnimation(
        parent: _controller,
        curve: Curves.linear,
    ));

    _heightAnimation?.addListener(() {
        setState(() {});
    });
}
```
5. Use in your widget
```dart
_heightAnimation?.value.height
```
6. trigger animation
```dart
_controller?.forward();
// or
_controller?.reverse();
```
7. remember to dispose animation to prevent memory leak
```dart
@override
void dispose() {
    super.dispose();
    _controller?.dispose();
}
```

There is a drawback of this way, the animation will always rebuild the widget when the state changes, so there is a better way is use Animation Builder to improve app performance.