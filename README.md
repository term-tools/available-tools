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

Reimplementation of the popular linux `cowsay` from
`Tony Monroe (tony@nog.net)`.

**Usage:** `curl cowsay.cli.tools/flag/flag...?option=value...`

| Flags | Location | Default | Description                   |
|-------|----------|---------|-------------------------------|
| n     | Path     | false   | Allow new lines               |
| W     | GET      | 40      | Max columns                   |
| b     | Path     | false   | Style: Borg                   |
| d     | Path     | false   | Style: Dead                   |
| g     | Path     | false   | Style: Greedy                 |
| p     | Path     | false   | Style: Paranoid               |
| s     | Path     | false   | Style: Stoned                 |
| t     | Path     | false   | Style: Tired                  |
| w     | Path     | false   | Style: Wired                  |
| y     | Path     | false   | Style: Young                  |
| E     | GET      | (style) | Custom Eyes                   |
| T     | GET      | (style) | Custom Tongue                 |
| msg   | GET      | null    | Use instead of sending a body |

```
# curl cowsay.cli.tools
 ______________________________
< Welcome to cowsay.cli.tools! >
 ------------------------------
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
| adipiscing elit. Nullam sit amet nisl id |
\ sapien consectetur venenatis.            /
 ------------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
# curl cowsay.cli.tools/n --data-binary @test.txt
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
# curl cowsay.cli.tools/n/p --data-binary @test.txt
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
# curl cowsay.cli.tools/n/p?W=100 --data-binary @test.txt
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