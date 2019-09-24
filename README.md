# Bitbake Nonsense

*I worked on Bitbake and after a week of reading documentation I went nuts...*


* Appending or *why make it simple when you can make it complicated*

```sh
FOO += "bar"
FOO .= " bar"
FOO_append = " bar"
```
These 3 expression do the same thing...


* The world of assignment

```sh
BAR = "FOO" # Assignment when the variable is actually used (??)
BAR ?= "FOO" # Assignment now only if BAR is undefined (I can understand)
BAR ??= "FOO" # Assignment at the end of "the parsing process"
              # if BAR is undefined (Mmmm...)
BAR := "FOO" # Assignment of the variable now (Ok so this is actually "=")
```


* ```BITBAKE_remove = "simplicity"```

```sh
FOO = "123 456"
FOO_remove = "123"
# FOO equals " 456"
# Do we need to play hide and seek to get the value of FOO ?!
```


* Find your way into the configverse !

```sh
$ find meta/ -name "*.conf" -print | wc -l
66 # ok
$ find meta/ -name "*.bbclass" -print | wc -l
201 # lol
$ find meta/ -name "*.bb" -print | wc -l
781 # wait
$ wc -l meta/conf/bitbake.conf
906 meta/conf/bitbake.conf # wtf !
```


* Error handling.

```sh
$ bitbake <some-target-with-an-error>
ERROR: Unable to start bitbake server (None)
# blabla...
Traceback (most recent call last): # Wow python errors ?
# blabla python errors...
# Do I need to learne python3 to use Bitbake ?
# blabla python errors...
  raise bb.BBHandledException
# WTF is this supposed to help me ??
# I guess this "BBHandledException" is not handled after all...
```

### Feel free to add more Bitbake nonsense !
