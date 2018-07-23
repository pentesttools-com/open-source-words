jQuery-menu-aim menu-aim is a jQuery plugin for dropdown menus that can differentiate between a user trying hover over a dropdown item vs trying to navigate into a submenus contents. Try a demo. This problem is normally solved using timeouts and delays. menu-aim tries to solve this by detecting the direction of the users mouse movement. This can make for quicker transitions when navigating up and down the menu. The experience is hopefully similar to amazon.com/s "Shop by Department" dropdown. Use like so: $("#menu").menuAim({ activate: $.noop, // fired on row activation deactivate: $.noop // fired on row deactivation }); ...to receive events when a menus row has been purposefully (de)activated. The following options can be passed to menuAim. All functions execute with the relevant rows HTML element as the execution context (this): .menuAim({ // Function to call when a row is purposefully activated. Use this // to show a submenus content for the activated row. activate: function() {}, // Function to call when a row is deactivated. deactivate: function() {}, // Function to call when mouse enters a menu row. Entering a row // does not mean the row has been activated, as the user may be // mousing over to a submenu. enter: function() {}, // Function to call when mouse exits a menu row. exit: function() {}, // Function to call when mouse exits the entire menu. If this returns // true, the current rows deactivation event and callback function // will be fired. Otherwise, if this isnt supplied or it returns // false, the currently activated row will stay activated when the // mouse leaves the menu entirely. exitMenu: function() {}, // Selector for identifying which elements in the menu are rows // that can trigger the above events. Defaults to "> li". rowSelector: "> li", // You may have some menu rows that arent submenus and therefore // shouldnt ever need to "activate." If so, filter submenu rows w/ // this selector. Defaults to "*" (all elements). submenuSelector: "*", // Direction the submenu opens relative to the main menu. This // controls which direction is "forgiving" as the user moves their // cursor from the main menu into the submenu. Can be one of "right", // "left", "above", or "below". Defaults to "right". submenuDirection: "right" }); menu-aim assumes that you are using a menu with submenus that expand to the menus right. It will fire events when the users mouse enters a new dropdown item and when that item is being intentionally hovered over. Want an example to learn from? Check out example/example.html -- it has a working dropdown for you to play with: Play with the above example full of fun monkey pictures by opening example/example.html after downloading the repo. FAQ Whats the license? MIT. Does it support horizontal menus or submenus that open to the left? Yup. Check out the submenuDirection option above. I work at a big company that requires a version number on this third party code before I can use it. Do you have a version number? Sure, current version: 1.1 Im not nearly bored enough. Got anything else? Read about this plugins creation.