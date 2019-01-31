## Using Your Own Photos, With a Camera

The aim of this project is to be able to see which character the `Classify` function thinks you are.

In order to take a picture, you can use the `CurrentImage` function.

--- task ---
Take a photo of yourself using your camera, and give it the variable name `image`

```image = CurrentImage[ImageSize -> 350]```

--- /task ---

We can then put this image through the Classify Function to see which character the function thinks you look like.

--- task ---
Run your photo through your classifier function to see which character you look most like.

```potter[image]```

And use `"Probabilities"` to see how likely you are to be each character.

```potter[image, "Probabilities"]```

--- /task ---

--- task ---
Build a button which takes a photo and runs it through the classifier function.

```
Button["New Photo",
image = CurrentImage[ImageSize -> 350];
character = potter[image];
probabilities = potter[image, "Probabilities"]]
```

Display the results using `Dynamic`
 
```
Dynamic[image]
Dynamic[character]
Dynamic[probabilities]
```
--- /task ---
