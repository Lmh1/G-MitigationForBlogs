#Finding Posts on WordPress Blogs

**Manually:**
Go to the admin area of WordPress, then go to eh posts section and search for: *plus.google.com*.

**SQL**
using SQL makes it much easier to get an accurate portrayal of the scope of how many posts on your blog contain links to G+ content.

I use SQL nearly daily in my day job. I always build from a general script to a specific script to ensure I've got everything right.

The following will select all WordPress posts that contain *plus.google.com*. **NOTE:** WordPress *Pages* are considered *Posts* in the WordPress data model. 

```SELECT * FROM `wpfmad_posts` WHERE post_content like '%plus.google.com%'```

The above script is not as helpful as it could be as it contains all of the revisions to every post. If, like me, you put in a quick not to get started, come back to it a few time, and safe often as you write it, can have several stored copies of past versions of the post. We need to identify **ONLY** the *most current* version of each post that has a G+ link.

The following, using distinct on the column, *post_title* will give us the list of unique pages with links. Each page has at least one G+ link and may have multiple links, depending on how many you put on a given post.

```SELECT distinct(post_title) FROM `wpfmad_posts` WHERE post_content like '%plus.google.com%'```

Once you have the list of distinct pages, you can investigate the text of each. PHPMyAdmin has an option to allow the user to export the results of an SQL script. However, we will need another SQL script to return the text of the most recent post.

The manual way of doing this is to refine your SQL statement to get what you want. (I did not have time to refine this to fewer scripts when I initially create this page. Again, this is to get something useable to help others.)

```
--Get list of Unique Posts with G+ links.
SELECT DISTINCT (post_title)
FROM  `wpfmad_posts` 
WHERE post_content LIKE  '%plus.google.com%'

--Now that you have the list of post titles with G+ links, pick one to use with this script.
--Use the following to get the content of the post of a single title
--NOTE: It will list all revisions of the post.
SELECT post_content 
FROM  `wpfmad_posts` 
WHERE post_title='TITLE_OF_YOUR_POST'

--Use the following to get the newest version of the post.
SELECT MAX(POST_DATE) 
FROM  `wpfmad_posts` 
WHERE post_title='TITLE_OF_YOUR_POST'

--Use the following with the post title you are working on and the date returned by the prior script.
SELECT *
FROM  `wpfmad_posts`  
WHERE post_title='TITLE_OF_YOUR_POST'
AND post_date='2015-04-10 17:38:07'

--This is a variation of the prior script, it will only return the post content. 
--You can export it to a file and identify the specific G+ links to script.
SELECT post_content
FROM  `wpfmad_posts`  
WHERE post_title='TITLE_OF_YOUR_POST'
AND post_date='2015-04-10 17:38:07'
```

**NOTE:** You can use SQL to generate a list of all posts, including all the various revisions of each post, export the results, and then use a program like grep to pull out all the unique G+ links so you can create them at the internet archive.

**ToDo:** 

* Simplify the SQL to return the unique post titles for the most recent revision of each post.
* Craft a grep script to scan a file for G+ links and create a new file of just the G+ links.
