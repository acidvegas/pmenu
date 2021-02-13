# pmenu
> pass via dmenu

There are many dmenu scripts for pass floating around, but this one has got you covered in every way possible. You can fully navigate your pass database with the ability to view multi-lined entries, copy specific lines from your entries, and even entering your GPG key password, all via dmenu!

## Requirements
- [dmenu](https://tools.suckless.org/dmenu/)
- [pass](https://git.zx2c4.com/password-store/)
- [pinentry](https://github.com/gpg/pinentry)
- [pinentry-dmenu](https://github.com/ritze/pinentry-dmenu)
- [xclip](https://github.com/astrand/xclip)

## Pinentry Usage
Using [pinentry-dmenu](https://github.com/ritze/pinentry-dmenu) will allow you to enter your GPG key password inside of dmenu, but in order to do that you will need to create a wrapper for pinetry at `$HOME/.gnupg/pinentry-wrapper`:
```
if [ "$PINENTRY_USER_DATA" = "dmenu" ]; then
    exec /usr/local/bin/pinentry-dmenu "$@"
else
    exec /usr/bin/pinentry-curses "$@"
fi
```
Make it executable with `chmod +x $HOME/.gnupg/pinentry-wrapper` and then edit your `.gnupg/gpg-agent.conf` and add `pinentry-program $HOME/.gnupg/pinentry-wrapper`.

## Todo
- Incorperate the `args` variable to allow custom dmenu args such as colors, font, etc.

## Mirrors
- [acid.vegas](https://acid.vegas/pmenu) *(main)*
- [GitHub](https://github.com/acidvegas/pmenu)
- [GitLab](https://gitlab.com/acidvegas/pmenu)