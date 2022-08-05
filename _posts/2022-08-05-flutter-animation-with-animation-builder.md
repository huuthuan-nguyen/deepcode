---
layout: post
title:  "Flutter animations with Animation Builder"
author: kean
categories: [ Flutter, animation, builder ]
image: assets/images/9.jpg
---
We can implement animations with controller and animation widget, but there is better way to implement animation which allow you to create a complex animations that requires a widget and builder function. In this post, I will show you how to implement an animation in Flutter using Animation Builder

1. First create an animation controller
```dart
AnimationController? _controller;
```
2. And create an animation widget
```dart
Animation<Size>? _heightAnimation;
```
3. Initialize animation
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
4. Use in your widget
```dart
_heightAnimation?.value.height
```
5. trigger animation
```dart
_controller?.forward();
// or
_controller?.reverse();
```
6. remember to dispose animation to prevent memory leak
```dart
@override
void dispose() {
    super.dispose();
    _controller?.dispose();
}
```