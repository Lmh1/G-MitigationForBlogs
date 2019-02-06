#Steps for manual creation of an Internet Archive request to archive a link.

The [Internet Archive](https://web.archive.org), AKA the *WayBack Machine*, has a way to submit a request to archive any publicly accessible link

Thus any public G+ link can be archived at the Internet Archive and survive the death of G+.

**The format of the special link is as follows:**

https://web.archive.org/save/<URL>

Replace the characters "<URL>" with the link to the G+ page to archive it. **NOTE:** This will work with ANY public internet link.

For example, my [G+ page](https://plus.google.com/+Followmeanddie) for my Blog, [Follow Me, And Die!](https://followmeanddie.com) would look like this:

**REQUEST LINK:**
https://web.archive.org/save/https://plus.google.com/+Followmeanddie

The resulting link becomes: (This part is handled by The Internet Archive and not something you will create.)

**RESULTING LINK:**
https://web.archive.org/web/20190206103057/https://plus.google.com/+Followmeanddie

Each time you use a request link, you get a new resulting link, that has the data and time as part of the URL. You do not need to generate a new request if the page has not changed since you last generated it.

**NOTE:** It is possible to use the json or other file from Google Takeout or G+ Exporter to generate a list of all the links to your G+. You can then script a solution to feed each of those links to The Internet Archive to archive your G+ posts. The same could be done for a G+ Community.

**Where's the script?** I have not yet built a script. This little project is to help me organize and share information as I go, since the end of G+ is close. I didn't want to make others wait. Perhaps there is someone better at scripting than I am to do this. Wget, grep, and awk are probably the tools to use. They have versions available on Windows, Linux, and Mac. Other than directory paths on each machine, the same script should work on any OS with these tools. 

**Document Created:** February 6, 2019
