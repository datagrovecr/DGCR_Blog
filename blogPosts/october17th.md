# Creating my first website with Vitepress
 Date: 10/16/2022

Developer: Raquel Abarca Espinoza

### Project name: [Datagrove blog website](https://github.com/datagrovecr/datagrove_blog_website)

#### Goal: An interactive website for sharing blog posts about Datagrove development projects.

### What is Vitepress?
It is said that VitePress is VuePress little brother.

A static website is made up of one or more HTML webpages that load the same way every time. Static webpages are simple HTML files that can load quickly, and the dynamic webpages require the execution of JavaScript code within the browser in order to render.

A static site generator automates the task of coding individual HTML pages and gets those pages ready to serve to users ahead of time, because these HTML pages are pre-built, they can load very quickly in users

So, VuePress is a combination of a minimalistic static site generator, little brother.

> #### What are the improvements that difference Vitepress from VuePress v1:
> - Faster server start
> - Faster build
> - Lighter page weight
>
> #### Other differences:
> VitePress is more opinionated and less configurable.
> VitePress is future-oriented: VitePress only targets browsers that support native ES module imports. It encourages the use of native JavaScript without transpilation and CSS variables for theming.
> You can find more info here: https://vitepress.vuejs.org/guide/what-is-vitepress

### What specifically do I use vitepress for?
I am using Vitepress to specifically work on creating a website, with only Vitepress I have the chance to create and design a functional site, in my case, a blog site in which the developers can upload their own blogs with information about what are they working on, how they solved a problem or any other ideas or documentation regarding their work.

This website will be for Datagrove CR, and my inspiration is from the [Vue blog](https://blog.vuejs.org/) that is also built with VitePress, this site use Vitepress and other element and languages like css, but the idea for now is only use Vitepress and markdown for the blog site.
![image](https://user-images.githubusercontent.com/110420288/196104431-971f6b47-53e8-4735-a3de-33e1b8433a4e.png)

### Challenges I have faced

Understanding what is Vitepress, how it works and learn how to use it. 

- Creating a project from scratch was complicated, because I had never created one, so I didn’t know which files I had to add, like the `.gitignore`.
- Understanding the code, so I tried to study, practice and test different code from different websites.
- Finding other variations of code to try when code from the guides doesn't work, for example, in the [guide](https://vitepress.vuejs.org/guide/theme-nav), the way to change the title of the page was with `siteTitle: ‘My Custom Title’`, but that did not work for me, so I checked how that was done on the [DatagroveCR website](https://github.com/datagrovecr/website/blob/main/docs/.vitepress/config.js) and I saw that this site only used `title: My Cusom Title`.
- I also had problems running the `npm run docs:dev`, first of all, because I always had use only `npm run dev`, but in this repository, it is necessary to use `docs:dev`, this because it is declared with that name in the `package.json`.
- Every time that I closed the code and then went to run it on another day the website showed an error or just a white page.I am working to solve this, but I think that the problem was that I did not add the basic files and packages. 

<img width="304" alt="image" src="https://user-images.githubusercontent.com/110420288/196098778-b15b97c5-2a59-4905-85bc-d4c0c5282215.png">

I am working on solve this, but I think that the problem was hat I did not add the basic files and packages. 

### Things that I learned
First of all I learned about Vitepress, the code to add images, logos and to change the title of the website.

Also, I learned that Vitepress only really needs markdown to create a nice basic site. For example with this markdown as my index.md I already have a nice looking site.
```
# Welcome
# To Datagrove Blog

### What you can find here?

In this website you will find blog post that our developers upload about what they learn, problems that they solve, and updates about their projects.

## Understanding OpenXML SDK
[Read more ->](blogpost\fabianmonday10th.md)

## Blog post temple

[Read more ->](blogpost\templeblog.md)

```

I learned that there are different types of menus that Vitepress offers to the developer, in my case I used this menu that allows navigation to different pages when you put this code in the `.vitepress\theme\config.js` file:
```
import { defineConfig } from 'vitepress'

export default ({

    title: 'Datagrove Blog',
    description: 'Software That Does Good',

    themeConfig: {
        
        logo: '/bright_green_circle.png',

        nav: [
            { text: 'Home page', link: '/index' },
            {
              text: 'Menu',
              items: [
                { text: 'Item A', link: '/item-1' },
                { text: 'Item B', link: '/item-2' },
                { text: 'Item C', link: '/item-3' }
              ]
            }
          ],

      }
})
```
Finally I learned that the order and structure of the files actually matters, my file (for now) looks like this:

<img width="196" alt="image" src="https://user-images.githubusercontent.com/110420288/196102138-f5628c4c-84e2-4d63-9577-4c42536dd8cc.png">

You can see that it’s important to maintain order and readability, so that you can find your files. However, in addition to this, it is important because if the root of the program is missing a required file, the entire program will fail.

### Links with more info:

#### Markdown: 

https://paperhive.org/help/markdown

https://www.markdownguide.org/basic-syntax/

https://anvilproject.org/guides/content/creating-links

#### Vitepress:

https://vitepress.vuejs.org/

https://javascript.plainenglish.io/write-beautiful-documentation-quickly-with-vitepress-a0cc4e6d25

https://www.npmjs.com/package/vitepress

Example: https://blog.vuejs.org/

### List of tags

`typescript` `markdown` `blog` `datagrove` `vitepress` `website` `basic` `challenge` `project`
