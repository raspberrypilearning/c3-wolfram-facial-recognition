```
potter = Classify[<|
   "Harry" -> 
    Import["https://www.google.co.uk/search?q=\"harry+potter\"+\"\
Daniel+Radcliffe\"&tbm=isch", "Images"], 
   "Ron" -> 
    Import["https://www.google.co.uk/search?q=\"ron+weasley\"+\"\
Rubert+Grint\"&tbm=isch", "Images"], 
   "Hermione" -> 
    Import["https://www.google.co.uk/search?q=\"hermione+granger\"+\"\
emma+watson\"&tbm=isch", "Images"] |>]
```
### With a camera

```
Grid[{
  {Text[Style["Which Harry Potter Character Are You?", Bold, 
     18]]}, {Dynamic[image]}, {Text[
    Style[Dynamic[character], Bold, 18]], Button["New Photo",
    image = CurrentImage[ImageSize -> 350];
    character = potter[image];
    probabilities = Normal[potter[image, "Probabilities"]]]}, {Text[
    Style[Dynamic[probabilities], 14]], 
   Button["Turn Off Camera", DeviceClose[First[Devices["Camera"]]]]}},
  Frame -> True, FrameStyle -> Thick]

```
### Without a camera

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
