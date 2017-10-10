tcl-tk (OSX)
===

install
---

```
brew reinstall python --with-tcl-tk
brew install homebrew/dupes/tcl-tk
```

check homebrew output message
---
```
....

echo 'export PATH="/usr/local/opt/tcl-tk/bin:$PATH"' >> ~/.bash_profile

because tk installs some X11 headers and macOS provides an (older) Tcl/Tk.

If you need to have this software first in your PATH run:
  echo 'export PATH="/usr/local/opt/tcl-tk/bin:$PATH"' >> ~/.bash_profile

For compilers to find this software you may need to set:
    LDFLAGS:  -L/usr/local/opt/tcl-tk/lib
    CPPFLAGS: -I/usr/local/opt/tcl-tk/include

...

```

test
---
```python
python -c 'import Tkinter; Tkinter.Tk()'
```
