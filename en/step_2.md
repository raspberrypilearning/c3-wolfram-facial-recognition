##  Building a Classify Function

--- task ---
If you have never used the Wolfram Language before, follow [this guide](https://projects.raspberrypi.org/en/projects/getting-started-with-mathematica) to get started and learn to use the tool. You'll need to look at **Starting Mathematica** and **Programming in Mathematica**.
--- /task ---

We will be using the Classify function to put images of each character into buckets, depending on the features of the image.
The Wolfram Language can handle a lot of image processing tasks for us, so we don't need to worry about that.

Let's look at how the Classify function works: 


  First, we need to associate a label to a value.

![Example Training Data](images/exampletrainingdata.png)

If we look at this training data, we can see that the colour red fits into the category `"Red"`, and the colour blue fits into the category `"Blue"`, but we can't tell what category orange falls into. This is because we haven't told the computer that information. `Classify` helps us teach the computer to make a good guess. Let's train a Classify Function on this training data.

``` classified = Classify[exampletrainingdata]```

When you evaluate `classified`, after waiting a few seconds, you should get a `ClassifierFunction`.

![Example Classifier Function](images/exampleClassifierFunction.png)

The `ClassifierFunction` has categories (Classes) `"Red"` and `"Blue"`. Let's see how good this Classify Function is at telling us which category a new colour should go in.

![Example Classifier Function Output](images/exampleClassifierOutput.png)

The classify function put the new colour into the category whose members most closely resembled the new colour.

Now that we know what a classify function is, we can apply it to our problem. Instead of colours, we are going to use images of Harry Potter, Hermionie Granger and Ron Weasley as data for our categories.

First, we need to find images of Harry, Ron and Hermione, so that we can train our `Classifier` to recognise their faces. We can do this by finding the URL to a Google image search, and then using Import to import the images.

We will then train a classifier function on the images, putting them into three categories: "Harry", "Ron", and "Hermionie".

--- task ---
Create a `Classify` function called `potter` using Google Images search results for each main Harry Potter character.

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

This function will take some time to evaluate.
--- /task ---

Let's test the `Classifier` function with images it hasn't seen before.

--- task ---
Go onto the internet and find two photos each of Harry, Ron, and Hermione. Try to find one when they were a child, and one as an adult.

Test your `potter` classifier by the images you find through it in a list, `{}`. You should get the classification for each image as the output.

Classify the images by replaceing `image1` by copy/pasting the first image, `image2` with the second image etc. (If you are using Wolfram in a browser, we recommend that you save images to your desktop and then drag and drop them into the notebook)

`potter[{image1,image2,image3,image4,image5,image6}]`
--- /task ---

It looks like our Classifier is doing quite well. It recognises the characters even when they look younger or older, or have very different backgrounds. 

Let's see what the function does when we ask it to classify a photo which is not of one of the characters.

![New Character](images/testsubjects.png)

As you can see, the Classifier puts the image in to the most similar category.

We can also see how sure the Classify function is by using `Probabilities`. This gives the probability that an image belongs to each class. In this case, there is an 89.5% probability that this image fits into the `Harry` class.

![Probabilities](images/probability.png)

--- task ---
Add two more characters to your classifier: Neville Longbottom, played by Matthew Lewis, and Luna Lovegood, played by Evanna Lynch.

--- hints ---
--- hint ---
Look at the code you used to create the `potter` classifier, and see where the names of the characters and actors appear. In case you don't know them:

  + Harry Potter was played by Daniel Radcliffe
  + Hermione Granger was played by Emma Watson
  + Ron Weasley was played by Rupert Grint

These names are used to create Google Image searches for pictures of those characers. You'll need to do the same for the two new ones.
--- /hint ---
--- hint ---
You'll need to add two more lines to your classifier, changing the character and actor names to those for Neville and Luna.

Notice that the last line is a bit different to the others.
--- /hint ---
--- hint ---
Here's the updated code, if you're stuck:
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
emma+watson\"&tbm=isch", "Images"],
   "Neville" -> 
    Import["https://www.google.co.uk/search?q=\"neville+longbottom\"+\"\
matthew+lewis\"&tbm=isch", "Images"],
   "Luna" -> 
    Import["https://www.google.co.uk/search?q=\"luna+lovegood\"+\"\
evanna+lynch\"&tbm=isch", "Images"] |>]
```
--- /hint ---
--- /hints ---
--- /task ---
