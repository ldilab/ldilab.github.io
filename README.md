# Language and Data Intelligence Laboratory Website

The Language and Data Intelligence Laboratory (LDI) website is built using [Jekyll](https://jekyllrb.com/), a static site generator. This allows us to easily create and maintain a dynamic website with minimal effort.

## Build and Deploy

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
    - title: Title of paper 2
      authors: Author 3
      venue: Venue 2 Year
```

### People

Under `_members/`, each member is represented through a markdown file.
Please adopt the filename as follow: `<family name lowercased><first letters of each symbol>.md`

Content:
```yaml
---
short_name: <filename>
name: Family First
korean_name: 
position: <M.S. Student | Ph.D. & M.S. (integrated) Student | Ph.D. Student | Professor> (Please respect the exact format)
department: Department of Computer Science and Engineering
interests:
 - "Interest 1"
 - "Interest 2"
education:
 - Please always use <Type (M.S. | Ph.D. | B.S.)> in <Field>, <University> <Year> format. From most recent to oldest.
mail: <your mail>
website: [Optional] <your website>
photo: <file name with extension under _assets/images/people>
---
```

Don't forget to add the photo under `_assets/images/people/`.

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