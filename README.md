# al-folio

A simple, clean, and responsive [Jekyll](https://jekyllrb.com/) theme for academics.
If you like the theme, give it a star ⭐!

## Test change to trigger deploy workflow

[![Preview](readme_preview/al-folio-preview.png)](https://alshedivat.github.io/al-folio/)

**al-folio** is based on the [\*folio theme](https://github.com/bogoli/-folio) (published by [Lia Bogoev](https://liabogoev.com) and under the MIT license).
The theme is available as-is under the MIT license. However, if you make it big, don't forget us :wink:

Currently, **al-folio** provides the following features:
- Clean, responsive design based on [Bootstrap 5](https://getbootstrap.com/)
- Integrated [Font Awesome](https://fontawesome.com/) icons
- Beautiful theme colors inspired by the [Distill theme](https://github.com/distillpub/template)
- Automatic Light/Dark mode toggling
- Support for [GitHub's Emoji API](https://github.com/jekyll/jemoji)
- Support for [Jekyll Tabs](https://github.com/Ovski4/jekyll-tabs)
- Support for [typograms](https://github.com/jcoglan/typograms)
- Mathematical expressions using [MathJax](https://www.mathjax.org/)
- Interactive plots using [Plotly](https://plotly.com/javascript/)
- Interactive maps using [Leaflet](https://leafletjs.com/)
- Code syntax highlighting using [Highlight.js](https://highlightjs.org/)
- Automatic bibliography generation using [Jekyll Scholar](https://github.com/inukshuk/jekyll-scholar)
- Twitter integration using [Jekyll Twitter Plugin](https://github.com/rob-murray/jekyll-twitter-plugin)
- Support for displaying [Altmetric](https://www.altmetric.com/) badges
- Support for [Disqus](https://disqus.com/) comments
- Support for [Giscus](https://giscus.app/) comments
- Automatic sitemap generation using [Jekyll Sitemap Generator](https://github.com/jekyll/jekyll-sitemap)
- Automatic RSS feed generation using [Jekyll Feed](https://github.com/jekyll/jekyll-feed)
- Automatic broken links checks using [Broken Link Checker](https://github.com/stevenvachon/broken-link-checker)
- Automatic lighthouse audits using [Lighthouse GitHub Action](https://github.com/treosh/lighthouse-ci-action)
- SEO/Social media friendly using [Jekyll SEO Tag](https://github.com/jekyll/jekyll-seo-tag)
- Media embedding using [Jekyll Picture Tag](https://github.com/rbuchberger/jekyll_picture_tag)
- Jupyter notebooks display using [Jekyll Jupyter Notebook plugin](https://github.com/red-data-tools/jekyll-jupyter-notebook)
- Support for [Vega-Lite](https://vega.github.io/vega-lite/) charts
- Support for table of contents using [Jekyll Table of Contents](https://github.com/toshimaru/jekyll-toc)
- Easy Google Analytics integration using [Jekyll Google Analytics](https://github.com/jekyll/jekyll-analytics)
- Easy YouTube video embedding using [Jekyll YouTube](https://github.com/dommmel/jekyll-youtube)
- GitHub's repositories information using [GitHub Metadata](https://github.com/jekyll/github-metadata)

## Getting started

Want to learn more about Jekyll? Check out [this tutorial](https://www.taniarascia.com/make-a-static-website-with-jekyll/).
Why Jekyll? Read [Andrej Karpathy's blog post](https://karpathy.github.io/2014/07/01/blog/)!

### Installation

For a hands-on walkthrough of al-folio installation, check out [this cool video tutorial](https://www.youtube.com/watch?v=g6AJ9qPPoyc) by one of the community members! 🎬 🍿

---

#### Local setup using Docker (Recommended)

Using Docker to install Jekyll and Ruby dependencies is the easiest way to set up your environment.

You need to take the following steps to get `al-folio` up and running on your local machine:

- First, install [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/).
- Finally, run the following command that will pull the latest pre-built image from DockerHub and will run your website.

```bash
$ docker compose pull && docker compose up
```

Note that when you run it for the first time, it will download a docker image of size 400MB or so. 

Now, feel free to customize the theme however you like (don't forget to change the name!). After you are done, you can use the same command (`docker compose up`) to render the webpage with all you changes. Also, make sure to commit your final changes.

<details><summary>(click to expand) <strong>Build your own docker image (more advanced):</strong> </summary>

> Note: this approach is only necessary if you would like to build the image yourself or if you are running it on a platform that is not supported by the multi-arch image.

Build and run a new image using:

```bash
$ docker compose -f docker-compose-slim.yml up --build
```

> If you want to update jekyll, install new ruby packages, etc., all you have to do is build the image again using `--force-recreate` argument at the end of the previous command! It will download Ruby and Jekyll and install all Ruby packages again from scratch.

</details>

---

#### Local Setup (Standard)

Assuming you have [Ruby](https://www.ruby-lang.org/en/downloads/) and [Bundler](https://bundler.io/) installed on your system (*hint: for ease of managing ruby gems, consider using [rbenv](https://github.com/rbenv/rbenv)*), and also [Python](https://www.python.org/) and [pip](https://pip.pypa.io/en/stable/):

```bash
$ bundle install
# assuming pip is installed
$ pip install jupyter
$ bundle exec jekyll serve
```

Now, feel free to customize the theme however you like (don't forget to change the name!).
After you are done, **commit** your final changes.

---

## Deployment

Deploying your website to [GitHub Pages](https://pages.github.com/) is the most popular option.
For other deployment options, check out the [Deployment](https://github.com/alshedivat/al-folio/wiki/Deployment) wiki page.

### GitHub Pages

The quickest way to deploy your website to GitHub Pages is to use the [al-folio-actions](https://github.com/alshedivat/al-folio-actions) GitHub Action.

1. Click [**Use this template**](https://github.com/new?template_name=al-folio-actions&template_owner=alshedivat) button above. Make sure to select all branches (not just main) to have access to automatic deployments! Also, make sure to select `Include all branches` as shown in the screenshot below.

    <img width="400" alt="Enable all branches" src="https://user-images.githubusercontent.com/2901215/230615080-ba64d6ec-122e-4956-9b19-b74900de4fed.png">

2. Fix any name conflicts, then click on **Create repository from template**.
3. After few minutes, your website should be deployed and accessible at `https://<your-username>.github.io/<your-repo-name>/`.
4. To enable automatic deployments after each new commit, go to Settings -> Actions -> General -> Workflow permissions, and give Actions read and write permissions.

<details><summary>(click to expand) <strong>Manual deployment to GitHub Pages:</strong></summary>

If you are using a private repository, then you may want to deploy using the manual way. For that, you need to do the following:

1. Create and checkout a new `gh-pages` branch:
    ```bash
    $ git checkout --orphan gh-pages
    ```
2. Remove all files in this branch and commit an empty commit:
    ```bash
    $ git rm -rf . && git clean -fxd
    $ git commit --allow-empty -m "Initial empty commit"
    $ git push origin gh-pages
    ```
3. Checkout to your main branch.
4. Build your site using Docker:
    ```bash
    $ docker compose -f docker-compose-deploy.yml up
    ```
5. Navigate to the `_site/` folder and check out the `gh-pages` branch:
    ```bash
    $ cd _site && git checkout gh-pages
    ```
6. Add all the contents in this directory to the `gh-pages` branch and push it to GitHub:
    ```bash
    $ git add . && git commit -m "Deploy" && git push origin gh-pages
    ```
7. Wait for few minutes and then your website should be deployed at `https://<your-username>.github.io/<your-repo-name>/`.

</details>

<details><summary>(click to expand) <strong>Deployment to other hosting services:</strong></summary>

For deployment to other hosting services, check out the [Deployment](https://github.com/alshedivat/al-folio/wiki/Deployment) wiki page.

</details>

## FAQ

For frequently asked questions, check out the [FAQ](https://github.com/alshedivat/al-folio/wiki/FAQ) wiki page.

---

## License

The theme is available as open source under the terms of the [MIT License](https://github.com/alshedivat/al-folio/blob/master/LICENSE).

Originally, **al-folio** was based on the [\*folio theme](https://github.com/bogoli/-folio) (published by [Lia Bogoev](https://liabogoev.com) and under the MIT license).
Since then, it got a full re-write and many additional cool features.
