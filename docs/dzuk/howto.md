
# Main arguments

The arguments you could use in any type of Orxporter command.


## Input (`-i`)`

The folder where the source images are located.

## Output (`-o`)

Where forc outputs to.

## Manifest (`-m`)

A file where you set all of your emoji metadata.

Documentation on manifests coming soon.

[How to use SVG and EXIF metadata in your manifest (optional)](metadata.md).


## Filter (`-e`) (optional)

Set a conditions for what emoji in your input will actually get exported. Useful if you just want to export a slice of what you've got in your input and manifest.


---

# Image output

The arguments and flags to use for image output:

## Formats (`-F`)

[Check out this doc](image_formats.md) for a list of the supported formats and how to type them.

You can put multiple formats in this flag in a comma-separated list like this:

````
-F svg-69,flif-420,png-666,png-128
````

## Directory and filename structure (`-f`) (optional)

This is a way of fiddling with the way that your output files are named and what folder structure they will be stored in.

[Check out this doc](file_structure.md) for the kinds of things you can do.


## Renderer (`-r`) (optional)

This is how PNGs are produced (either standalone or for other formats like WebP and FLIF).
Depending on what you have installed on your computer, you can choose:

- `inkscape` (requires inkscape)
- `imagemagick` (requires ImageMagick)
- `resvg` (requires resvg)

*(check the [readme](../../readme.md) for all the information on dependencies)*

Based on our experiences, we highly recommend resvg (unless you need fancy SVG support like filters) because it is much faster than the others.


## Cache (`-C`) (optional)

Set a directory as a cache. When a cache is set, Orxporter will store a keyed copy of all of your exported emoji there, so when you export again, Orxporter will only export the images that have changed or are in formats that it hasn't exported before, saving you a lot of time on repeat exports or publishing emoji set updates.

(Make sure you point to the same cache directory when re-exporting with a different command or script!)

## Export without metadata embedding (`-l`) (optional)

If you have [specified metadata for embedding in your manifest](metadata.md), metadata
will be automatically embedded in compatible image outputs.
Using this flag will stop Orxporter from doing that.


-----

# Data output

The argument to use for JSON metadata output:

#### JSON export (`-j`, `-J`) (optional)

Compile the metadata you've set in .orx files into a JSON file for web and other applications.

Filters done with `-e` still apply to this export.

Using this means that you're just exporting JSON for this command, you can't use the image-related stuff here.

- `-j`: JSON file with a flat structure.
- `-J`: JSON with a specific format expected by the Mutant Standard website (lol)

----


### Extra flags

#### Force Text Descriptions (`--force-desc`)

Makes Orxporter complain if there are any emoji with missing text descriptions.


#### Check SVG image size (`-q`) (optional)

Check the size of your input SVGs' `viewBox` attribute to make sure there are no input emoji with the wrong size.

This won't work if your input SVGs don't have this attribute.
