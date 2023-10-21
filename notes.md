# How the Web Works
There are **clients** and **servers**. The server runs services/applications that are provided to the clients.

Clients and servers communicate with the **Request-Response-Cycle**. The Client sends a request to a server which processes it and returns a response.

A Web-Server mainly handles web-requests but also provides security data storage and can manage emails. (*nginx*) Usually the client to a web-server is a web browser.

[What is a web browser](https://www.mozilla.org/en-US/firefox/browsers/what-is-a-browser/ "What is a web browser")

[What is a web server](https://www.nginx.com/learn/web-server/)


Web server and web browser communicate usign the *Hypertext Transfer Protocol* **(HTTP)**

## Web hosting
A website is hosted on a server and there are several types of hosting.

* Shared hosting ` Shares physical hardware with multiple web sites `

* Virtual Private Hosting `Shares physical hardware which is split into virtual servers of a fixed size`

* Dedicated Hosting`Entire Server used for one website`

* Cloud Hosting `Combines physical and virtual servers. Website can run on multiple virtual servers on multiple hardware servers`

## Internet Protocols
### IPv4 and IPv6

* IPv4 - 0.0.0.0 up to 255.255.255.255 | 32Bit addresses
* IPv6 - i.e 2001:0db8:0000:0000:0000:8a2e:0370:7334 | 128Bit addresses

Data is sent in multiple IP packets also called Datagrams.
IP Packet contain Header and Data
Destination and Source IP addresss in Header

Packets can get lost, become damaged, lost or arrive out of order


TCP - Transmission Control Protocol

`
TCP cares that packages do arrive are not corrupted and for data that needs to be in the correct order. USed for Images, HTTP and anything that can not tolerate data loss.
`

UDP - User Datagram Protocol

`UDP only cares that the packages are not corrupted. Used for application that can tolerate some data loss. (I.e. voice calls, live streaming)`


### HTTP and HTTPS

Hypertext Transfer Protocol. Request-Response based protocol.

#### HTTP Request

**Header**

* Method - (GET {Retrieve}, POST {Send}, PUT {Update}, DELETE {Remove})
* Path - Where the resource is located on the web server
* Version - 1.1 and 2.0 most used
* Headers - Additional information about the request and the client making it.

```
Host: example.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9) ...
Accept: */*
Accept-Language: en
Content-Type: text/json
```

Host of the server where the resource is requested from. Accept is what kind of content is accepted in the response. **Content-Type** indicates the type of content transmitted in the HTTP request's body

**Body**

* Body *(optional)* - For certain methods a body containing information exists

#### HTTP Response:
Similar Format to Request
**Header**

* Status Code - Indicate if HTTP Request successfully completed (100 to 599) grouped by purpose

`Headers usually contain the date, information about the server, content-length which describes the length of the response and content-type which states the type of content included in the response body`


**Body**

* Body *(optional)* - Image File, HTML, ...

#### HTTP Status Codes
* Informational - 100 to 199

```
Interim (Before acutal response)
Provisional?
Status Code 100 Continue is the most common
```
* Successful - 200 to 299

```
Successfully processed by server
200 OK is most common but meaning depends on Request Method
GET = Resource was found and is included in Body of HTTP response
POST = Resource was successfully transmitted to server
PUT = same as POST
DELETE = successfully delteted resource
```
* Redirection - 300 to 399

```
Requested Resource has been moved to other path
301 Moved Permanently
302 Found - Temporary redirection
Request for the new path will be executed automatically
```
* Client Error - 400 to 499

```
Bad syntax or content
400 Bad Data
401 Log in needed
403 Request Valid but Server refuses to process (usually priviliges)
404 Resources not found
```
* Server Error - 500 to 599

```
500 internal server error
```

#### HTTPS
Traffic is encrypted before sending


### DHCP - Dynamic Host Configuration Protocol
Used to get a valid IP address. A machine requests an IP address from a DHCP server on the local network. The new IP address will be sent as a response. From then on the machine can communicate with other machines on the same network using this IP address

### DNS - Domain Name System Protocol
A domain name needs *(i.e. google.com)* needs to be converted to an IP address so that the computer can talk with the web server of that domain. A DNS server is queried for the IP address of this domain.

## Webpage vs Website vs Web application
All Webpages that are under the same domain name are considered the same website

Website usually more infromative than a web application. Web application usually more interactive

## Frameworks vs Libraries
Libraries are reusable pieces of code to provide a specific functionality to save time. For example verifying if an email is valid. Libraries are consider un-opinionated

Frameworks provide a structure for developers to work with. Frameworks are considered opinionated.

Opinioatedness describes how much freedom the developer has in the way functionality is implemented. A framework might force you to things a certain way hence having an opinion on how things should be done. 

## API - Application Programming Interface

Set of functions and procedures to access the functions of a service

Often called gateway or middleware as it is the gate or in the middle in between two services.

### Browser (Web) API
* DOM API - Translates HTML into tree of nodes represented as javascript objects
* Geolocation API
* Fetch API
* ...

### REST API - Representational State Transfer
Set of Principles to create efficient APIs

### SENSOR API
IoT based on this. Communicate with Sensors i.e. phillips hue sensors


[An Overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)





# HTML - Hypertext Markup Language
The first file is usually called *index.html*

HTML consists of **tags** which have an opening and a closing tag.

`<p>This is a <i>paragraph</i></p>`

Elements can also be empty and/or self closing 

`<p>This is a <br/> paragraph</p>`

## Basic HTML

``` html
<!DOCTYPE html>
<html>
	<head>
		<!-- Nothing in here is displayed on the actual website -->
		<title>This will be displayed in the tab</title>
	</head>
	<body>
		<h1>Our Menu</h1>
		<h2>Falafel</h2>
		<p>Chickpea, herbs, spices</p>
		<h2>Pasta Salad</h2>
		<p>Lettuce, vegetables, mozzarella</p>f
	</body>
</html>
```

### Common Tags
* \<h1>, \<h2>, ... , \<h6> 
* \<p> - Line breaks inside a paragraph are ignored by the browser
* \<br> - Specify a line break
* \<strong> - Show that a part of a sentence is important
* \<b> - make bold. Looks the same as strong but should only be used to draw attention
* \<em> - Emphasis (looks like italics)
* \<i> - Italics
* \<ul> - Unordered list (dots)
* \<ol> - Ordered list (numbers)
* \<li> - Specifies one list item
* \<div> - Content divider/container. Has **no effect** on the way content is display unless specified with *css*.
* A comment looks like this *\<!-- This is a comment -->
* \<a href="google.com"> - Create a hyperlink
* \<img src="/path/to/image.jpeg" width="240" height="135" alt="Description to the image for accessibility" /> - Show picture and set size. Also set alt for accessibility

### Tables

Created using \<table>. \<tr> creates a new *row* and in this row each \<td> creates an entry. For the header within the table the \<th> tag can be used

``` html
<table>
  <tr>
    <th>Dish</th>
    <th>Price</th>
  </tr>
  <tr>
	<td>Falafel</td>
	<td>10$</td>
  </tr>
  <tr>
	<td>Pasta Salad</td>
	<td>12$</td>
  </tr>
</table>
```


## Forms
Defined with the \<form> tag. If action is not set the request will be sent to the current endpoint. Method specifies with which HTTP method the request should be sent. 

``` html
<form action="/registration" method="POST">
	<label for="username">Username:</label><br>
	<input type="text" name="username" />
	
	<label for="password">Password:</label><br>
	<input type="password" />
	
	<input type="submit" />
</form>
```

With the \<label> tag it is possible to create a label for an input field. Each input field has a type. *Text* generates a simple text box and *password* generates a text box where the content is not visible. Input type *submit* creates a button that finally sends the request with the data from the input fields.

### Checkbox
Multiple or all of the checkboxes can be selected

``` html
<input type="checkbox" name="dog" value="Dog" />
<label for="dog">I own a dog</label><br>

<input type="checkbox" name="cat" value="Cat" />
<label for="cat">I own a cat</label><br>
```

### Radio buttons
Like checkboxes but only one can ever be selected.
 
``` html
<input type="radio" name="right" value="Right" />
<label for="right">I am right handed</label><br>

<input type="radio" name="left" value="Left" />
<label for="left">I am left handed</label><br>
```

### Other input types
``` html
<input type="number" name="left" />
<input type="email" name="left" />
<input type="file" name="left" />
```

### Input that doesn't use the \<input> tag

``` html
<!-- If multiple lines of text are needed as input use textarea -->
<textarea name="multiline" rows="5"></textarea>


<!-- Generates a drop down menu with the two options -->
<select name="food">
	<option value="chocolate">Chocolate</option>
	<option value="ice_cream">Ice cream</option>
</select>
```

## DOM - Document Object Model
Needed so that Javascript can interact with HTML and modify it.

### What is DOM
HTML page is being converted to a tree structure of the HTML file by the browser

JavaScript can use the DOM to add, delete, change or animate content on the current web page

## Sources
* [DOM](https://www.w3.org/TR/WD-DOM/introduction.html)
* [HTML Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
* [Form Element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)


# CSS - Cascading Style Sheet

*h1* is the the selector. This will affect all the h1 tags on the website.

Thedeclaration block begins with { and ends wirh }

The properties *color* and *background-color* are set to the *values* grey and red.

``` css
h1 {
	color: grey;
	background-color: red;
}
```

A CSS file can be connected to an html file with the \<link> tag inside the html file's header like so: *\<link rel="stylesheet" href="./style.css">*

## Selector Types
There are several selector types
* Element - Lets the developer change the style for a specfic html tag type. I.e. for all \<h1> tags.

``` html
<p>New!</p>
```

```css
p {
	background-color: red;
}
```

* ID - Specifies the style for one specific element.

``` html
<span id="latest">New!</span>
```

``` css
#latest {
	background-color: red;
}
```

* Class - Specifies the style for all elements with this class

``` html
<a class="navigation">Test1</a>
<p class="navigation">Test2</p>
```

``` css
.navigation {
	background-color: red;
}
```

* Element with Class - All p tags with the class

``` html
<a class="navigation">Test1</a>
<p class="navigation">Test2</p>
```

``` css
p.navigation {
	background-color: red;
}
```

* Descendant - Sets style for all elements within another one. Test1 and Test2 will be affected

``` html
<div id="mainDiv">
	<p>Test1</>
	<div>
		<p>Test2</p>
	</div>
</div>
```

``` css
#mainDiv p {
	background-color: red;
}
```

* Child - Only selects **immediate** descendants. Only Test1 will be affected

``` html
<div id="mainDiv">
	<p>Test1</>
	<div>
		<p>Test2</p>
	</div>
</div>
```

``` css
#mainDiv > p {
	background-color: red;
}
```

### Pseudo classes
The pseudo class *:hover* changes the links color to red when the user hovers above it with the mouse. A pseudo class is appended at the end of a selector.

``` html
<a>Test1</a>
```

``` css
a:hover {
	color: red;
}
```

## COLOR
5 ways to reference a color

* RGB
* RGBA 
* HSL
* HEX
* Predefined Color Names

## TEXT

* **color** - sets the color of the text itself
* **font-family** - Lets the dev specify the font to use *(i.e. "Courier New")*
* **font-size** - Lets the dev specify the font size *(i.e. 12px)*
* **text-transform** - Make sure the text is a certain format *(uppercase, lowercase, capitalize, none)*
* **text-decoration** - Add or set decorative elements *(underline, overline, line-through, none)*. With *text-decoration-style* it is possible to further specify the decoration *(solid, double, dottet, dashed, wavy)*

## BOX MODEL
Every element has a Box. The Content itself is the *Content Box* (i.e the text or the image). After that there is the *padding* which is a space around the content. This space would also have a background if the property is set in css. Around that there is the *border* and around that the *margin*. The margin specifies the distance to other elements on the page.

Padding, Border and Margin can be set all in one with a shorthand propert:

* Padding: 4px 2px 1px 5px;
* Margin: 4px 2px 1px 5px;
* Border-width: 4px 2px 1px 5px;

## DOCUMENT FLOW
### INLINE
Inline Elements only occupy the width and height of their content. They do not appear on a new line - hence inline. They will be displayed in one line as long as it fits. They will form a row of elements.

`<a>, <img>, <input>, <label>, <b>, <i>, <em>, <span>`

### BLOCK
Block elements occupy the entire horizontal space (the entire width), the height of it's content and have a new line before and after itself. That means that multiple block elements will stack on top of each other.

` <div>, <form>, <h1-5>`

## Text Alignment
* **text-align** property: possible values are *left, right, center, justify*. Justify spaces the text so that each line of text has the same width.

### Float
The float property sets an elements position relative to the text content within a parent element. The text will wrap arount this element. The elemt whos float is set needs to be before the text that shall wrap around it. 

* [CSS Refernce](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)
* [HTML & CSS - Design and build Websites](https://www.amazon.com/HTML-CSS-Design-Build-Websites/dp/1118008189/)
* [CSS Definitive Guide](https://www.amazon.com/CSS-Definitive-Guide-Visual-Presentation/dp/1449393195/)

`Rewatch "What are Forms"`

# UI FRAMEWORKS

## Dependencies
Libraries need to be included in the final application. The application depends on them. Hence they are often called dependencies.

When dependencies depend on other dependencies that forms a **dependency tree**

A **package manager** handles dependencies. It will automatically download the appropriate version of a package and also install the entire dependency tree.

Packages can be bundled into one single fileusing a **bundler** *(i.e. webpack)* to avoid having to include many libraries in the HTML file. 

## Using Bootstrap

Bootstrap is collection of pre-written css and javascript code chunks.

Include the following in the header

``` html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
		rel="stylesheet" 
		integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN"
		crossorigin="anonymous">
```

And somewhere in the body the following:

``` html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"
		integrity="sha384-C6RzsynM9kWDrMNeT87bh95OGNyZPhcTNXj1NW7RuBCsyN/o0jlpcV8Qyq46cDfL"
		crossorigin="anonymous">
</script>
```

### Responsive design
3 Practices

* Flexible grids
* Fluid images
* Media queries

Breakpoint is the point at which the UI adapts to fit a differe

* Fixed width Grids have a fixed width and the rest is spaced with margin
* Flui

### Infixes

**Breakpoints** are the triggers for how the UI changes on different devices *(i.e. different layout for screens with a width smaller than 720px)*

<table>
	<tr>
		<th>Breakpoint</th>
		<th>Class infix</th>
		<th>Dimensions</th>
	</tr>
	<tr>
		<th>Extra Small</th>
		<th><em>No infix because default</em></th>
		<th>< 576px</th>
	</tr>
	<tr>
		<th>Small</th>
		<th>sm</th>
		<th>>= 576px</th>
	</tr>
	<tr>
		<th>Medium</th>
		<th>md</th>
		<th>>= 768px</th>
	</tr>
	<tr>
		<th>Large</th>
		<th>lg</th>
		<th>>= 992</th>
	</tr>
	<tr>
		<th>Extra Large</th>
		<th>xl</th>
		<th>>= 1200px</th>
	</tr>
	<tr>
		<th>Extra Extra Large</th>
		<th>xxl</th>
		<th>>= 1400px</th>
	</tr>
</table>

### Modifiers

* primary
* secondary
* success
* info
* warning
* danger
* light
* dark

### Bootstrap Grid System
Grid uses a 12 column grid system that can be fluid or fixed.

Always has container, rows and columns.
**container** is the root element of the grid. Always starts with this.

``` html
<div class="container">
  <div class="row">
    <!-- On devices smaller than 'lg' each column will take up the entire space -->
    <!-- On devices larger or equal to 'lg' each column will take up half the space -->
    <div class="col-12 col-lg-6">
    	<h1>Burger</h1>
    </div>
    <div class="col-12 col-lg-6">
    	<h1>Fries</h1>
    </div>
  </div>
</div>
```

### Bootstrap Components

The Documentation has everything one can wish for.

Some interesting things are

`Input Groups, Navbar, Forms `

### Other Framworks

* Foundation
* Pure.css
* Tailwind

# STATIC VS DYNAMIC CONTENT

Static content is files that are transferred as is. For example videos or images.

Dynamic content is generated when the HTTP request is made


Web Server talks to an application server/backend. The application server generates the content that the web server then sends to the client. The web server caches dynamic content to reduce stress on the application server. 

## Single Page Applications (SPAs)
One HTML page that gets sent form server to browser. The page updates it's content.

There are two approaches:

1. Bundling - Server returns all needed data. 
2. Lazy Loading - Send only the necessary data and load additional content on demand only when needed

# REACT

Can develop SPAs or Mobile applications with React Native

[SPA vs Traditional Web App](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/choose-between-traditional-web-and-single-page-apps)

**`Define components that can be reused and combined into a website`**

There are react component libraries for different needs. Video player components, Map components.

## How it works
React Element has 1 to 1 realtion to an HTML element on the website

Builds a virtual dom anch checks if that differs from the DOM in the browser. If so an update is made. If not no update is needed. This whole process is called **reconciliation**

```
If there was a change the virtual DOM get updated
The new virtual DOM is checked against the old virtual DOM to identify if there were any changes and if so where.
Only the changed elements are then changed in the web browsers DOM causing the website to change
```

Furthermore updates to the browser are spread out through time. If a change occurs that is not visible on the browser it does not need to be updated right away. Rather a change that affects something that is currently visible will be prioritized. This technology is called **React Fiber Architecture**

## Component Hierarchy

It always starts with the Root - *App* - component. After that usually a Navbar Component and a Main Body Component. These in turn contain other components.

## Complementary libraries

* Lodash - Sort Lists, Round Numbers
* Luxon - Date and Time Formatting
* Redux - Keep track of state of the state. (Shopping cart)
* Axios - Simplify sendinding HTTP Request (for example with APIs)
* Jest - JavaScript testing







