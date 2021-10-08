---
layout: post
title: "TheFneuff"
subtitle: "Java 2D game"
background: '/img/posts/TheFneuff/header.png'
tags: "Java, JavaFX"
---
## Background

This application is the result of my homework topic in the CTU Programming in Java course.

### Installation & Setup

As this is an old project, make sure you are running it with Java 8.

### Application overview
Each level is described in an external file in JSON format. The game loads a list of player items from a file.  At the end of each level, the game saves the list of items in the same format. This is done via the GSON library.
The method of fighting monsters is implemented within the game - AABB collisions are in place to ensure that the player takes damage when he and a monster collide.

The hero is able to use the collected objects to interact with other objects (open the door with a key etc.).

The application is implemented in Java with the addition of JavaFX for the frontend. The sprites are animated by cycling several images - how is shown in the code example below.

```java
/**
 * Represents animated image consisting of frames.
 */
public class AnimatedImage {
    // assumes animation loops,
    // each image displays for equal time
    private transient Image[] frames;
    private double duration;
    private int width, height;

    private String spriteName;
    private int numberOfSpritesToAnimate;

    /**
     * Creates instance of AnimatedImage.
     *
     * @param spriteName               sprite url
     * @param numberOfSpritesToAnimate of how many frames animation consists
     * @param duration                 how long should one frame be displayed
     * @param width                    width of sprite
     * @param height                   height of sprite
     */
    public AnimatedImage(final String spriteName, int numberOfSpritesToAnimate, double duration, int width, int height) {
        this.duration = duration;
        this.width = width;
        this.height = height;
        this.spriteName = spriteName;
        this.numberOfSpritesToAnimate = numberOfSpritesToAnimate;
        loadSprites(spriteName, numberOfSpritesToAnimate);
    }

    /**
     * Loads images from source.
     *
     * @param spriteName sprite url
     * @param number     of how many frames animation consists
     */
    public void loadSprites(final String spriteName, int number) {
        Image[] frames = new Image[number];
        for (int i = 0; i < frames.length; i++) {
            frames[i] = new PixelImage(spriteName + i + ".png", width, height);
        }
        this.frames = frames;
    }

    /**
     * @param time current time
     * @return current frame in animation depending on time
     */
    public Image getFrame(double time) {
        int index = (int) ((time % (frames.length * duration)) / duration);
        return frames[index];
    }
    ...
```

## [GitHub link](https://github.com/zdenduk/TheFneuff)

