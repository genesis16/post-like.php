This week I had a client request a modification to an existing page template which already had two post anchor identifiers
to retrieve get_the_author_meta and get_the_date. It was a custom template that displays a CPT by category to a page.

So I found this repository on Github by Jon Masters and decided to implement it ( https://github.com/JonMasterson/WordPress-Post-Like-System )
but modifying the custom post type template instead of the standard blog page template.
Jon gives walkthrough instructions, but since I modified it for a custom post type template I will do my own walkthrough,
in case you are looking to modify a CPT template as well.

1. RUN QUERY MONITOR TO FIND THE TEMPLATE FILE YOU ARE AFTER
If you install the Query Monitor plugin, you can click on ‘templates’ to see which template file is being called in.
It’s not perfect though. In this case, it showed me a template hierarchy of 5 template files, none of which contained the section I wished to modify.
If this happens, then you can just dig around through the template files and if the naming convention is obvious you shouldn’t have too much trouble.
In this case I was editing the header-insight.php

2. OPEN YOUR FUNCTIONS FILE AND ADD THE POST-LIKE.PHP FILE CODE
Ok, this will make your functions file enormously long, but since Jon has shared the code I am going with what he as built for us already. 
Of course you can refactor that code into a post-like.php template file and call it into your functions file,
but let’s keep it simple and add the post-like.php into functions.php. 

3. CHANGE THEME NAME
In the pile of code we just added to functions.php go hit control F,
and replace “YourThemeTextDomain” with your theme name. This isn’t necessary but I think it makes your code clearer to read.

4. ADD THE JAVASCRIPT FILE TO YOUR LIBRARY
Add this javascript to your theme/lib/js/simple-likes-public.js path and save. 

5. 5. REPLACE THE SVG WITH FONT AWESOME
I found the SVG file came out massive, and of course its easy to modify it with CSS, but it’s also easy to add font awesome icons in,
and Jon has already commented out the instructions on how to do this in the functions.php file.

6. ADD THE LIKES FUNCTION WITHIN THE LOOP OF YOUR TEMPLATE
Now we are going to go into our template file, in my case it’s header-insights.php and find the section where the GET parameters that are already calling in the author and the date,
and we are going to echo in our function here.

7. CHECK YOUR PAGE TEMPLATE AND MAKE SURE YOUR LIKE BUTTON IS WORKING
Now we’re going to go to our post template file, refresh the page and see if our like button is working. If you click and un-click the button,
the heart will turn on and off which is correct. The way the function is setup, it only allows one user to like a post by calling your IP address into the wp_postmeta table in SQL,
so for example you cannot publish a post and click like a hundred times to look really cool, LOL.

Full guide with images here : https://jane-james.com.au/add-a-like-button-to-your-posts-in-wordpress-using-php-and-javascript
