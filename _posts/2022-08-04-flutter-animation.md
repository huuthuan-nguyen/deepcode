---
layout: post
title:  "Flutter animations basic way"
author: kean
categories: [ Flutter, animation ]
image: assets/images/9.jpg
---
Animation in Flutter - basic way

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