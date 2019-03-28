## Build an interface

At this point, you have either one or two buttons:
+ If you're using a camera, your button takes a photo
+ If you are not using a camera, one button sets the file path, and the other button imports00 the image

Now use `Grid` to create a good-looking interface for the button(s).

Here is a basic example of `Grid`.

![Grid](images/Grid.png)

`Grid` is made up of a list of lists, where each list becomes a row in the grid.

--- task ---

Make a `Grid` with four rows.

+ The first row should have a title. You can make text look the way you want using `Text` and `Style`.
+ The second row should be the `Dynamic` image. This is either be the image from your camera, or the image you import using your buttons.
+ The third row should have two items: the result of your `Classify` function, and your first button. The first button is either `CurrentImage`, or `FileNameSetter`, depending on whether you have one or two buttons.
+ **If you are using a camera**, the fourth row should have one item: the result of `"Probabilities"` from your `Classify` function.
+ **If you are uploading an image**, the fourth row should have two items: the result of `"Probabilities"` from your `Classify` function, and the button to import the file and classify the image.

You can use `Framed` and `FrameStyle` to draw a frame around the `Grid`.

**If you are using a camera**, this is the code you need:
```
Framed[Grid[{
{Text[Style["Which Harry Potter Character Are You?", Bold, 18]]},
{Dynamic[image]},
{Text[Style[Dynamic[character], Bold, 18]],
Button["New Photo",
image = CurrentImage[ImageSize -> 350];
character = potter[image];
probabilities = Normal[potter[image, "Probabilities"]]]},
{Text[Style[Dynamic[probabilities], 14]]}}], FrameStyle -> Thick]
```

**If you are uploading an image**, this is the code you need:

```
Framed[Grid[{
{Text[Style["Which Harry Potter Character Are You?", Bold, 18]]},
{Dynamic[image]},
{Text[Style[Dynamic[character], Bold, 18]],
FileNameSetter[Dynamic[file], Appearance -> "Select New Image"]},
{Text[Style[Dynamic[probabilities], 14]],
Button["Classify Image",
image = Import[file];
character = potter[image];
probabilities = Normal[potter[image, "Probabilities"]]]}}],
FrameStyle -> Thick]
 ```
---/task ---

![Interface](images/firstcomplete.png)
