<img src="http://cf.jare.io/?u=http%3A%2F%2Fwww.yegor256.com%2Fimages%2Fbooks%2Felegant-objects%2Fcactus.svg" height="100px" />

[![EO principles respected here](http://www.elegantobjects.org/badge.svg)](http://www.elegantobjects.org)
[![We recommend IntelliJ IDEA](http://www.elegantobjects.org/intellij-idea.svg)](https://www.jetbrains.com/idea/)

[![Build Status](https://travis-ci.org/yegor256/jpages.svg)](https://travis-ci.org/yegor256/jpages)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/yegor256/jpages/blob/master/LICENSE.txt)
[![Hits-of-Code](https://hitsofcode.com/github/yegor256/jpages)](https://hitsofcode.com/view/github/yegor256/jpages)

**jPages** is an experimental prototype of a web framework,
which respects all possible principles of
[true object-oriented](http://www.yegor256.com/2014/11/20/seven-virtues-of-good-object.html)
design. More about it in this
[blog post](https://www.yegor256.com/2019/03/26/jpages.html)
and in this [webinar](https://www.youtube.com/watch?v=bVzEPOZ_mDU).

This is how you start a web app:

```java
Thread thread = new Thread(
  () -> {
    App app = new App(
      new App.Resource() {
        @Override
        public App.Resource refine(String name, String value) {
            if (value.equals("/")) {
              return new TextResource("Hello, world!");
            }
            return new TextResource("Not found!");
        }
        @Override
        public void print(App.Output output) {
          output.print("X-Body", "Not found");
        }
      }
    );
    try {
      app.start(8080);
    } catch (Exception ex) {
      System.out.println(ex.getMessage());
      throw new IllegalStateException(ex);
    }
  }
);
thread.setDaemon(true);
thread.start();
```

Do you want to contribute? Submit a pull request.
