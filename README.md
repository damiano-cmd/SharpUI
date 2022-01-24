# SharpUI

This is my custom ui bundle what I use.

## Use
There are 5 components: 
  - NavBar (Just a navbar)
  - Numbers (Numerator for pages has next, back, to end, to begining buttons)
  - Options (Dropdown menu with custom options)
  - Search (A search bar)
  - Switch (It's a custom switch)

All components have two shared attributes:
  - thm - the theme of the component, curently there are only two: "dark" and "lite". Default is dark.
  - _class - it applies a global class to the element. 
    If this field is filled the thm filled wont applie by default if it is not manually specified.

## Here are the components custom attribs:
- Nav, navigation bar that allows items to be placed in it. The arguments are:
  - layout - the layout of the navbar can be: flex or grid. By default flex.
    This filled will not be applied by default if the _class attrib is specified. 
  - grid-temp - assignee the css `grid-template-column` the the grid layout (only works when the layout is grid).
  - positions - the css `position` for navbar, options are sticky and fixed.
    This filled will not be applied by default if the _class attrib is specified. 

- SearchBar just a simple search bar with dark and lite themes. Can not displatch any data curently, it is not functional. Attributes are:
  - bind:value - the curent text is in the bar.
  - on:enter - a dispatch function that dispatches when the search input form is submited.

- Switch, it is just a custom switch, bind value is `is_switched`. Attribs:
  - label - the name that is displayes next to the switch.
  - bind:is_switched - shows is it switched.

- Numbers, a pages list for multy page apps. Is not functional jet. Attribs:
  - showing - number is pages to display on the pages list. Attribs:
  - curent - the curent page.
  - maximum - the maximum number page that it can't go over.

- Options, an options element. Attribs:
  - options, you put the array of document objects (like this `[ {text: "hello"}, {image: "/..."}]`) in here that will get displayed as options on the menu. 
      The main values are:
      - text - to the display text on you option.
      - image - displays a little image on you option.
        They display in the order that you put them in.
      You can put any other value in here that you want, but those two are the ones that are gonna be displayed.
  - bind:value - is the curently selected options (json document that hold the values you want).

