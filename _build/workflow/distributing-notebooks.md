---
title: 'Distributing Assignments'
prev_page:
  url: /workflow/pushing-to-github
  title: 'Uploading Files to Github'
next_page:
  url: /workflow/collecting-grading-assignments
  title: 'Collecting and Grading Assignments'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# Distributing Notebooks

We recommend using interact links to distribute notebooks to students. Interact links are described in detail below. If you do not wish to use interact links, you can distribute assignments through bCourses as well. In this case, after you have uploaded the files to bCourses, students will need to download them and then upload them to their own JupyterHub accounts.

### The Steps

Here are the basic steps you will need to go through to distribute notebooks and other files. To learn more about the details of the process, please read through the rest of this page.

1. Create a folder with all files for the assignment \(notebook, datasets, etc.\)
2. [Upload folder to a public GitHub repository](/workflow/pushing-to-github.md)
3. Generate an interact link for the folder using the interact link generator (more on this below)
4. Distribute the link to students through some web page

### What are interact links?

Interact links simplify the assignment distribution process. Rather than downloading files from an external source and then uploading to their personal JupyterHub accounts, users can obtain all files for a given assignment with just one click. When a user clicks on an interact link for a particular assignment, all files for the assignment will show up in the user's personal JupyterHub account.

These links can be used with any content stored on GitHub in a public repository. Interact links can be generated for an entire repository, or a particular file or folder. When a link is clicked, a series of Git commands are run from the user's JupyterHub account, which is why interact links must be used with content on GitHub. They cannot be used to pull arbitrary files from sources other than GitHub.

Using these links enables users to immediately interact with publicly available content on GitHub. This is valuable for easy assignment distribution, but also in the broader context of using the open-source content that is available on GitHub. Learning Git is no longer a barrier to interacting with this content.

### How do interact links work?

Here is an interact link with the various components highlighted in different colors. The grey portions of the link are needed for formatting and will remain the same for each links. The colored portions will be different for each link. If you are new to GitHub you may want to familiarize yourself with the basics \(repositories, branches, etc.\) to better understand each component.

![link components](link-components.png)

The above link does the following:

* Clones the repo `ds-modules/SW-282` into the user's account on `https://datahub.berkeley.edu`
* Checks out to the `master` branch (this is the default, but specifiable on nbgitpuller)
* Opens the file `lab04/lab04.ipynb` on `datahub.berkeley.edu`. The full path of this file on the user's JupyterHub account would be `~/SW-282/lab04/lab04.ipynb`.

### Restrictions

To use an interact link, files must be stored in a public GitHub repo. Interact links will not work with private repositories. Previously, content had to be stored in the `data-8` GitHub organization or in an approved account or organization. This no longer applies, interact links can be used with content stored in ANY public repository.

### **Interact Link Generator**

Interact links can be manually created in the format shown above, or can be automatically generated using [this](https://jupyterhub.github.io/nbgitpuller/link?hub=https://datahub.berkeley.edu&repo=https://github.com/ds-modules/) tool. The interact link generator tool allows users to specify a JupyterHub URL and GitHub url as inputs. The tool will generate an interact link for the specified GitHub content and JupyterHub.

![nbgitpuller](nbgitpuller.png)

For example, to pull [this repo](https://github.com/ds-modules/SW-282/tree/master/lab04/lab04.ipynb) into DataHub, we would fill out the nbgitpuller link generator with:

1. Fill in the JupyterHub URL field with `https://datahub.berkeley.edu`
2. Paste the GitHub URL **to the repo** in the Git Repository URL field: `https://github.com/ds-modules/SW-282`
3. Leave the Branch field blank, because it defaults to `master`
4. Fill in the File to Open field with the path to the file: `lab04/lab04.ipynb`

After finishing these steps, the link in the grey text box will be your interact link. Note that the link to the link generator above will pre-fill the JupyterHub URL and GitHub URL fields, **but it will not paste in the repo**, so you will need to add the name of the repo to the GitHub URL field, as well as fill in the (optional) branch and file path fields.


<!--

For example, to pull [this](https://github.com/data-8/mcb-88-connector/tree/gh-pages/exercises/lab5) folder into a JupyterHub account on `datahub.berkeley.edu:`

* Select `datahub.berkeley.edu` as the desired hub
* Paste the GitHub url [https://github.com/data-8/mcb-88-connector/tree/gh-pages/exercises/lab5](https://github.com/data-8/mcb-88-connector/tree/gh-pages/exercises/lab5) into the generator
* Hit the convert button 

The output should be [https://datahub.berkeley.edu/user-redirect/interact?account=data-8&repo=mcb-88-connector&branch=gh-pages&path=exercises/lab5](https://datahub.berkeley.edu/user-redirect/interact?account=data-8&repo=mcb-88-connector&branch=gh-pages&path=exercises/lab5). This link will copy the desired folder into your JupyterHub account.

-->

#### **Important Note**

The technology behind interact links, called nbgitpuller, pulls _all files_ from a repo into the user's DataHub account. This means that **you should not store unfinished materials and answer keys in the same repo as published assignments**. Any interact link for a published assignment would also distribute the unfinished materials and answer keys to the students, which you probably do not want. Instead, **we recommend that you use a public repo for published assignments and a private repo for unfinished materials and answer keys**.