# Language and Data Intelligence Laboratory Website

The Language and Data Intelligence Laboratory (LDI) website is built using [Jekyll](https://jekyllrb.com/), a static site generator. This allows us to easily create and maintain a dynamic website with minimal effort. Moreover, Github Pages natively supports Jekyll, making it easy to deploy the website just by commiting the current folder.

## Build and Deploy Locally

### Testing the website locally with Bundle

After cloning the repository, one may want to run the website locally to see the changes before deploying it to the main repository.
Hopefully, Jekyll got you covered, and you can run the website locally with the following command:

```bash
bundle exec jekyll serve --baseurl=""
```

The website will be available at `http://localhost:4000/`. (Even though you run the command on a remote dev container.)
If you get any error, you can refer to this page for help: [Github Pages run your Jekyll locally for testing](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

### Building the static website locally

*This section concerns the local development of the website. If you want to deploy the website to Github Pages, no actions are needed except pushing the changes to the `master` branch.*

In order to build the website, you will need to have [Ruby](https://www.ruby-lang.org/en/) and [Bundler](https://bundler.io/) installed.

Execute the following commands to build the website:
```bash
bundle install \
    && bundle exec jekyll build
```

The generated website could be located under `_site/`. That is the folder you will need to deploy.

## Change data

### Publications

Under `_data/publications.yml` you will find the list of publications.
They are organized as follow:
```yaml
- year: <Year regrouping all the papers>
  papers:
    - title: Title of paper 1
      authors: Author 1, Author 2
      venue: Venue Year
      url: [Optional] <URL to the paper>
    - title: Title of paper 2
      authors: Author 3
      venue: Venue 2 Year
```

### People

Under `_people/`, each member is represented through a markdown file.
Please adopt the filename as follow: `<family name lowercased><first letters of each symbol>.md`

Content:
```yaml
---
short_name: <filename>
name: Family First
korean_name: 
position: <M.S. Student | Integrated M.S./Ph.D. Student | Ph.D. Student | Professor> (Please respect the exact format)
department: Department of Computer Science and Engineering
interests:
 - "Interest 1"
 - "Interest 2"
education:
 - Please always use <Type (M.S. | Ph.D. | B.S.)> in <Field>, <University> <Year> format. From most recent to oldest.
mail: <your mail>
website: [Optional] <your website>
office: <your office>
photo: <file name with extension under _assets/images/people>
---
[Optional] Biography or whatever you want in the markdown format
```

Don't forget to add the photo under `_assets/images/people/`.

To add alumnis, please head to `_data/alumnis.yml` and follow the same format as for the publications:
```yaml
- type: <Ph.D. or M.S.>
  alumnis:
    - name: FirstName FamilyName
      year: 20..
      website: [Optional] <URL to personal webpage>
    - name: FirstName2 FamilyName2
      year: 20..
```

## Website Info

The CSS isn't relying on any framework, it's all custom made.
The website is responsive and should work on all devices.

The SNU logo is from the official website. The LDI logo is custom made.
The SVG icons are from bootstrap icons and the one on the homepage are AI generated [here](https://svg.io/).

If you need any help, feel free to ask Romain Storaï (romsto@snu.ac.kr)

### Jekyll plugins

The website uses the following plugins:
- jekyll-sitemap: to generate the sitemap (sitemap.xml & robots.txt)
- jekyll-seo-tag: to generate the SEO tags