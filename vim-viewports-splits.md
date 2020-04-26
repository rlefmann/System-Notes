# Viewports in VIM

## Split the screen
* `:split filename.ext` split the screen horizontally. You can open an existing file or create a new file doing this.
* `:vsplit filename.ext`: Do a vertical split instead
* To close a file, you use the typical `:q` command.


## Navigate and rearrange viewports
* `Ctrl+w+arrowkey`: Move between viewports
* `Ctrl+w+r`: Rotate viewports (you can use capital `R` to rotate the other way around)

## Resize viewports
* `Ctrl+w+plus` and `Ctrl+w+minus`: Horizontal resizing by one line
* You can resize by more than one line, e.g. `Ctrl+w+10+plus`
* `Ctrl+w+>` and `Ctrl+w+<`: Vertical resizing
* You can also set the width of a viewport directly using `:resize 80` or `:vertical resize 80`
* `Ctrl+w+_` and `Ctrl+w+|`: extend the size of the current viewport to the (horizontal or vertical) maximum.
* `Ctrl+w+=`: Reset the size of the viewports
