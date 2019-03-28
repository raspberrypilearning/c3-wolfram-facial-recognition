## Use your own photos, with a camera

If you don't have a camera to hand, skip to the next step.

Now see which character the `Classify` function thinks you look most similar to!

To take a photo of yourself, you can use the `CurrentImage` function.

--- task ---

Take a photo of yourself using your camera, and give the photo the variable name `image`.

```image = CurrentImage[ImageSize -> 350]```

--- /task ---

Then put this photo through the `Classify` function.

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
