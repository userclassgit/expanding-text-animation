<h2>Text Expansion Animation</h2>

In this tutorial, I will teach you how to create [this](https://userclassgit.github.io/expanding-text-animation/) cool animation where the text expands and reveals more letters when you hover over it.

Let’s take a look at the HTML code first. Write the ```h2``` elements and make sure there are 2 ```span``` elements inside each ```h2```. In the first ```span```, you want to write the first letter of the word; In the second ```span```, write the rest of the letters in that word.

````markdown
<body>
    <h2><span>C</span><span>ascading</span></h2>
    <h2><span>S</span><span>tyle</span></h2>
    <h2><span>S</span><span>heets</span></h2>
 </body>
````

Now, let’s go to CSS and do some basic styling for the page.

```css
:root {
    --text-color: #2ae6ff;
}


body {
    font-family: Arial, Helvetica, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-color: #001f25;
}
```

Next, we style the ```h2``` element. Note that it is important to add a fixed height to this element because without it, after you’ve written all the code, you’ll find that the elements sometimes “jitter” when you hover over them. After you’ve finished following the tutorial, you can comment out the height property at the bottom of the below code snippet and see what happens. This will help you understand why having a fixed height here is essential.

```css
h2 {
    font-size: 6rem;
    color: transparent;
    -webkit-text-stroke: 2px var(--text-color); 
    text-transform: uppercase;
    cursor: default;
    line-height: 1em;
    height: 1em;
}
```

After styling ```h2```, target and style all the spans within ```h2```. Give it a cool drop shadow using the filter property. Make sure ```display``` is set to ```inline-flex```. You will see why this is important soon.

```css
h2 span {
    display: inline-flex;
    filter: drop-shadow(0 0 15px var(--text-color));
}
```

We then target and style the 2nd ```span``` in ```h2```. set the overflow property to hidden. ```overflow: hidden```,  ```letter-spacing: -1em```, and```display: inline-flex``` which you saw in the above code snippet effectively hide the 2nd ```span``` in ```h2```. In other words, they hide all the letters except the first letter in each ```h2```. Make sure you add a ```transition``` to ```letter-spacing``` so that we have a smooth animation when the value of ```letter-spacing``` changes.

```css
h2 span + span {
    overflow: hidden;
    letter-spacing: -1em;
    transition: letter-spacing 0.5s ease-in-out;
}
```

Finally, we configure what happens to the 2nd ```span``` in ```h2``` when you hover over ```h2```. Here, instead of having a negative value for letter-spacing, we want it to be 0. This will make the text expand and show the hidden letters when we hover over it.

```css
h2:hover span + span {
    letter-spacing: 0;
    color: var(--text-color);
}
```

And that’s how you create this cool text expansion effect. I hope you find this tutorial informative and helpful.