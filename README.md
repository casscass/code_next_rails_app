# Ruby on Rails for High School

Go to https://github.com/casscass/code_next_rails_app and open the README 

## Setting up our Rails app Day 1


Sign into cloud9

Give your Blog a name

Select the ruby on rails button (top right )

Click the green Create workspace button at the bottom.

![](https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/1.Create-new-workspace.png)

## Creating basic functionality
NB FOLDER STRUCTURE – Look at model, view, controller

Lets look at the file structure

Open the folders view, model & controller

Look at the files in these folders

We are about to make a Post scaffold, this will create a post file in each of these folders.

Currently there are no Post files in any of these folders.


## Using a Rails generator to build some code for you

In the Terminal type:

```
rails generate scaffold Post title:string body:text
```
#### Let’s break this command down:
We’re asking rails to generate a scaffold (basic building blocks; think construction scaffolding) for a “thing” that we want to call a Post in our system. In Rails terminology this “thing” (Post) is called a “resource”.

###### We want to give our Post two attributes:

1. a title, which we want to be a string, and

2. a body, which we want to be text.

A string is computer-speak for a short sequence of characters like "hello" or "Are you having fun, yet?", and can usually be as long as your average tweet. Blog titles tend to be short, so we’ll use a string for ours. 

text is like a string, but longer, so we’ll use it to have enough room to write as many paragraphs as we want in the body of our blog post.

NB FOLDER STRUCTURE – Looking at POST files

NOW lets go back and look at the folders again. We can see that now there are post files in them.

AND…An important file that was generated was the migration 

db/migrate/20140528075017_create_posts.rb

Note that, as this filename starts with a unique id including the date and time, yours will have a different set of numbers.

```
# db/migrate/20140528075017_create_posts.rb 
class CreatePosts < ActiveRecord::Migration   
   def change     
   create_table :posts do |t|       
   t.string :title       
   t.text :body        
   t.timestamps     
  end   
 end 
end 
```

This file is Ruby code that Rails uses to manage how your data is stored in the database.

You can see that this code is to create a table called Posts 

and to create two columns in this table, 

1. a title column and 

2. a body column.

Whilst we have generated this code to create our Posts table, the script has not yet been executed and therefore the table does not yet exist in our database.

We need to instruct Rails to apply this to our database. In the Terminal type type :

```
 rake db:migrate 
 ```

## Setting the index/root page in Rails

If we run the server and look at our Blog it will look like this:

![]
(https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/2.App-Preview.png)

Click the red Open the App buttion

Now we have this page

![]
(https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/3.Add-routes.png)

Because we are in Cloud9 we need to set the route
Open config/routes.rb and add 

```
 root ‘posts#index’ 
 ```
 
 to that file so it looks like:

 ```
 # config/routes.rb 
 
Rails.application.routes.draw do  
	resources :posts 	  
	end 
root 'posts#index'  
```

(Don’t forget to save your file.)

Once this command has run you can start up your Rails server again with rails server and then navigate to your workspace to see the changes you’ve made to your application.

From here you can play around with your application.

### TASK Create 3 new posts

## Changing the Heading and title of your new blog

NB put up app and terminal side by side so students can see the html changes.

Lets look at the html code for your apps main page.

Goto cloud9 text editor.

Look at the folders down the left hand side.

Open the app folder by clicking on the grey arrow. The views folder is the 6th one down

Open the views folder, inside is the posts folder.

Open the posts folder - Look at the file structure.

Open the file called index.html.erb by double clicking on it.

This file structure is written as app/views/posts/index.html.erb 

On line 3 change 

``` <h1>Listing Posts</h1> 
```
 to 
 
 ```
  <h1>Awesome Posts</h1>
  ```

Save  

```
command s
```

and refresh the app… what is the keyboard shortcut to refresh the app

## Every Post must have a title & body

We’re going to add some functionality to our new Rails app to enforce a rule that every post must have a title.

Open 

```
app/models/post.rb 
```

and add the following line to your code:

```
validates :body, :title, presence: true 
```

(Don’t forget to save your file.)

Your post.rb file should look like:

```
# app/models/post.rb 
class Post < ApplicationRecord   
  validates :body, :title, presence: true 
end 
```

We can check that this works by returning to our browser, editing our blog post, deleting the title and clicking Update Post.

You’ll get an error informing you that you’ve attempted to break the rule you just created:

## Changing the Look of the Show Page

Right now our  show post page isn’t looking very good.

Mine looks like this:

![Show Page](https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/ShowPage1-original.png)

Lets fix up the look by changing the title to a <h2> and get rid of the words “title” and ‘body”Open   

``` 
app/views/posts/show.html.erb 
```     

and make it look like the following:

```
<p id="notice"><%= notice %></p>  
<h2><%= link_to_unless_current @post.title, @post %></h2> 
<%= simple_format @post.body %>  
 
<%= link_to 'Edit', edit_post_path(@post) %> | 
<%= link_to 'Back', posts_path %>
```

SAVE FILE

Refresh the Show page in your browser  

What has changed? The Post heading is now a <h2> heading and the words Title and Body have gone. 

Mine now looks like this:

![Mine now looks like this:](https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/ShowPage2-FixedUp.png)


Go To your show page at 
```
app/views/posts/show.html.erb 
```

and add a <h1> heading so your  show.html.erb  file looks like this: 

```
<p id="notice"><%= notice %></p>
<h1>My Awesome Show Page</h1>  
<h2><%= link_to_unless_current @post.title, @post %></h2> 
<%= simple_format @post.body %>  
 
<%= link_to 'Edit', edit_post_path(@post) %> | 
<%= link_to 'Back', posts_path %> 
```
SAVE FILE

And now my show page looks like this:

![Show Page-with headings](https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/ShowPage3-h1-Heading.png)








![Bootstrap](https://github.com/casscass/code_next_rails_app/blob/master/README-IMAGES/Bootstrap-in-Gemfile.png)








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