# My VSCode config

## From: [github](https://github.com/microsoft/vscode/issues/42994)

I was about to transfer a set of 20 extensions to another instance of VSC on another machine. In Atom it works simply with two commands:
create a list with all extensions

```bash
apm list --installed --bare > packages.list
```

Install all extensions from list

```bash
apm install --packages-file packages.list
```

I know you have the possibility to install via cli as well in VSC, but it is somewhat weird. I can list all the extensions and save them in a list:

```bash
code --list-extensions > extensions.list
```

But from that point on it's overcomplicated as I'm not able to install from a list. So, in a powershell I now use something like

```bash
foreach($line in get-content extensions.list) {code --install-extension $($line)}
```

But I'd wish there was a built-in method to install from a list, like in Atom. Please consider this in a future update.

Linux/Mac:

```bash
cat extensions.list | xargs -L1 code --install-extension
```

---

I use this for windows cmd:
for /F "tokens=*" %%A in (extensions.list) do code --install-extension %%A

and this for bash:

```bash
<extensions.list xargs -I % code --install-extension %
```
