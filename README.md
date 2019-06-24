This repository holds the html files for the showcase page of my website, https://mcglynnk.github.io/showcase/.    
      
Made using hugo and the Forty theme (https://github.com/MarcusVirg/forty). Credit also to https://github.com/emitanaka for the 
data science projects showcase design!     


/    
/   
/    
/    
/   
/   
/   
/   
/   
/   
/   
/   
/   

## Showcase setup
This took quite awhile to set up, so if anyone comes across this and is interested in setting this up on their own site, here are some
good resources:
(I'm using git bash and WSL Ubuntu)
https://gohugo.io/hosting-and-deployment/hosting-on-github/     
https://inside.getambassador.com/creating-and-deploying-your-first-hugo-site-to-github-pages-1e1f496cf88d    
      
      
Briefly, you'll need to make two repositories (this is because of how hugo sites are hosted on github)     
### Repo #1: name it forty-fork (or whatever you like)      
  - Download the zip file of the forty theme
  - Create a local directory called forty-fork, and a themes folder inside
  - Copy the "forty" folder from the zip file into the themes folder
  - Inside themes/forty, copy the contents of exampleSite into the main forty-fork folder
  - Make sure there is a config.toml file in the main folder, edit this file with your own personal info.
  - In git bash, go to the forty-fork folder, ```git init```, ```git remote add origin yourrepo#1url.git```
  - Git add, commit and push your local files to the remote repo

### Repo #2: 
If forty will be your main website, name this repo yourusername.github.io.  If forty will be a page on another website (like  mine, I named it showcase), name it whatever you like (you'll see why in a minute).  In the config.toml file, set your website url to "https://yourusername.github.io/" or "https://yourothersite.github.io/showcase/".

Run:   
```git submodule add -b master git@github.com:<USERNAME>/<USERNAME.github.io OR (in my case) showcase>.git public```   
    
At this point, you can edit your site locally. Change anything you want in config.toml and the content folder, then in your console, run ```hugo serve --watch``` and go to localhost:1313 (if this is your main site) or localhost:1313/showcase to view your site built locally. You can continue updating local files and localhost:1313 will update automatically. Use ctrl+C in the console when you're done.   
*Note: if you change anything in config.toml, you'll need to stop the local build with ctrl+C and re-run ```hugo serve --watch``` to see changes.*    

### Deploy site
When you're ready to send the site live, first check that your remotes point to the right place.      
In the console, go to your forty-fork folder and run ```git remote -v```. It should point to  https://github.com/yourusername.forty-fork.git.
From here, ```cd public``` and run ```git remote -v``` again.  This should point to the url you named in the config.toml file.

Then run:   
```hugo    
cd public    
git add .    
git commit -m "your commit message"    
git push origin master```     
      
Your site should now be live at your url.    
You can automate this part by copying my deploy.sh file, see this site again: https://gohugo.io/hosting-and-deployment/hosting-on-github/.
    
    
One more thing... At first, my showcase site built just fine locally but did not render any css and js when I sent it live.  This is because of how the forty theme is built. Github does not allow http:/ addresses in the css content or any direct http:// or https:// references. Using a text editor like sublime text, open the forty-fork folder, search all files for http://, and find and replace with https://.  Then search for direct references to your url and replace them. For example, find all https://yourusername.github.io/showcase/ and replace with /showcase/.  Now the site should work!      
      
*Note: If you're still having trouble, you can open your site in chrome, right click > inspect and go to the security tab.  Now refresh the page. Any security issues should pop up in red and point you to the css file that still has issues.*     



