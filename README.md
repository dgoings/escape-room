# Developer Escape Room

This is a small web app that forms part of a programming-themed escape room as described [here](spin.atomicobject.com).
It is designed to be easily deployed to a platform like Heroku or even just run on a local network.

## Building

The app is just a simple express server with a websocket component.
This file is written in Typescript, and the app can be compiled with `npm run build`.
To run the app locally, use `npm run start`.

Most of the rest of the app are just `/public` files that don't need any pre-processing to keep things simple.

The countdown timer library comes from http://www.flipclockjs.com/
Basic css styling from [Bootstrap](https://getbootstrap.com/)

## Notes on Setup and Personalization

Before launching this app to run your own escape room, there are some configuration details and changes you may need to make. Here is a rundown on all the customizations to consider.

### The Color Grid

The `public/color-grid.html` page displays a grid of 20 different hexidecimal colors, and clicking on any color block reveals a number. For one of the escape room puzzles, three of these colors need to match up with the numbers that unlock a combination lock. Make sure to edit the `colorsArray` on lines 45-66 so that the correct colors reveal the correct numbers for the lock. The other colors can reveal any random numbers you choose and should all be composed out of six possible 2-character hexidecimal numbers, which will match the numbers used in the escape room.

### The Countdown clock

The `public/index-but-not-really.html` page shows the clock that counts down the remaining time for participants to solve the escape room. Line 47 sets the initial time on the clock in seconds (defaults to 30 minutes), make sure to adjust this if you want to give your group more or less time to solve the room, as well as the matching time on line 65.

The switch statement on lines 52-67 define the codes being listened for to start/stop/reset the clock. The file name is chosen to keep participants from discovering the page on their own, since the escape room will link them to other pages like the color grid, and smart participants could think to check the source code of this page to cheat the solving of the puzzles. This might actually be a feature, in which case feel free to rename this file to just `index.html`. Alternatively the javascript code could be moved to its own file and imported.

The actual start/stop/reset codes can be anything you want, but the specific stop code on line 56 should be set to something fun, since this is what participants will be typing in to solve the escape room.

### The Admin page

The `public/for-admin-eyes-only.html` page is for you to remotely control the countdown clock. When participants enter the room, you can press the start button, and use the reset button for the next group. Make sure to change the codes on lines 39, 44, and 49 to match whatever you set on the `index-but-not-really.html` page.

Again, this page should not be easily discoverable by participants. Consider changing the filename to something else before running your escape room.

### The Passcode page

The `public/super-secret-control.html` page is where participants should ulimately land to finish the escape room. You don't need to change any code here, but this page will be linked to as part of the escape room and shouldn't be easily discovered by participants. Feel free to rename the file to something else fun and relevant.
