---
title: Keyboard modifications
tags:
- apple
- macos
---

# Keyboard modifications

## Why?

* `CapsLock` is never used and `Esc` is hard to reach, but useful. 
    * The typical _back to normal mode_ in vim, but also as meta `Esc  f` `Esc  b` is next/previous word. 
* I've used to have much more sophisticated setup with a smart caps lock, but not anymore. It's to finicky.
    * On linux there's no way to do it reliably.
    * On macOS there's karabinier elements, which is amazing. But in my tests I had trouble with karabinier + touchbar customizations. 


## How?

* MacOS
    * **Settings** then **Keyboard** then **Modifier Keys** then you can map `CapsLock` to your linking.
* Linux -- ubuntu
    * Use gnome tweaks to map `CapsLock` to `Esc`.


## Resources

* Space Cadet -- an article on the joy of improving your keyboard workflow [https://stevelosh.com/blog/2012/10/a-modern-space-cadet/#control-escape](https://stevelosh.com/blog/2012/10/a-modern-space-cadet/#control-escape)
* Various keyboard improvements with hammerspoon -- [https://github.com/jasonrudolph/keyboard#features](https://github.com/jasonrudolph/keyboard#features)
* Smart capslock (on ubuntu) -- [https://gist.github.com/tanyuan/55bca522bf50363ae4573d4bdcf06e2e](https://gist.github.com/tanyuan/55bca522bf50363ae4573d4bdcf06e2e)
* Return to control on ubuntu -- [https://emacsredux.com/blog/2016/01/30/remap-return-to-control-in-gnu-slash-linux/](https://emacsredux.com/blog/2016/01/30/remap-return-to-control-in-gnu-slash-linux/) -- note the first comment about using xkeysnail.
* xkeysnail example configuration -- [https://github.com/mooz/xkeysnail/blob/master/example/config.py](https://github.com/mooz/xkeysnail/blob/master/example/config.py) -- to remap capslock & return to control