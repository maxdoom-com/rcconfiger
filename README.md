# rcconfiger
readable config file configurator

## what does it do?
rcconfiger reads and modifies rc (readable config) files.
you may get (-g) or set (-s) single options in a supported config file.
you may list all identified options (-l).
you may decide to let rcconfiger automaticly create the config file if it does not exist.
it's possible to comment (-c) and uncomment (-u) an option.

furthermore it allows to apply the options in a "patch file" to a given config file. this way you can (un)comment options and set options.


## command line options:
```
rcconfiger [-h|--help]
 -h|--help    ... print this help and exit

rcconfiger [[-n] -f file] [-g key] [-s key value] [-c key] [-u key] [-l]
 -f file      ... work on file
 -n           ... create file if nessesary
 -g key       ... get value of key
 -s key value ... set key = value
 -c key       ... comment key
 -u key       ... uncomment key
 -l           ... list all options

rcconfiger [[-n] -f file] [-p patch]
 -p patch     ... apply config lines from patch to file
                  lines must be (optionally commented) key=value pairs, empty
                  or comments (#[ ]...)
```

## supported format
A rc file that wants to be configurable with this tool has to follow these formating rules:
- options are defined as ```key = value``` pairs
- options may be commented out with a single hash as the first character of the line. the key must start right after the hash tag.
- everything else is kept in place

an example:
```
# this is a comment.
## this as well.

#an-option= 123
another_option =asd
some.more="Test 123"
```

## beware!
**rcconfiger will automaticly save the files if any changes were made.**
**use it at your own risk.**
