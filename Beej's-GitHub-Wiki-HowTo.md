## Questions

* Does this actually work well with our workflow?
* How does it mesh into the `README.md`'s we have in the assignment/code skeleton repos?
* Is it easier to use and maintain than Google Docs?

## Good Stuff

Syntax highlighting:

```c
#include <stdio.h>

int main(void)
{
   printf("Hello, world!\n");
   return 0;
}
```
Pages written in markdown.

Can clone the wiki and edit markdown in the editor of your choice.

## Bad stuff

A little clunky on searching; see below.

Can't make subdirs from within the UI; need to clone and do it from the command line.

Inserting images not as smooth as in the main repo markdown files.

## Searching

### By Page Title

Type in the "Pages" bar on the right to search by page title.

### By Page Content

Enter the search text in the top-of-page search bar. On the results page, click the "Wikis" subtab.

This link gets you to the Wikis subtab directly, after which you have to type a search term up top: https://github.com/beejjorgensen/wiki-test/search?type=Wikis&utf8=%E2%9C%93

## Cloning the Wiki Repo

1. Go back to the main repo page (the `<> Code` tab).
2. Copy the clone ssh URL
3. Add the word `.wiki` just before the `.git`, like so: `git@github.com:beejjorgensen/wiki-test.wiki.git`

## Subdirectories in the Repo

Although the wiki displays as flat, you can have subdirectories. However, you must make them from the command line in a clone of the wiki.

Even though it's possible to add custom sidebars and footers in subdirectories, it's not recommended. The web UI is hardcoded to overwrite the root header/sidebar file, even if you edit one in a subdirectory.

## Inserting Images

[Adding Images to Wikis](https://help.github.com/articles/adding-images-to-wikis/) (GitHub help)

![Learn!](https://github.com/beejjorgensen/wiki-test/blob/master/wiki-images/learn-goddammit.jpg)

`![Learn!](https://github.com/beejjorgensen/wiki-test/blob/master/wiki-images/learn-goddammit.jpg)`

## References

[GitHub wiki help](https://help.github.com/articles/about-github-wikis/)

[Adding Images to Wikis](https://help.github.com/articles/adding-images-to-wikis/)

[Beginner's Guide to GitHub Wiki](https://guides.github.com/features/wikis/)

[GitHub wiki reference](https://help.github.com/categories/wiki/)

[Viewing wiki change history](https://help.github.com/articles/viewing-a-wiki-s-history-of-changes/)

[Cloning wiki repo via ssh](https://stackoverflow.com/questions/42493135/is-it-possible-to-access-a-github-wiki-via-ssh)


