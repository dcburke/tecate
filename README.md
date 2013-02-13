# Tecate.js

Writing HTML is hard. Let's go shopping

### Usage

You have an HTML file and you want to check if you made a mistake writing the
HTML tags. Drop `tecate.js` into the &lt;head> of your HTML document, like
this:

```html
<!doctype html>
<html>
    <head>
        <script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
        <script type="text/javascript" src="https://raw.github.com/kevinburke/tecate/master/tecate.js"></script>
        <!-- ... more files in the head ... -->
    </head>
    <body>
    <!-- ... the body content ... -->
    </body>
</html>
```

Then if there's a problem with your HTML, you'll start getting nice error
messages, like this:

<img src="https://www.evernote.com/shard/s265/sh/1d0ef423-e5de-4e40-a110-fad2ccd01bef/22bffc622af4152261b63184ad4b8cae/res/645f4d83-f8a8-45c7-8ec7-b2fc12b5e16d/skitch.png" alt="error message" />

### But you shouldn't put Javascript in the &lt;head>

[I agree][footer]. The problem is if you load the `tecate.js` file after, say,
an unclosed link tag:

```html
<a href="foo
<script src="tecate.js"></script>
```

It won't load properly and you'll never get the message telling you it didn't
load! That's why I recommend putting `tecate.js` in the &lt;head>

[footer]: http://stackoverflow.com/a/5329895/329700

### Catching Bugs

Tecate will display an error message straight to the page if you messed up your
HTML. Here are some of the bugs it can catch for you:

##### Missing a Closing Bracket

Say you forgot to end a tag with a bracket, or closed it badly:

```html
<div class="foo"
    Some text
</div>
```

##### Missing Equals Sign For Attribute

```html
<div class"foo">
    Some text
</div>
```

##### Missing Opening or Closing Attribute Quotes

These are some of the most pernicious.

```html
<div class=foo">
    <a href="blah>Some text</a>
</div>
```

##### Invalid Element Name

Say you mixed up your "m" and your "n":

```html
<form class="foo">
    <imput type="text" />
</form>
```
