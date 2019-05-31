# Flowc setup (Linux)

## Simple JavaScript target setup

1. Clone Flow9 repository
    ```
    git clone https://github.com/area9innovation/flow9
    ```

2. Add `flow9/bin` to `PATH` in `.profile` & relogin into system:
    ```
    PATH=$PATH:/path/to/flow9/bin
    ```

3. Install **Java 8 Runtime Environment** to run `flowc1`.

    Your distro may have this package in repositories, called `openjdk-8-jre` or `jre8-openjdk`.


4. Install **Haxe 3.4.7** to be able to compile into js target.

    Your distro may have it too, or check the [haxe website](https://haxe.org/download/linux/).

6. Run `haxelib setup` and specify the path for haxe libraries.

7. Run `haxelib install pixijs 4.7.1` to install **PixiJS** required for canvas rendering in js.

Now you're ready to compile flow programs to js target like so:
```
flowc1 js=flow_program.js html=flow_program.html flow_program.flow
```

Open `flow_program.html` in browser to see the result. Check browser console for output.

## Advanced steps

If you need to rebuild the `flowc1` binary:

1. Install **Java 8 Development Kit** to install `javac` that can compile `flowc1`. Your distro may have this package in repositories, called `openjdk-8-jdk` or `jdk8-openjdk`.

2. Change to flow9 directory & run `build-flowc`.


## Troubleshooting

#### Error: This is the first time you are running haxelib. Please run `haxelib setup` first

Setup haxe by performing step 5


#### Error: Library pixijs is not installed : run 'haxelib install pixijs'

Install pixijs by performing step 6