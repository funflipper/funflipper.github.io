# funflipper.github.io
fun_flipper / funflipper / libdolphin (which from now on will be referred to as dolphin) is a FOSS (free and open source software) general purpose binary format fuzzer.

fun_flipper works by randomly "flipping" (randomizing) characters in a binary / binary format, to try to find bugs in their parsers.

as an example, to fuzz macOS's disk attachment, you might do

```bash
IN_FILE = {INSERT_DMG_PATH_HERE}
while true;
do
    OUT_FILE = OUT_$RANDOM$RANDOM
    python fun_flipper.py $IN_FILE $OUT_FILE.dmg
    hdiutil attach $OUT_FILE.dmg
    if [ $? -lt -127];
    then
        echo "possible bug? sleeping"
        sleep 5
    fi
done
```

when it finds a bug, it will notify you and sleep.

if you think your product could be made more secure with fun_flipper binary fuzzing, go ahead and use it in your project, it's GPLv2! if you need help, you can file an issue on GitHub, or email the "manager" at [aquaticvegetable@gmail.com](mailto:aquaticvegetable@gmail.com)
