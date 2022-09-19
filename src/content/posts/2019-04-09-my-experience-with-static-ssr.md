---
template: blog-post
title:  "My Experience with Static SSR"
date:   2019-04-08 22:00
slug: /my-experience-with-static-ssr
description: Coming Soon
---

Recently I have been creating websites in a statically generated way on a server, this being referred to as Static SSR (Server Side Rendering), where a server essentially generates HTML files based on code written, then those files are served to the user.

There are two main reasons I initially delved into static SSR, the first was due to frustration in using Jekyll, which is currently as of writing is the framework my blog is on, made by GitHub it is a way drop simple markdown files into a folder and let everything else generate, simple. Well, one of many initial issues was getting third-party plug-ins to work being hosted on GitHub (which is free), which long story short is not allowed, then the second issue was no styling being applied to the blog when moved over, again (long story short) the "baseurl" needs to be set in the config file.

Then second was to re-create my portfolio (again), which I wanted to do wth JSON (instead of markdown), rather than creating every page (or use a builder, since I like writing HTML/CSS/JavaScript). Although, this was just before I knew of the term SSR and the capabilities of Netlify.

## Quick MVP

Before creating anything, I wanted to see how simple it would be to create a statically generated website, so using NodeJS (my language of choice) and its fs (file system) module, I created what can be seen in this [GitHub Repo](https://github.com/Sean12697/simple-static-site-generator){:target="_blank"}. It's fairly basic and is used for demonstration purposes, but has the core principles of what was to become my current portfolio, a json object, custom string interpolation (concatenation) templating and `fs.writeFileSync()`.

## Jekyll in NodeJS

For fun, before re-creating my portfolio, I thought I would try to recreate the core principles of Jekyll, where a user could put markdown files into a `_posts` directory and have it generate everything for them.

This was not too difficult to achieve, where I did the majority of within a few hours one Sunday night, since I was using an npm package (kramed) to convert the actual markdown into HTML, then the actual default Jekyll theme for mine (which I split into the core components).

The GitHub Repo being [JekyllJS](https://github.com/Sean12697/JekyllJS){:target="_blank"}, then it also being deployed on [Netlify](https://zealous-jang-b5c7b4.netlify.com/){:target="_blank"}.

Although, there were a few key learning points that I should share, the first being always ensure you know where the root is, meaning if you're on index.html and go further in the site (into another folder), if your templates just have links to `./style.css` when you go to another folders html it will break, since there will likely not be a `./style.css` file (`../style.css` instead).

This can be seen when I use a `toRoot` variable in my Jekyll Clone's templates, which is my second learning point. Any reusable elements of HTML, often being referred to as components in popular JavaScript libraries, I store in a `_modules` folder, mainly being the head (with meta data), header and footer, then whole templates are stored in a `_layouts` folders (just a convention).

Then the last two/three points are to do with folders/file, the first being if a folder doesn't exist for the fs module to create a file in, it will just fail. Due to this I use an npm package called `shelljs`, with this I can run `.mkdir('-p', './_site')` to always ensure that the folder is there, along with `copy-dir` to ensure static files like images are where they belong (`copydir.sync('./_static', './_site')`). Then the second point is the files that go in, I want to name the HTML files are their title, although not includes spaces and special characters, which is why I use regex to change all non-alphanumeric characters to dashes (with a function I can reuse).

## Portfolio (v4)

With the above knowledge I was set to create the fourth iteration of [my portfolio](https://seanomahoney.com/){:target="_blank"}, using the same index theme to its third iteration (being based of Spotify, since I love music), along with improving performance along the way (which static ssr helps with, that I cover in my talk), which I still thank [Harry Roberts](https://twitter.com/csswizardry){:target="_blank"} for and his "Front-end Performance" workshop (with 300+ slides that we got to keep).

### Tags

Having tags on each item of my portfolio, each project, I can use handy JavaScript ES6 functions like map/filter/reduce to generate lists of items with certain tags (using the tags defined in all items), showing off what skills I most frequently use and most importantly where I have used them.

### Meta Descriptions (SEO)

Due to having the text for each item, I can easily pass that into the head module I create for a generated page, meaning the meta description of a project will match the main content of its page.

### GitHub Repo Listing

Using the `@octokit/rest` npm package, I can easily interact with the GitHub API without having to supply a token to retrieve a list of all my pubic GitHub repo, which using my templates and the `language` property, I can create lists of every repo corresponding to a particular programming language.

### Minify

Using npm's `minify` package, I wrote this simple function below that will overwrite an existing files content with a minified version, that being a version with all comments/spaces removed and generally made smaller.

```javascript
function minifyFile(fileLocation) {
    minify(fileLocation).then(minified => fs.writeFileSync(fileLocation, minified, () => { }));
}
```

### Blog Post Listing

My blog having a site map, allows me to use the `node-fetch` npm package to simply fetch that xml into my code, then with the `xml-js` package I can simply convert this to JSON and traverse it to generate my blogs listing.

Although, similar to when I was converting titles/names into suitable file names, I created a function to do it in reverse (kinda), this will turn all dashes into spaces and then all words into capitalised versions.

```javascript
function urlToText(url) {
    return url.split('/').slice(-1)[0].replace('.html', '').split('-').map(word => word.charAt(0).toUpperCase() + word.substr(1)).join(' ');
}
```

### Sitemap

For SEO purposes creating a sitemap is ideal, and was easy to implement, along with writing a file for everything, I also pushed a link to where it is into an array, which at the end of writing all the html files, I could call the following function I created.

```javascript
function rtnSiteMap(array) {
    return `
    <?xml version="1.0" encoding="UTF-8"?>
        <urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
            ${ array.reduce((pre, curr) => pre += '<url><loc>' + curr.url + '</loc><priority>' + curr.priority + '</priority></url>', "")}
        </urlset>`;
}
```

### SVGs / Objects

Vector Graphics are amazing for performance, they can be as little as 2kb and be everything you want, although loading them from a file can be a bit of a pain, especially if you're unsure if they'll exist (since with a template you don't want to hard code any exceptions).

Due to this I initially just used Object elements, which did have fallbacks, although after inspecting the Chrome Dev Tools, I found it still tried to load them and showed errors in the console log, which was an issue.

Due to this I wrote the following function which would first check if the file exists, then return the object elements for it, if not then it would just return an empty paragraph.

```javascript
function getSVG(fileName, toRoot, title) {
    try {
        if (fs.existsSync('./_site/assets/svg/' + fileName + '.svg')) return `<object data="${toRoot}/assets/svg/${fileName}.svg" type="image/svg+xml"><p>${title}</p></object>`;
    } catch(err) {
        return "<p></p>";
    }   return "<p></p>";
}
```

### Font Loading (Performance)

The main performance issue I has was my TTI, Time to Interactive, due to linking fonts to another server a browser would have to make a separate request and wait on it until the pages load function was triggered.

Because of this, I removed the font faces that I was using on another server, and added a cheeky little script at the bottom of my footer module. With this small script, the page would load fast initially with a sans-serif font, but once the page had loaded, triggering the windows load function, it would then download and render the fonts afterwards, letting the user see the content quickly.

```javascript
window.addEventListener('load', () => {
    let fonts = document.createElement("link");
    fonts.type = "text/css";
    fonts.rel = "stylesheet";
    fonts.href = "${toRoot}/fonts.css";
    document.body.appendChild(fonts);
});
```

### Scroll Snapping

In the past I have tried to implement scroll snapping nativly in CSS, although had ran into compatabily issues previously, although adding `@supports (scroll-snap-align: center) and (scroll-snap-type: x mandatory)` around the attempted implementation in CSS, then following a blog post by Xander Gottlieb I had with [the right padding problem](https://blog.alexandergottlieb.com/overflow-scroll-and-the-right-padding-problem-a-css-only-solution-6d442915b3f4){:target="_blank"}, I was able to finally implement it (which can be seen in the mobile version of my portfolio).

## Workshop (Creating Your Own Static Website Generator)

Feeling inspired to show others how cool and optimised Static SSR is, I thought I would do a workshop/talk on it, first being ran at CodeUp Manchester, where I ended up creating this [GitHub Repo](https://github.com/Sean12697/codeup-static-ssr-demo){:target="_blank"}, it mostly went to plan, although in simplification the issue arose of the `fs` module not finding the `./_site` folder, due to it being blank and Git not adding it to the repo due to that fact (next time I will use `shelljs`).

The slides for then can be seen on [SlideShare](https://www.slideshare.net/SeanOMahoney3/creating-your-own-static-website-generator){:target="_blank"}, and the next time I will be running it will be at the [Manchester Web Meetup](https://www.meetup.com/Manchester-Web-Meetup/events/260446380/){:target="_blank"} on the 17th of April, which will be less of a workshop and more of a talk on performance (especially verses Client Side Rendering, which React and Angular are examples of).