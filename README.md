# Cozy Coloring

A one-page website about adult coloring books and tools, built with Bootstrap 5 for the "Custom Website with Frameworks" assignment.

- **Live site:** [https://wynoami.github.io/cozy-coloring-custom-website-bootstrap-assignment-week-5-wynoami-g/#shop]
- **Repository:** [https://github.com/wynoami/cozy-coloring-custom-website-bootstrap-assignment-week-5-wynoami-g.git]

## Bootstrap components used

Every component works from Bootstrap's `data-bs-*` attributes. There is no custom JavaScript in this project.

| Component | Where it is | Requirement |
|---|---|---|
| Carousel | Hero at the top of the page | Required |
| Modal | "See the starter kit" buttons | Required |
| Accordion | Beginner questions | Required |
| Tabs | Shop section (pencils, markers, gel pens, books) | Custom component 1 |
| Scrollspy | Highlights the current section in the navbar | Custom component 2 |
| Dropdown | "Learn" menu in the navbar | Extra |
| Collapse | Mobile navbar menu | Extra |

## Files

- `index.html`: page structure and Bootstrap components
- `styles.css`: colors, fonts, and the two styles utilities can't do
- `README.md`: this file and the write-up

## Write-up

Nesting the HTML components was probably the most challenging part for me. I found myself needing to go back a few times to realign the code so that it was nested inside of the appropriate tags. And spelling errors always get me in the end.

Scrollspy was also a challenge.

Changing the color palette was far more challenging than expected. 

### Custom CSS that couldn't be replaced with framework utilities

Colors and fonts were one of the few places we could be creative, so I went with a custom palette and font family to suite the vibes of a coloring site: cozy and friendly. 

`scroll-padding-top: 6rem on html:
when you click a nav link like #shop, the browser scrolls so the top edge of that section lines up with the top of the screen. Your header is sticky-top, so it sits on top of that spot and would cover the section's heading. scroll-padding-top tells the browser to leave a 6rem gap at the top when it scrolls to an anchor, so the heading lands just below the header. It also applies to the "Skip to content" link and any other # link.

Why no Bootstrap utility covers it:
Bootstrap 5.3 has no scroll-padding or scroll-margin utilities. Its spacing utilities (p-*, m-*) change an element's own padding or margin, not where the browser stops when it scrolls.

A zero-CSS alternative:
drop sticky-top from the header. The header would scroll away with the page, so nothing would be covering the headings. The cost is that the nav is no longer always visible, and Scrollspy is less useful when the nav scrolls out of sight.

`.hero-slide { min-height: 65vh; }:
65vh means 65% of the browser window's height. Each carousel slide gets at least that much height, so the hero is a large banner on any screen size. It also stops the page from jumping. Without it, each slide is only as tall as its text, and the slides have different amounts of text. When the carousel auto-advances, the height changes and everything below it shifts up or down.

Why no BS utility covers it:
* min-vh-100 and vh-100 are the only viewport-height utilities, and they mean the full screen height. That would make the hero fill the entire window, with the header on top pushing the bottom edge below the fold.
* h-25, h-50, and h-75 are percentages of the parent's height. The parent here has no set height, so they would do nothing.
* The ratio helper (like ratio-16x9) keeps a fixed shape, but on a narrow phone a 16:9 box is too short for the text, and Bootstrap has no responsive ratio classes to fix that.
* Bootstrap can generate a custom min-vh-65 class, but only through its Sass Utilities API, which needs a build step. That doesn't work when you load Bootstrap from a CDN, as this assignment requires.

A zero-CSS alternative:
use min-vh-100 on each slide's wrapper. It's simpler, but the hero becomes full-screen, which is a bigger design change.

### Most challenging component

Discovering exactly which colors I could override and which I needed to work around was a challenge. I had to write a new set of variables to cover things like the buttons, nav pills, and the dropdown's active items. 

Classes like tes-bg-primary force white text which is unreadable on lavender and pastel colors. I worked around it by using bg-* classes, which leave the text dark, and by avoiding text-primary. 

Peach and blush don't correspond to any Bootstrap theme color, so they're custom classes. 

### Easiest component

The Accordion worked from copy-and-adapt markup. I change the question and answer text and keep the Bootstrap's structure.

### How the framework improved my code

I appreciated the structure it provided. I love how small the CSS file is, even with my changes. 

### Framework features I liked or disliked

Recoloring was a chore. The hard-coded blue into so many components is not fun. and the pastels clashwith some built-in classes. There was nothing for scroll padding and no min-vh-65 so the utilities for everything idea has gaps. 

## Testing checklist

- [ ] Hosted on GitHub Pages
- [ ] Works in Chrome, Firefox, and Safari
- [ ] Fully responsive (phone, tablet, desktop)
- [ ] Every component works on desktop and mobile
- [ ] Custom CSS is small, with no duplicate styles
- [ ] Code is commented and organized
- [ ] Write-up is complete

## Credits

- [Bootstrap 5.3](https://getbootstrap.com/) via CDN
- Fonts: [Fredoka](https://fonts.google.com/specimen/Fredoka) and [Nunito](https://fonts.google.com/specimen/Nunito) from Google Fonts
- Pastel palette based on a common pastel rainbow set
