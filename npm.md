## Upgrade Node

[Full Explanation Here](https://davidwalsh.name/upgrade-nodejs)
```
sudo npm cache clean -f
sudo npm install -g n
sudo n stable
```

## Tilde Vs Caret
In the simplest terms, the tilde matches the most recent minor version (the middle number). ~1.2.3 will match all 1.2.x versions but will miss 1.3.0.

The caret, on the other hand, is more relaxed. It will update you to the most recent major version (the first number). ^1.2.3 will match any 1.x.x release including 1.3.0, but will hold off on 2.0.0.

So if you have something that requires a dependency of ^15.4.2, a package of **16 WILL NOT WORK**