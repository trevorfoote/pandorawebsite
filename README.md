# pandorawebsite

Website for the Pandora Mission.

## How does the website update?

The website updates via **GitHub Actions** which means **whenever a pull request is merged, the website is automatically updated to reflect the changes**. To update the website **someone with admin access needs to merge a pull request**. There are some instructions below about different ways you might want to do this.

### Making small changes to existing pages (I don't have admin access).

If you need to make a small (e.g. wording) change to the website content you can find the page you need (usually in `docs` on the `master` branch), click the pencil icon at the top (see below) and then edit the file. You then click "Create a new branch for this commit and start a pull request" and hit the "Commit changes" button.

![](docs/assets/devimage1.png)

This will open a new PR. Someone with admin access on the website repository will merge your PR and the changes will go live!

### Making small changes and making new pages/content (I don't have admin access).

If you want to, for example, update an image on the website, you should be able to use the github features to open a pull request in your browser, and add/amend that file. I will update with some images to show how to do that.


### Making large changes and making new pages/content (I don't have admin access).

If you need to make something new for the website that doesn't exist and it's more than just uploading a file, your best way forward is to follow these steps;

1. Fork the repository using the button at the top of this page
2. Clone the repository on your local machine
3. `cd` into the directory
4. Add the files you want to change
5. Push your changes to your fork (set up your remote, git add, git commit, git push)
6. Open a pull request to the main repo (pandoramission/pandorawebsite)

Someone will review the PR and merge it for you

If you want to additionally check on your local machine that the website looks good you can follow these steps:

After step 3 (in the working directory) type these commands from your terminal to upgrade `pip`, install `poetry`, and then install the website package.
```
        python -m pip install --upgrade pip
        python -m pip install poetry
        poetry install
```

Then use this command to serve a local copy of the website

```
      poetry run mkdocs serve
```

If you navigate to this URL in your browser you will see your local version of the website, and you can check that the content looks good: [http://127.0.0.1:8000](http://127.0.0.1:8000).

**Watch out**: If you have a fork of the website, always make sure to pull from the original repo often to get the most up to date changes before you start making any new content. You can do this using:

```
git checkout main
git remote add live https://github.com/PandoraMission/pandorawebsite
git pull live main
```


### I have admin access

You can follow any of the instructions above, merge pull requests, and the website will automatically update.

## Instructions for making a blog post

Blogposts are made in markdown. You can set up the beginning of the blogpost like this if you like:
```
# Title
*Date*
*Author: First Last*

**Some TL;DR for the blogpost**
```

To make a blog post you should use the following structure:

```
docs/
.... blogposts/
........ blogpostNUMBER.md
........ blogNUMBER/
............ figurename.png
............ otherfigurename.png
............ ...
```

And then add your images into markdown as you usually would (`![alttext](figurename.md)`)

At the bottom you can add a `spotlight` on the author, which will pull in their avatar and their bio. You have to use the name of the file in the `docs/authors/` directory, which is usually people's last name. Here's an example of what to put at the bottom of the blog for a spotlight:

```
!!! author "About the Author"

    {%
       include-markdown "../authors/hedges.md"
    %}
```

Once you've written your blogpost in markdown you'll need to do the following to make sure it goes live on the Website

1. Edit the `mkdocs.yml` file to add your blogpost, e.g.:
```
- Blog:
  - blogposts/blogpost1.md
  - blogposts/blogpost2.md
  - blogposts/blogpost3.md
```
2. Open a pull request and have someone with admin access merge the blogpost into the repo.
