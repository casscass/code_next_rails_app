# Ruby on Rails for High School

## HTML / CSS Explainers

### HTML

``` HTML
<!-- THIS IS A COMMENT -->
<h1>   <!-- Opening tag -->
    This is a Heading 1
</h1>  <!-- Closing tag -->

<p>
    This is a paragraph
</p>

<img src="images/image.png" class="img-responsive"> <!-- Image tag -->
```

1. What does `<h2>` mean?

2. What does `<p>` mean?
   
3. What does `<img>` mean?

### CSS

``` CSS
// THIS IS A COMMENT
/* THIS IS ALSO A COMMENT */

p { // This is a selector
    color: black; // This is a CSS Rule
}

h1 {
    color: red;
    font-size: 96px;
}
```

1. What would the `p` selector do?

2. What would the `h1` selector do?

## Process for Styling Rails with Bootstrap

This section must use the starter app provided in the `starter-app` folder.

### Google Fonts with Ruby on Rails!

1. Go to http://fonts.google.com and pick:

  - ONE serif font
  - ONE san-serif font
  
  For the fonts get the `@import` statement, and their CSS rules: `font-family: FontName, serif`
  
  For example, the @import statement for the fonts Roboto and Allerta Stencil looks like this:
  
  `@import url('https://fonts.googleapis.com/css?family=Allerta+Stencil|Roboto');`
  
  ... and the CSS rules for these fonts looks like this:
  
  `font-family: Roboto, sans-serif;`
  
  `font-family: 'Allerta Stencil', sans-serif;`
  
  **Hint:** click the + button next to fonts you like and you will find the `@import` and CSS properties in the floating menu at the bottom of the page.

  
  If you are interested in the difference between serif and san-serif, watch this video: https://www.youtube.com/watch?v=ocvUGN-OD0w

2. In Cloud 9, open the following file `app/assets/stylesheets/application.scss`.

3. Add the two `@import` statements to the top of the file.

4. Add the `h1-6` and `p` CSS selectors underneath your `@import`, it should look like this:

``` SCSS

@import url('https://fonts.googleapis.com/css?family=Allerta+Stencil|Roboto')

 h1, h2, h3, h4, h5, h6 {
  // ADD CSS RULES HERE
 }
 
 p {
   // ADD CSS RULES HERE 
 }
```
5. Add the `font-family` CSS rule for the heading font to the `h1-6` selector (the rule should go between the curly braces!).

6. Add the `font-family` CSS rule for the paragraph font to the `p` selector (the rule should go between the curly braces!).

#### Extension Activity (for later)

Find a third font to use for important headings, such as the title of your website. In the next section you will create a navigation bar that will have the name of your website in it -  you can come back and find a really special font for this later.

How to do this:

1. Put the following `<span></span>` element around the title of your website, it should look like this:

``` HTML
  <a class="navbar-brand" href="#"><span class="title-font">MY WEBSITE TITLE</span></a>
```

2. Add the `@import` for your chosen font to the top of your `app/assets/stylesheets/application.scss` file.

3.Add the following CSS selector and font family rule to your `app/assets/stylesheets/application.scss`, it should look like this:

``` CSS 
.title-font{
  // ADD the font-family CSS rule for your chosen font here
}
```

### Add A Nav Menu and Footer to a Rails App Using Bootstrap!

Navigation menus are so important on websites, they let you navigate 
between pages, and often give you an idea about what a website is about.

We will implement a nav menu that you can style however you like!

#### Navigation Menu

1. Open the following file in Cloud 9: `app/views/layouts/application.html.erb`.

2. Add the following code snippet to the file:

``` HTML
<!-- START NAVBAR  -->
<nav class="navbar navbar-expand-lg navbar-light bg-light"> 
  <a class="navbar-brand" href="#">MY WEBSITE TITLE</a> <!-- TODO: Put your website's name here !!  -->
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
    <div class="navbar-nav">
      <a class="nav-item nav-link active" href="/">Home</a> <!-- Duplicate this to add more items to your menu -->
      <a class="nav-item nav-link active" href="/menuItemName">Your Menu Item</a> <!-- Duplicate this to add more items to your menu -->
    </div>
  </div>
</nav>
<!-- END NAVBAR -->
```

3. Open the following file in Cloud 9: `app/assets/stylesheets/application.scss` and add the following to the end of the file:

``` SCSS

.navbar-brand {
  color: red !important;
  font-weight: bold;
}

```

4. Remove `bg-light` from the `<nav>` element in your menu, and change `navbar-light` to `navbar-dark`.

5. Add the following CSS selector to the end of the `application.scss` file:

``` SCSS

nav {
  background: #333333;
}

```

#### Footer

1. Scroll to the bottom of your `application.html.erb` file and put a `<footer>` element before the closing `</body>` tag, it should look like this:

``` HTML
<footer>
  
</footer>
</body>

```
2. Inside the `<footer>` put the following:

``` HTML
<p>
 Your Name &copy; 2018
</p>
```

3. Open the `app/assets/stylesheets/application.scss` file and add the following:

``` SCSS

footer {
  background: // CHOOSE A COLOUR, see the CSS Gradient link on your handout!
  padding: 30px;
}

footer p {
  text-align: center;
  color: // CHOOSE A COLOUR, see https://htmlcolorcodes.com/ 
}

```
4. Open the `app/assets/stylesheets/application.scss` file and add the following:

``` SCSS

nav a:hover {
  color: // CHOOSE A HOVER COLOUR AND ADD !important after it
}

```

#### Extension Activity (for later)

1. Add additional styles to the `nav` selector in `application.scss` such as:
  - `border-bottom`, see: https://www.w3schools.com/css/css_border.asp
  - `box-shadow`, see: https://www.w3schools.com/css/css3_shadows.asp
  
2. Add a CSS Gradient as a background to your footer. Use the following website: http://www.colorzilla.com/gradient-editor/ to create a gradient rule.

3. Look at the Bootstrap documentation on Navbars and add some additional features to your navbar, see: https://getbootstrap.com/docs/4.1/components/navbar/

### Use Bootstrap to Make Forms Look Nice in Rails!

Forms are a very important part of a website - people spend a lot of time
typing stuff into them so they have to look good and be easy to use.

1. Open the `app/views/posts/_form.html.erb`.

2. Make the changes to form indicated in the comments:

``` ERB
  <div class="field"> <!-- CHANGE field to form-group -->
    <%= f.label :title %><br> 
    <%= f.text_field :title %> <!-- AFTER :title put a comma and INSERT class: "form-control" -->
  </div>
  <div class="field">
    <%= f.label :body %><br>
    <%= f.text_area :body %> <!-- AFTER :body put a comma and INSERT class: "form-control" -->
  </div>
  <div class="actions">
    <%= f.submit %> <!-- ADD class: "btn btn-primary" AFTER f.submit -->
  </div>

```

3. Open the `app/views/posts/show.html.erb` file and follow the same process as in the last step to add Bootstrap styles to the Comment form.

### Text Generators and Styling Blog Posts!

Websites need content!

Content can be words, pictures, diagrams, videos, animations, etc... the list goes on.

1. Go to the lorem ipsum text generator link on your handout and generate:
  - 5 paragraphs of placeholder text
  - 1 list
  
2. Copy your paragraphs and lists to the create post textarea in the `app/views/posts/_form.html.erb` file.

3. Add `<p></p>` tags around each paragraph, then submit the form.

4. Open the `app/views/posts/show.html.erb` file, find the following line which renders the `@post.body` of your blog post, and replace it with the following line:

``` HTML
<%= simple_format(@post.body) %>
```

5. Add `<ul></ul>` tags around ALL your list items, then add `<li></li>` tags around each list item. Your list will end up looking like this:

``` HTML
<ul>
  <li>List Item 1</li>
  <li>List Item 2</li>
</ul>
```
Post your list as a comment.

6. Open the `app/views/comments/_comment.html.erb` file, find the following line which renders the `@comment.body` and replace it with the following line:

``` HTML
<%= simple_format(comment.body) %>
```

### Stretch Goals

Style your posts/show.html.erb to:
- make the show, edit and destroy links into buttons, or a button group, see the Bootstrap docs for how to do this: https://getbootstrap.com/docs/4.1/components/buttons/

- Create a dropcap for the first letter of your blog post, change its colour, and give it a hover effect. Add the following code to your `app/assets/stylesheets/application.scss` file, and then modify the `font-size`, `line-height`, and `padding` rules to style it how you like:

``` SCSS

.drop-cap {
  color: #000000;
  float: left;
  font-size: 75px;
  line-height: 60px;
  padding-top: 4px;
  padding-right: 8px;
  padding-left: 3px;
}

.drop-cap:hover {
  color: #000000;// choose a colour
  border-bottom: 1px solid #000000 ;// choose a border style, see: https://www.w3schools.com/css/css_border.asp
  // text-shadow: ; // experiment with text-shadow, see: https://www.w3schools.com/css/css3_shadows.asp
}

```

- Use `:hover` and background or box-shadow to style the table of blog posts in posts/index.html.erb

### Superstar Developer Goals *

1. Use the Bootstrap collapse component to create an accordion of your blog posts in your `app/posts/index.html.erb` file. Replace the `<table></table>` and everything inside it with the following:

``` HTML
<section>
        <h2 class="display-2">Option 3:<br> Accordion Post List</h2>
        <div class="accordion" id="myAccordion">
          <% @posts.each do |post| %>
          <div class="card">
            <div class="card-header" id="headingOne">
              <h5 class="mb-0">
                <button class="btn btn-link" type="button" data-toggle="collapse" data-target="#collapseOne<%= post.id.to_s %>" aria-expanded="true" aria-controls="collapseOne">
                  <%= post.title %>
                </button>
              </h5>
            </div>
        
            <div id="collapseOne<%= post.id.to_s %>" class="collapse" aria-labelledby="headingOne" data-parent="#myAccordion">
              <div class="card-body">
                <%= simple_format(post.body, sanitize=false) %>
              </div>
            </div>
          </div>
          <% end %>
        </div>
    </section>
```

2. Put a Bootstrap Jumbotron (https://getbootstrap.com/docs/4.1/components/jumbotron/) at the top of your `app/views/posts/index.html.erb` file. Add styles to your `application.scss` file to:
  - change the background colour of the Jumbotron
  - make the background of the Jumbotron a linear gradient
  - code the button on the Jumbotron to go to a particular blog post
  
### Extreme Programming Perfection Goals

1. make at least 5 blog posts
   
  - each post must contain at least one picture, see: https://unsplash.com for pictures
  - each post must have a `blockquote`
  - each post must have am `ul` and `ol` list with THREE list items.
  
2. Replace your Jumbotron with a carousel (https://getbootstrap.com/docs/4.1/components/carousel/)
   
  - find three images to add to your carousel
  - add captions to your carousel