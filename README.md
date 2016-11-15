# Simple flexgrid
A simple, yet customizable flexbox-based grid written in SCSS

## Installation
Using Node Package Manager
```
npm install --save simple-flexgrid
```
Alternatively using unpkg.com as a CDN

* For SCSS usage you will need both the main and the configuration file
    1. https://unpkg.com/simple-flexgrid/dist/simple-flexgrid.scss
    2. https://unpkg.com/simple-flexgrid/dist/_config.scss

* For CSS usage you will need the main CSS file
    1. https://unpkg.com/simple-flexgrid/dist/simple-flexgrid.css

## Usage
### 1. The efficient way
This generates just the CSS you use. No more, no less.
```SCSS
// in SCSS

import 'path/to/simple-flexgrid.scss';

.some-container {
    @include row();
}

.some-content {
    @include col(6, 12, 8px); // will generate a 6/12th column with an 8px gutter
    // Only the first parameter is mandatory.
    // Default settings will be used if optional parameters are left out.

    @include mq('max-width: 800px') {
        @include col(6, 12, 8px);
    }

    @include mq('max-width: 450px') {
        @include col(12, 12, 8px);
    }
}
```


### 2. The lazy way
This generates a huge overhead of CSS classes, but hey it's easy.
```SCSS
// In SCSS file
import 'path/to/simple-flexgrid.scss';



// This will generate a 10-based grid with 0px gutters and the names of the clasess have the prefix 'myPrefix'.
// Custom breakpoints where sm=350px, md=500px, lg=750px, xl=1100px
@include simpleFlexgrid('myPrefix', 10, 0px, (350px, 500px, 750px, 1100px));
// All parameters are optional and default settings will be used if left out.
```

```HTML
<!-- in HTML -->
<div class='row'>
    <div class="xl-6-12 md-12-12">Some content</div>
    <div class="xl-6-12 md-12-12">Some other content</div>
</div>
```


### 3. The old school way
Using an Simple Flexgrid with an external stylesheet
 ```HTML
<head>
    <link rel="stylesheet" href="path/to/simple-flexgrid.css">
</head>

<body>
    <div class='row'>
        <div class="xl-6-12 md-12-12">Some content</div>
        <div class="xl-6-12 md-12-12">Some other content</div>
    </div>
</body>
 ```

## Misc.
Simple-flexgrid has a few helper classes
#### Pusher classes
The example below will push the element 2/12th of the containing row.
```SCSS
// In SCSS
.my-class {
    include push(2, 12, 8px) }
```
Alternatively
```HTML
<!-- in HTML -->
<div class='xl-push-2-12'></div>
```
#### Spacer classes
The example below will push the next element 2/12th of the containing row.
```SCSS
// In SCSS
.my-class {
    include space(2, 12, 8px)
    // All parameters are optional.
    // Default settings will be used if left out.
}
```
Alternatively
```HTML
<!-- in HTML -->
<div class='xl-space-2-12'></div>
```

## Default settings
Simple-flexgrid is by default set to be a 12-based grid with 8px gutters.
The default breakpoints are sm: 450px, md: 650px, lg: 800px, xl: 1200px.

All of these settings can be changed by editing the config file: ```simple-flexgrid/dist/_config.SCSS```
