## Use your own photos, without a camera

Now see which character the `Classify` function thinks you look most similar to!

If you don't have a camera, you can still use a photo of yourself by uploading one to your notebook.

To load an image directly from your computer, you need to make two buttons. The first button get created automatically when you use `FileNameSetter`. This function creates a variable with the name of the file you select. When you press the button, a pop-up window appears in whic you can search for and select your image. `FileNameSetter` then remembers the path to the selected image.

Then use `Import` to create a second button to actually load the selected image.

You can show the imported image using `Dynamic`.

--- task ---
Create two buttons:
1. One that sets the file path using `FileNameSetter`
1. One that loads the file to the notebook

Show the image using `Dynamic`.

```
FileNameSetter[Dynamic[file], Appearance -> "Select New Image"]
Button["Load file", image = Import[file]]
Dynamic[image]
```
--- /task ---

Then put the imported image through the `Classify` function.

--- task ---

Run your photo through the `potter` classifier.

```potter[image]```

And use `"Probabilities"` to see how similar you look to each character.

```potter[image, "Probabilities"]```

--- /task ---

--- task ---

Build a button that takes a photo and runs it through the `potter` classifier.

```
Button["New Photo",
image = CurrentImage[ImageSize -> 350];
character = potter[image];
probabilities = potter[image, "Probabilities"]]
```

Display the results using `Dynamic`.
 
```
Dynamic[image]
Dynamic[character]
Dynamic[probabilities]
```
--- /task ---
