---
layout: post
title:  "Flutter animations with Animation Builder"
author: kean
categories: [ Flutter, animation, builder ]
image: assets/images/9.jpg
---
We can implement animations with controller and animation widget, but there is better way to implement animation which allow you to create a complex animations that requires a widget and builder function. In this post, I will show you how to implement an animation in Flutter using Animation Builder

1. First create an animation controller to control animation duration
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

    // attach controller to animation
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

    // we do not need to listen state anymore
    // _heightAnimation?.addListener(() {
    //     setState(() {});
    // });
}
```
4. Use in your widget
```dart
@override
  Widget build(BuildContext context) {
    return AnimatedBuilder(
      animation: _controller,
      child: Container( // prebuilt child will not rebuild on every animation tick
        width: 200.0,
        height: 200.0,
        color: Colors.red,
        child: const Center(
          child: Text('Hello World!'),
        ),
      ),
      builder: (BuildContext context, Widget? child) {
        return Container(
          height: _heightAnimation.value.height,
          color: Colors.blue,
          child: child,
        );
      },
    );
  }
}
```

Animation Builder is not limited to Animations, any subtype of Listenable (ChangeNotifier and ValueNotifier) can use with an AnimationBuilder to rebuild only specific widgets leaving others untouched.
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

It's more efficient to build a subtree once instead of rebuilding it on every animation tick. Using prebuilt child can improve performance significantly in some cases and is therefore a good practice.