# Available Tools

Below is a list of available tools that can be used with `cli.tools` and
`term.tools` domains. All domains support both http and https unless otherwise
specified.

## ip.{cli,term}.tools

Returns the public ip as seen by our servers, followed by a
new line. You can remove the new line by appending `/r` for raw.

**Usage:** `curl ip.cli.tools`

```
# curl ip.cli.tools
136.32.123.123
#
# curl ip.cli.tools/r
136.32.123.123# 
```

## cowsay.cli.tools

Reimplementation of the popular linux `cowsay` from `Tony Monroe (tony@nog.net)`.

**Usage:** `curl cowsay.cli.tools/option=value/option=value...?option=value...`

| Options                | Location | Default | Description                   |
|------------------------|----------|---------|-------------------------------|
| `n \| no-newline`      | Path     |         | Remove last newline           |
| `w= \| width=`         | GET      | 40      | Max columns                   |
| `s= \| style=borg`     | Path     |         | Style: Borg                   |
| `s= \| style=dead`     | Path     |         | Style: Dead                   |
| `s= \| style=greedy`   | Path     |         | Style: Greedy                 |
| `s= \| style=paranoid` | Path     |         | Style: Paranoid               |
| `s= \| style=stoned`   | Path     |         | Style: Stoned                 |
| `s= \| style=tired`    | Path     |         | Style: Tired                  |
| `s= \| style=wired`    | Path     |         | Style: Wired                  |
| `s= \| style=young`    | Path     |         | Style: Young                  |
| `m= \| msg=`           | GET      | null    | Use instead of sending a body |

> [!note]
> Short options are only available as a path option.

```
# curl cowsay.cli.tools
 _____________
< No Mooosage >
 -------------
    \   ^__^
     \  (oo)\_______
        (__)\       )\/\
            ||----w |
            ||     ||
# curl cowsay.cli.tools -d 'Example Test!'
 _______________
< Example Test! >
 ---------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
# curl cowsay.cli.tools -d @test.txt
 ________________________________
< line 1line 2line 3line 4line 5 >
 --------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
# cat test.txt
Lorem ipsum dolor sit amet, consectetur adipiscing elit.
Nullam sit amet nisl id sapien consectetur venenatis.
# curl cowsay.cli.tools --data-binary @test.txt
 __________________________________________
/ Lorem ipsum dolor sit amet, consectetur  \
| adipiscing elit.                         |
| Nullam sit amet nisl id sapien consectet |
\ ur venenatis.                            /
 ------------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
# curl cowsay.cli.tools/s=paranoid --data-binary @test.txt
 __________________________________________
/ Lorem ipsum dolor sit amet, consectetur  \
| adipiscing elit.                         |
| Nullam sit amet nisl id sapien consectet |
\ ur venenatis.                            /
 ------------------------------------------
        \   ^__^
         \  (@@)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
# curl cowsay.cli.tools/s=paranoid?width=100 --data-binary @test.txt
 __________________________________________________________
/ Lorem ipsum dolor sit amet, consectetur adipiscing elit. \
\ Nullam sit amet nisl id sapien consectetur venenatis.    /
 ----------------------------------------------------------
        \   ^__^
         \  (@@)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```
