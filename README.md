# star_struck
Space Tourism Multi-page Website Solution - Frontend Mentor Challenge

This is a solution to the [Space tourism website challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/space-tourism-multipage-website-gRWj1URZ3). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
# Frontend Mentor - Space tourism website solution
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)


## Overview

### The challenge

Users should be able to:

- View the optimal layout for each of the website's pages depending on their device's screen size
- See hover states for all interactive elements on the page
- View each page and be able to toggle between the tabs to see new information

### Screenshot

#### Mobile
![screenshot_mobileInterface_home1](https://github.com/Aperlae/star_struck/blob/main/assets/screenshot_mobileInterface_home1.png?raw=true)
![screenshot_mobileInterface_home2](https://github.com/Aperlae/star_struck/blob/main/assets/screenshot_mobileInterface_home2.png?raw=true)

#### Tablet
![screenshot_tablet_tech](https://github.com/Aperlae/star_struck/blob/main/assets/screenshot_tablet_tech.png?raw=true)

#### Desktop
![screenshot_desktop_destination](https://github.com/Aperlae/star_struck/blob/main/assets/screenshot_desktop_destination.png?raw=true)


### Links

- Solution URL: [Frontend Mentor](https://www.frontendmentor.io/solutions/responsive-multipage-website-using-cssgrid-jquery-utility-classes-pPsr8Qk1f)
- Live Site URL: [Space Tourism Website](http://space-tourism-website-mauve.vercel.app/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow

### What I learned

Once again I followed a tutorial to build this site [Kevin Powell / Scrimba](https://scrimba.com/learn/spacetravel).  It was great fun working with utility classes and although I wasn't always capable of completing all challenges, my own research and explanations provided by Kevin were of great help.  I learnt more about syntax and semantics in both HTML and CSS as well as some JQuery on which I still need to work.  I found the explanations on accessibility extremely interesting and I will keep using them going forward. 


I know it's a simple thing, but I really like how neatly this 'Skip to content' works.  I've often found tabbing around pages with screen reading technology a waste of time.  This saves precious minutes and it doesn't mess up the visual design of the page. 
```html
<a class="skip-to-content" href="#main">Skip to content</a>
```
```css
.skip-to-content {
    position: absolute;
    z-index: 999;
    margin-inline: auto;
    background: hsl(var(--clr-white));
    color: hsl(var(--clr-dark));
    padding: .5em 1em;
    transform: translateY(-100%);
    transition: transform 500ms ease-in;
}
.skip-to-content:focus {
    transform: translateY(0);
}
```

Here's one other piece of code that will be included in my pages from now on. **Bootstrap class sr-only** used to hide information that is only intended for screen-readers.
```html
<button class="mobile-nav-toggle" aria-controls="primary-navigation">
   <span class="sr-only" aria-expanded="false">Menu</span></button>         
```
```css
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap; /* added line */
    border: 0;
}
```

This **backdrop-filter** style looks absolutely lush although not supported by all browsers.
```css
.primary-navigation {
-webkit-backdrop-filter: blur(1.5rem);
backdrop-filter: blur(1.5rem);
}
/* Here's an easy fix example for those browsers that don't support it */
@supports not ((-webkit-backdrop-filter: blur(1.5em)) or 
(backdrop-filter: blur(1.5em))) {
    .primary-navigation {
        background: hsl(var(--clr-dark) / .85);
    }
}
```

Here's a function to help with **keyboard navigation** starting with changing focus on the tabs using the right and left arrow keys.

```js
const tabList = document.querySelector('[role="tablist"]');
const tabs = tabList.querySelectorAll('[role="tab"]');

tabList.addEventListener('keydown', changeTabFocus);

let tabFocus = 0;
function changeTabFocus(event) {
    const keydownLeft = 37;
    const keydownRight = 39;
// changing tabindex of current tab to -1 //
    if (event.keyCode === keydownLeft || event.keyCode === keydownRight) { 
        tabs[tabFocus].setAttribute("tabindex", -1); //removes focus when keydown takes place//
// if right key is pushed, move tab to right //        
        if (event.keyCode === keydownRight) {
            tabFocus++;
            if (tabFocus >= tabs.length) { //cycles through the tabs with right key//
                tabFocus = 0;
            }
// if left key is pushed, move tab to left // 
        } else if (event.keyCode === keydownLeft) {
           tabFocus--;
            if (tabFocus < 0) { //cycles through the tabs with left key//
                tabFocus = tabs.length - 1;
            }
        }
        tabs[tabFocus].setAttribute("tabindex", 0); //puts focus on next tab//
        tabs[tabFocus].focus();
    }           
}
```

If you want more help with writing markdown, we'd recommend checking out [The Markdown Guide](https://www.markdownguide.org/) to learn more.


### Continued development

I will definately continue focusing on accessibility in future projects.  
Read more about the use of **ARIA** roles, states and properties.
Make a habit of writing a general reset and use general utility classes that work with components and custom properties.
I need more practice with javaScript and JQuery as they're still pretty confusing at times.


### Useful resources

- [Stackoverflow](https://stackoverflow.com/) - Always find answers here ...
- [W3Schools](https://www.w3schools.com/default.asp) - And here ...
- [CSSTricks](https://css-tricks.com/archives/) - here  too ...
- [MDN Web Docs](https://developer.mozilla.org/en-US/) - yep ...
- [Piccalill-Andy Bell](https://piccalil.li/blog/a-modern-css-reset/) - This modern CSS reset came in handy and will again for sure.
- [WebDev](https://web.dev/prefers-reduced-motion/) - An interesting article on reducing animations for users who express this preference.
- [SmashingMagazine](https://www.smashingmagazine.com/2021/03/complete-guide-accessible-front-end-components/) - Handy guide to have!  



## Author

- Frontend Mentor - [@Aperlae](https://www.frontendmentor.io/profile/Aperlae)
- LinkedIn - [@Monique](https://www.linkedin.com/in/monique-parnis-89902722a/) *new profile under construction* 


## Acknowledgments

- [Scrimba](https://scrimba.com/allcourses) - Thanks to Per I learned a little bit of JS and with the help of Kevin is finished this challenge.


