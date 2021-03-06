# LaReveladora
**LaReveladora** is a project forked from [Reveal.js] (http://lab.hakim.se/reveal-js/#/), intended for people who need to create presentations on a regular basis. 
It has three main differences with a regular Reveal installation:
* Instead of downloading instances of Reveal library for each project it has a common folder with only an instance of Reveal.js and a folder of projects, managed by [Gulp](http://gulpjs.com/) tasks. 
* Instead of coupling data and representation in the `index.html` as Reveal does this flavour takes advantage of mighty [pandoc](http://pandoc.org/) (as a [node module](https://www.npmjs.com/package/gulp-pandoc), handled by Gulp) to have a markdown file with the data, `index.md`. This design makes easy to maintain the data and code (and, no way, who doesn't prefer markdown to html?). To do that it uses a template file, `template.html`, forked from [this gist](https://gist.github.com/aaronwolen/5017084).
* It's intended to be used with [Sass](http://sass-lang.com/). And if you don't know Sass yet, go right now and learn about it.

## Installation
To install it, clone it with a `--recursive` flag on, to enable the cloning of Reveal (contained as a submodule of LaReveladora):
```sh
git clone --recursive https://github.com/Ale-/LaReveladora
```
If you don't have node install it:
```sh
curl -sL https://deb.nodesource.com/setup | sudo bash -
sudo apt-get install -y nodejs
```
Install Gulp dependencies:
```sh
sudo npm install
```
And you're done!


## Usage

### Create your first project:
```sh
gulp create --n project-name
```

This command creates a project of name 'project-name', in projects folder, and updates 'index.json' with project's info. That file is readed by index.html to create a summary of the projects.

### Modify the data

To update contents you have to update `index.md`, that uses markdown as markup language. To create the structure of the document follow these simple rules:

* Each `# (h1)` will be considered a slide in the compiled `index.html`:
```md
# First slide
My content

# Second slide
Another content
```
* To create a vertical layout, embed `## (h2)` under a common title:
```md
# Common title for my vertical layout

## First slide in the stack
Content

## Second slide in the stack
Content
```

### Compile the results

Now it's time to see the results. You've to compile `index.md`. In order to get that, we use pandoc, following the template defined in `template.html`. This operation creates a proper `index.html` file to hold the slideshow.

```sh
gulp compile --n your-new-slideshow-project-name
```

You can also watch the changes in the file (with liveReload enabled) :
```sh
gulp watch --n your-new-slideshow-project-name
```

### Give some nice style

There's a gulp task to compile sass:

```sh
gulp sass --n your-new-slideshow-project-name
```
