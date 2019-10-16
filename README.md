# flutter_inner_drawer
[![pub package](https://img.shields.io/badge/pub-0.5.0-orange.svg)](https://pub.dartlang.org/packages/flutter_inner_drawer)
[![Awesome Flutter](https://img.shields.io/badge/Awesome-Flutter-blue.svg?longCache=true&style=flat-square)](https://github.com/Solido/awesome-flutter#drawers)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/dnag88)


Inner Drawer is an easy way to create an internal side section (left/right) where you can insert a list menu or other.

## Installing
Add this to your package's pubspec.yaml file:
```dart
dependencies:
  flutter_inner_drawer: "^0.5.0"
```
## Demo
<div align="center">
  <table><tr>
 <td style="text-align:center">
  <img width="250px"  src="https://github.com/Dn-a/flutter_inner_drawer/raw/master/repo-files/img/example5.1.gif?" />
 </td>
 <td style="text-align:center">
   <img width="250px"  src="https://github.com/Dn-a/flutter_inner_drawer/raw/master/repo-files/img/example5.2.gif?" />
 </td>
 </tr></table>
</div>


### Simple usage
```dart
import 'package:flutter_inner_drawer/inner_drawer.dart';
.
.
.

    final GlobalKey<InnerDrawerState> _innerDrawerKey = GlobalKey<InnerDrawerState>();


    @override
    Widget build(BuildContext context)
    {
        return InnerDrawer(
            key: _innerDrawerKey,
            onTapClose: true, // default false
            swipe: true, // default true            
            colorTransition: Color.red, // default Color.black54
            innerDrawerCallback: (a) => print(a ),// return bool
            leftOffset: 0.6, // default 0.4
            rightOffset: 0.6,// default 0.4
            leftScale: _scale,// default 1
            rightScale: _scale,// default 1
            borderRadius: _borderRadius, // default 0
            leftAnimationType: InnerDrawerAnimation.static, // default static
            rightAnimationType: InnerDrawerAnimation.quadratic,
            
            //when a pointer that is in contact with the screen and moves to the right or left
            // 
             onDragUpdate: (double val, InnerDrawerDirection direction) {
                // return values between 1 and 0
                print(val);
                // check if the swipe is to the right or to the left
                print(direction==InnerDraweDirection.start);
             },
            
            innerDrawerCallback: (a) => print(a), // return  true (open) or false (close)
            // at least one child is required
            leftChild: Container(),
            rightChild: Container(),
            //  A Scaffold is generally used but you are free to use other widgets
            // Note: use "automaticallyImplyLeading: false" if you do not personalize "leading" of Bar
            scaffold: Scaffold(
                appBar: AppBar(
                    automaticallyImplyLeading: false
                ),
            ) 
            OR
            CupertinoPageScaffold(                
                navigationBar: CupertinoNavigationBar(
                    automaticallyImplyLeading: false
                ),
            ), 
        )
    }
    
    void _toggle()
    {
       _innerDrawerKey.currentState.toggle(
       // direction is optional 
       // if not set, the last direction will be used                             
        direction: InnerDrawerDirection.end 
       );
    }
    
    

```

### All parameters
* `leftChild` - *Inner Widget*
* `rightChild` - *Inner Widget*
* `scaffold` - *A Scaffold is generally used but you are free to use other widgets (required)*
* `leftOffset` - *Offset drawer width (default 0.4)*
* `rightOffset` - *Offset drawer width (default 0.4)*
* `onTapClose` - *bool (default false)*
* `swipe` - *bool (default true)*
* `tapScaffoldEnabled` - *possibility to tap the scaffold even when open (default false)*
* `boxShadow` - *BoxShadow of scaffold opened*
* `colorTransition` - *default Colors.black54*
* `leftAnimationType` - *static / linear / quadratic (default static)*
* `rightAnimationType` - *static / linear / quadratic (default static)*
* `innerDrawerCallback` - *Optional callback that is called when a InnerDrawer is opened or closed*
* `innerDrawerKey.currentState.open` - *Open InnerDrawer*
* `innerDrawerKey.currentState.close` - *Close InnerDrawer*
* `innerDrawerKey.currentState.toggle` - *Open or Close InnerDrawer*


## Donate
If you found this project helpful or you learned something from the source code and want to thank me: 
- [![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.me/dnag88)

## Issues
If you encounter problems, open an issue. Pull request are also welcome.