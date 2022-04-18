---
description: Tips for using VS Code
---

# VS Code Tips

## Comment Out Multiple Lines at Once

Sometimes we wish to enable or disable certain segments of our code for quick testing. The easiest way to do this is to "comment out" the code we want to disable by turning it into comments, making our JavaScript runtime ignore those lines of code.

Rather than adding `//` to the start of each line manually, VS Code has a shortcut that allows us to comment out multiple lines simultaneously. To do this, select all lines we wish to comment out, then use the keyboard shortcut `Ctrl+/` on Windows, or `Cmd+/` on Mac.

## Editing a Variable Name in Multiple Places Concurrently

Sometimes we want to change the name of a variable in our code, a common practice in [refactoring](https://en.wikipedia.org/wiki/Code\_refactoring). If that variable is used in multiple places, we may be tempted to edit each instance individually. Luckily VS Code has a convenient feature that allows us to edit all instances of the same variable simultaneously, saving time and our fingers.

### Within a Single File

1. Move your cursor to the first instance of the variable
2. Press/hold `Ctrl+D` on Windows or `Cmd+D` on Mac until all instances of that variable are selected
3. Use left or right arrow keys to enable cursors on each instance of that variable and edit them simultaneously

### Across Multiple Files

VS Code has a [search and replace feature](https://code.visualstudio.com/docs/editor/codebasics#\_search-across-files) that allows us to edit all instances of a given string in multiple files at once.

## Hide Minimap

The [VS Code minimap](https://code.visualstudio.com/docs/getstarted/userinterface#\_minimap) is displayed by default in VS Code to show one's vertical position within a file. This may not be necessary and we can hide the minimap for more space in VS Code. Hide the minimap by toggling View > Show Minimap in the menu bar.
