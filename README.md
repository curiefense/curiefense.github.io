## Local setup


* install Jekyll by executing following in terminal
  
  `gem install bundler jekyll`
  
* Clone/download the repo
* Navigate to repo via terminal and execute following

  `bundle install`

  `bundle exec jekyll serve --livereload`
  
  this will start a local server on port `4000`. Go to a browser and access http://localhost:4000
  
* To only build the project execute `bundle exec jekyll build` and the project will get built inside `_site` folder
  
## Netlify setup


* When setting up this repo on netlify, make sure to have following as deployment settings

    **Build command:** `jekyll build`

    **Publish directory:** `_site/`

## Hello-Bar Setup and Customization

* The required script and configurations are added in `footer.html`
* The complete information about Hello-bar can be found [here](https://github.com/AnandChowdhary/hello-bar#customization)
* These are all the options you can use in the constructor:

```js
new HelloBar({
  id: "", // A unique ID for this hello bar content (required for targeting)
  text: "", // Text you want the banner to display
  hideClose: false, // Set to `true` to hide close button
  position: "top", // Set to "bottom" to have the bar in the bottom instead of top
  fixed: false, // Set to `true` to set the position as fixed (on scroll)
  move: null, // Element(s) to force add margin-top to, in case you have any absolutely positioned elements
  duration: 500, // Animation duration in ms
  delay: 1, // Delay in ms
  align: "center", // Text alignment in CSS ("left", "right", or "center")
  background: "#eee", // Background color
  textColor: null, // Black or white text is automagically determined; you can specify a color if you like
  size: "normal", // Set to "large" for a big banner like Hello Bar,
  multiline: false, // Set to true to have multiple lines of text
  disableBodyMove: false, // Set to true to not move the body slightly down,
  hide: false, // Set to true to not show the bar
  ipEndpoint: "https://ipinfo.io/json", // Endpoint to get IP info in case of location-based targeting
  i18n: {
    hideText: "Hide announcement" // ARIA-label for close button
  },
  targeting: {
    once: false, // Set to true to not show after it's been closed in this session
    onceUser: false, // Set to true to not show after it's been closed by this user EVER,
    params: { // Support for URL param targeting
      // Add key-value pairs here
    },
    // Some examples below
    location: { // Add targeting by location
      eu: false, // Set to true to only show in EU countries
      country: ["us", "ca", "in"], // Array of countries to show in,
      city: ["New Delhi"], // Array of cities to show in,
      ip: ["192.168.1.1"], // Array of IP addresses to show in,
      postal: [110048], // Array of postal codes to show in,
      region: ["California"], // Array of regions to show in
    },
    pathName: "/about", // Only show on this path,
    href: "https://example.com/about" // Only show on this URL
  }
});
```
