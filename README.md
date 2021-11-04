# Sailfish OS Documentation

Welcome to the Sailfish OS Docs source repo.

* [Edit and contribute](#edit-and-contribute)
   * [Just the documentation](#just-the-documentation)
   * [Changes to HTML (Jekyll template)](#changes-to-html-jekyll-template)
      * [Preview via GitHub Pages](#preview-via-github-pages)
      * [Preview on your desktop](#preview-on-your-desktop)
   * [Common pitfalls](#common-pitfalls)
      * [Tables](#tables)
      * [URLs](#urls)
      * [Syntax highlighting](#syntax-highlighting)
      * [Templates and forgotten ./precheckin.sh](#templates-and-forgotten-precheckinsh)
* [Feedback](#feedback)
* [Credits](#credits)

## Edit and contribute

### Just the documentation

Simply edit a chosen `README.md` file and preview the changes before
creating a PR.

Match existing docs source style, wrap your added lines after 72 chars, but
**please** do not continue text-wrapping the rest of the paragraph --
this will make it harder to see what you actually changed or added.

Final text wrapping will have to be done by a maintainer just before
merging.

IMPORTANT: please read about [the common pitfalls](#common-pitfalls).

### Changes to HTML (Jekyll template)

If you would like to improve the website itself (style, layout,
browser fix etc.), you should test your changes before creating a PR:

#### Preview via GitHub Pages

Fork this repo, then go to Settings | Pages | Source and choose the
`master` branch. After a short while, you will find a copy of the docs
published under `https://yourusername.github.io`.

As soon as you commit a change, the published website will shortly
update itself.

#### Preview on your desktop

To build on your local machine, perform the following commands:
```nosh
sudo apt install git ruby-bundler ruby-dev gcc g++ make
git clone https://github.com/sledges/sledges.github.io
cd sledges.github.io/
sudo gem install bundler
bundle config set --local path 'vendor/bundle'
bundle install
bundle exec jekyll serve
```

### Common pitfalls

#### \<tags\>

The following Markdown `zypper install <package_name>` will be rendered as
**zypper install**, and <package_name> is lost in GitHub Pages.

To avoid, always escape correctly: `zypper install \<package_name\>`.

#### Tables

* Markdown does not support header-less tables, so please come up with a
  name for each column, to avoid an empty row at the top.

* GitHub Pages does not render tables that have only one row, thus
  please come up with a header row for it too.

* Markdown doesn't support `rowspan` and `colspan`. The latter can be
  worked around by giving each column a more granular name.

  Instead of `rowspan`, use a
  [_ditto_](https://en.wikipedia.org/wiki/Ditto_mark) mark to show that
  a cell has the same content as the cell above: `<center>"</center>`.

  If you absolutely must defy the purpose of using Markdown, then it's
  possible to achieve `rowspan` `colspan` functionality by writing your
  tables in HTML inside a `*.md` file.

* Yes, we know that tables with long text in a cell look way too wide in
  Markdown's source, and cannot be rectified because it doesn't support
  line breaks in them. But if a cell is that big, maybe it shouldn't be
  a table in the first place? ;)

#### URLs

It's good practice to surround URLs: `<http://some.url>`. GitHub will
linkify even non-surrounded ones, but some Markdown renderers don't.
Thus please increase portability of these Markdown docs.

#### Syntax highlighting

* When using Markdown's syntax highlighter, you can find the list of
  Markdown supported syntax highlighters
  [here](<https://github.com/github/linguist/blob/master/lib/linguist/languages.yml>).

* Most if not all will correctly appear in your GitHub web editor
  preview. However **not all** of them will be highlighted in GitHub
  Pages due to an unknown limitation.

  The following do not to work at the time of writing: `gitattributes,
  qmake, specfile, ssh-config, wiki`.

  The following are rendered/coloured incorrectly in Pages (but correct
  in GitHub editor preview): `ini`

* Shell script syntax highlighter has been disabled (simply by
  identifying a code block as `nosh` instead of `sh`) because it does
  more harm than good. E.g. it always highlights `exec`, but doesn't
  know that it shouldn't highlight when `exec` is an argument to `sfdk`.

#### Templates and forgotten `./precheckin.sh`

If you are modifying a template (`*.mdpp` file), don't forget to run
`./precheckin.sh` before committing.

## Feedback

Please create a report in the
[Issues](https://github.com/sledges/sledges.github.io/issues)
section.

## Credits

The following content generators are being used additionally:

* [Jekyll Pure Liquid Table of Contents](https://github.com/allejo/jekyll-toc)
  - On every page the table of contents gets generated from all its headings
