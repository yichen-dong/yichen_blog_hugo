+++
title = 'How I Set Up My Blog'
date = 2023-12-20T00:37:14-05:00
draft = false
+++

When it came time to revamp my personal site, yichendong.com, I faced a bit of a problem. My old platform, fastpages, wasn't supported anymore, and honestly, I couldn't quite remember how the website worked. So, I decided it was time for a fresh start.

![What the website looked like pre-rework](/Pastedimage20231125124344.png)

## Choosing the Right Platform

I weighed my options: Hugo, Pelican, and Jekyll. Each had its strengths, but I initially leaned towards Jekyll for its established presence and GitHub's seamless support.

### The Journey with Github Pages

Creating a new GitHub page seemed like a straightforward task. I followed [GitHub's own guide](https://pages.github.com/) and set up a new repository named yichen-dong.github.io. A quick `git clone` command, a simple "Hello World" in `index.html`, and a push to GitHub, and voilà! My site was up and running at `https://yichen-dong.github.io/`.

![The initial GitHub page](/Pastedimage20231126022131.png)

## Custom Domain Saga

I'd previously set up GitHub pages differently when experimenting with fastpages. Upon revisiting, I noticed my custom domain DNS check hadn't gone through, despite yichendong.com resolving correctly.

![GitHub pages settings](/Pastedimage20231125132910.png)

### DNS Troubleshooting

I dove into GitHub's [documentation for apex domains](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#using-an-apex-domain-for-your-github-pages-site), which suggested setting up an `A`, `ALIAS`, or `ANAME` record. A quick check on my Namecheap Nameservers revealed some old DNS settings linked to Netlify—time to clear that up.

![Namecheap Nameservers](/Pastedimage20231126020941.png)

After tweaking some CNAMES and A Records as per this [Namecheap guide](https://www.namecheap.com/support/knowledgebase/article.aspx/9645/2208/how-do-i-link-my-domain-to-github-pages/), the DNS check was a success!

![DNS check successful](/Pastedimage20231126022435.png)

However, at this point, I couldn't figure out how to actually install Jekyll and set up the themes correctly. So I decided that I would explore my second option, which was Hugo. 
## The Hugo Experiment

### Getting Started with Hugo

Installing Hugo on Windows was a breeze: `winget install Hugo.Hugo.Extended`. The [quick start guide](https://gohugo.io/getting-started/quick-start/) was equally straightforward, and soon I had a local site skeleton.

![Hugo skeleton site](/Pastedimage20231127004713.png)

### GitHub and Custom Domain Integration

After pushing my Hugo site to a new GitHub repository, I used [this guide](https://gohugo.io/hosting-and-deployment/hosting-on-github/) for hosting and GitHub actions. Then, I directed the GitHub Pages in the repo settings to my custom domain.

![Setting custom domain in GitHub](/Pastedimage20231220124814.png)

However, the result wasn't quite what I expected. There was an unwanted subpage. A simple CNAME addition to the base repo set to yichendong.com fixed it.

## Setting Up PaperMod Theme

### Choosing PaperMod

The [PaperMod theme](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-installation/) caught my eye. After downloading it and updating the `config.toml` file, I was halfway there.

### Configuring the Theme

I needed to add more options to the configuration, as detailed in my [hugo.yaml](https://github.com/yichen-dong/yichen_blog_hugo/blob/main/hugo.yaml) file. This involved setting up menu items, home page info parameters, and adding functionalities like `ShowShareButtons` and social icons. The [PaperMod features page](https://adityatelange.github.io/hugo-PaperMod/posts/papermod/papermod-features/) was a great help.

Running `hugo server` throughout this process was a game-changer for quick iterations and previews.

And there you have it! That's how I quickly set up my data science website within two days (it would have been only a few hours, but I went down some wrong paths.) Hopefully this helps you set up a blog on Github Pages as well. 