# Heaps 2D Basics Tutorial

## Part 1

Welcome to a tutorial that should explain how to make a simple 2D game with Heaps.

### Foundation

- Haxe and Heaps should be installed
- you should be able to compile and run the Hello World samples (at least either Html5/JS or HashLink)


### A small recap

- Using Heaps may at times require some deeper work and skills compared to when you come from an editor based game engine like (Unity, Godot, Game Maker, Cocos2D) then things might be a bit slower in the beginning, but you'll get there!
- Haxe is the programming language. (This means for instance you can directly use the Haxe API as well as the Heaps API.)
- There is an introduction to the 2D side of Heaps under: https://github.com/HeapsIO/heaps/wiki/H2D-Introduction

### What you see in the first code file: Tutorial_01.hx

#### main method

The smallest Heaps program is:

```haxe
class Main extends hxd.App {
    static function main() {
        new Main();
    }
}
```

The static main class (in our code named `Tutorial_01`) must instantiate itself as an object. Thus a Heaps application (an instance of `hxd.App`) is created.

(Sidenote: You can also write `var myapp = new Main();` to save the reference to your app and manipulate it later from other classes.)

In our case this method also includes the lines:

```haxe
    #if sys
    hxd.Res.initLocal();
    #else
    hxd.Res.initEmbed();
    #end
```

Here we use Haxe' conditional compilation (by `#hello` syntax). In this case it means that when we compile to a target platform that is defined as `sys` (https://haxe.org/manual/std-sys.html). Otherwise the code after the `#else` gets executed.

`hxd.Res` (and `hxd.res`) provides us with access to our game assets and resources. (usually they are in the same project directory and use their own folder named `res`). Here we initialize the Heaps resource system. This will allow us to access and use game assets (like sprites, images, sounds and music) inside our game.

The code here will use local files for desktop platforms, but when compiling to javascript our game assets are going to be embedded into the js-script file. (By the way this works fine here because our assets together are very small in file size. For larger projects it is recommended to build PAK files).

#### init method

The `init` method is called right after `hxd.App` is set up as an instance. Now we can *actually* use the full Heaps API and can start programming our game. This means here we're no longer in static context like in the main method. Here is the first time after starting our game that we can add `h2d.Object`s to our scene.

In Heaps anything visual in 2D is an `h2d.Object` in the end. That is why all the objects we're going to add now extend the `h2d.Object` class: `h2d.Bitmap` and `h2d.Text`.

For our sprites in this sample we use a `h2d.Bitmap`, which can be used for images or single sprites without animation. The bitmap needs a `h2d.Tile`. Before images can be rendered to the screen, they must be loaded as a tile first, which only exists in the RAM for now. Only the bitmap, when added to the scene (`s2d` when inside the `hxd.App` context), can finally draw the tile to the screen so the user can actually see it.

We create a single bitmap for the player and then by two for-loops create several other objects, here called "coin" and "enemy". By our own defined method `assignRandomPositionInScene` we give them a random position inside our scene.

In the end we add a small description that will also be shown when running the game: A `h2d.Text`. Since we don't have any font of our own we rely on the Heaps font provided by default. To load this font we use `hxd.res.DefaultFont.get()`.
