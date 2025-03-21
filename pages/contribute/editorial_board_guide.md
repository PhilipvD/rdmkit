---
title: Editorial board guide
summary: This guide is there to help editors.
---

## All you need to know about this GitHub repository

### General rules

As an editor, try to work as much as possible on a different branch than the master branch. This can be on the elixir-europe rdm-toolkit repo or your own fork. Open a pull request if you want to merge your changes with the master branch. This way it is possible for other editors to give feedback on your changes. Typos or other small fixes can of course be done immediately on the master branch.

### The google doc way of contributing
This process is sketched below.

{% include image.html file="googledoc_way_flow.svg" alt="Process of contributing via Google docs" click=true %}

### Overview of the file structure in GitHub

The content of the website is built up using markdown files found in the [pages](https://github.com/elixir-europe/rdmkit/tree/master/pages) directory.
These markdown files are divided over subdirectories (your_role, your_domain, your_tasks...) for sorting reasons only.

### The metadata/frontmatter of the markdown file

In order to render the markdown file to the website, it needs a specific frontmatter/metadata section in the top part of the file. This latter can look like:

```
---
title: Title of the page
---
```

Mandatory metadata/frontmatter:
* `title`: Specify here the page title. This will be the H1 title (replacing the top level title using the # in markdown )

Optional metadata/frontmatter: 

* `summary`: By using this attribute it is possible to specify a summary which will be displayed under the page title.

* `description`: Short sentence about the page starting with a lowercase. This sentence is visualized when pages are automatically listed as Related page.

* `contributors`: List here all the contributors that helped in establishing the page, preferibly with their full name. Make sure that the person names that are listed can be found in the CONTRIBUTORS.yaml file in the *_data* directory if you want to link the GitHub ID and other contact information. Multiple contributors will be put in a list like this: [example1, example2].

* `coordinators`: List here the names of the people responsible for the content of the page. People responsible for the content of the National resources pages can be members of the ELIXIR data management network. Make sure that coordinators also listed as contributors in `contributors` and CONTRIBUTORS.yaml. Multiple coordinators will be put in a list like this: [example1, example2].

* `search_exclude`: By setting this field to "true", the page will not end up in the search results of the search bar. `search_exclude: true` is the default for template pages. Make sure to delete this metadata field when creating a new page for contributors, before approving or before merging a pull request.

* `sitemap`: let the page appear in the sitema.xml. Default: true

* `no_robots`: by setting this field to true, the page will not end up in the search results of google or any other search engine.

* `hide_sidebar`: When true, the sidebar will be hidden. Default: false.

* `custom-editme`: This attribute can be used to specify an alternative file/link when clicked on the edit-me button.

* `keywords`: List here all the keywords that can be used to find the page using the search box in the right-upper corner of the page. Multiple keywords are put in a list like this: [example1, example2].

* `sidebar`: Specify here an alternative sidebar. Default: main.

* `toc`: When set to false, the table of contents at the beginning of the page will not be generated.

* `affiliations`: List here all affiliations that made this page possible. This is especially used for tool assembly pages. Countries use the ISO 3166-1-alpha-2 notation, other affiliations must be present in the affiliations.yaml in the _data directory in order to work.

* `page_id`: Unique identifier of a page. It is usually a shortened version of the page name or title, with small letters and spaces, or an acronym, with capital and small letters. Used to list Related pages.

* `related_pages`: List here the page_id of RDMkit pages that you want to display as Related pages, grouped by section (Your tasks, Your domain, Tool assembly).

  If you want pages from the specific section (Your tasks, Your domain, Tool assembly) to be shown here as Related pages, list their `page_id`. If you want to list multiple related pages, make sure to put them in a list like this: [page_id1, page_id2]. The specific sections allowed in each page are specified in each page template. Please, do not add extra sections in the metadata of the page.
  ```yml
  related_pages: 
    your_tasks: [page_id1, page_id2]
    your_domain: [page_id1, page_id2]
    tool_assembly: [page_id1, page_id2]
    ``` 

* `training`: List here training material relevant for the page. We recommend to add your training material in TeSS. However, you can also list here training material that is not yet present in TeSS. Each training item will be automatically added as an entry to the table in the [All training resources page](all_training_resources).

  ```yml
  training:
    - name: Training in TeSS
      registry: TeSS
      registry_url: https://tess.elixir-europe.org
      url: https://tess.elixir-europe.org/search?q=data%20analysis

    - name: Training in TeSS
      registry: TeSS
      registry_url: https://tess.elixir-europe.org
      url: https://tess.elixir-europe.org/search?q=data%20analysis
  ```

* `faircookbook`: Here all relevant FAIR Cookbook recipes are listed. This is automaticity updated based on the `faircookbook_rdmkit_mapping.yml` mapping file. If you want to make a new link, please make a pull request against this file. Every week the changes of this mapping file are used to update the frontmatter of the corresponding markdown files.

* `dsw`: Here all relevant Data Stewardship Wizard questions in the RDMkit knowledge model are listed. This is automaticity updated and can not be altered by humans! If you want to add a link you have to add the link towards the RDMkit page the the knowledge model on DSW.

* `datatable`: Use this attribute to activate pagination, sorting  and searching in tables.

### Markdown file naming

- Markdown files should be named without capitals and without spaces (replace them with underscores).
- Make sure that the markdown file has a unique name.
- If the markdown file is named *example.md*, the page will be found at https://rdmkit.elixir-europe.org/example.
- By default a page will not show up in the sidebar. In order to do so you will have to add the link towards the page to the `.yaml` file in the *_data/sidebars* directory or link towards it from another page. More info about this can be found on the [find your page back section](#find-your-newly-added-page-back-on-the-website).

### GitHub checks

With each PR or merge to the master, some checks are done using GitHub actions. One of them checks wether the website builds correctly. The other checks for changes in the tool/resource Excel table. When each of them fails, the PR will not be able to be merged. Click on the red dot/failed check to understand better what caused the fail. 

## Label, discuss and assign issues

  * Check open issues regularly or enable notifications by clicking the "WATCH" icon in the top-right side of the [GitHub repository](https://github.com/elixir-europe/rdmkit/issues).
  * Assign labels to issues.
  * Discuss who is going to be responsible for each issue with other editors and reviewers (via issue comments or other communication channels).
  * Assign at least one editor/reviewer to the issue, who will discuss the possible content with the contributor.
  * When a Pull Request (PR) or a draft PR related to an issue is created, link the PR to the issue.
  
More information about these topics can be found in the GitHub documentation:
- [commenting on PRs](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request)
- [start a review](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/reviewing-proposed-changes-in-a-pull-request)

## Review pull requests

If contributors make a pull request to make changes, by default the editors that are responsible for files that will changed by the PR will be assigned and notified. All PR should be assigned to one of the editors. Before merging a PR, pages' tags and keywords, and tools and resources' tags should be checked and assigned according to the established tagging system.
  
## Link a pull request to an issue

When you make a pull request resolving an issue, it is possible to link this pull request to that specific issue. This can be easily done by writing in the conversation of the PR: `closes #number_of_issue`, or `fixes #number_of_issue` or even `resolves #number_of_issue`. This is definitely applicable when authors first open an issue announcing a change or requesting a new page, followed up by the pull request. 
For more information about this topic please visit the [GitHub documentation page](https://docs.github.com/en/free-pro-team@latest/github/managing-your-work-on-github/linking-a-pull-request-to-an-issue).

## Adding a new event

Add an event to the landing page by editing the `events.yml` in the `_data` directory in this repository. Use following attributes to define an event:


```yml
- name: Contentathon
  startDate: 2021-06-23
  startTime: '9:00'
  endDate: 2021-06-24
  endTime: 13:30 CET
  description: We would like to invite you to highlight your set of data management tools as a tool assembly in the RDMkit and describe how to use it, so others can do the same. (two half days)
  location: Online

```

Only name and startDate are mandatory attributes.

## Adding a news item

Add a news item to the landing page by editing the `news.yml` in the `_data` directory in this repository. Use following attributes to define a news item:


```yml
- name: News title
  date: 2021-06-23
  description: A short description
```

All attributes are mandatory.

## Create a new page

### Simple way: using the GitHub interface
To generate a new page it is sufficient to simply copy the TEMPLATE file in the subdirectory and rename it. To copy a template you have to:

1. Go to the `TEMPLATE_` file of choice in the [GitHub repo](https://github.com/elixir-europe/rdmkit/tree/master/pages), every section has its own TEMPLATE file. For example the [TEMPLATE_your_tasks.md](https://github.com/elixir-europe/rdmkit/blob/master/pages/your_tasks/TEMPLATE_your_tasks.md) file.

1. Click "Raw" on the GitHub page to open the file 'as is'
    {% include image.html file="raw_github.png" inline=true alt="Raw button GitHub." %}

1. Select and copy all the content.

1. Go back to the main section were you want to make the new page, in our example this will be in */pages/your_tasks*. Click on `Add file` on the right followed up by `Create new file`.
    {% include image.html file="create_new_file_github.png" inline=true alt="Create new file GitHub." %}

1. Paste the copied content from the template.

1. Name the file by choosing a unique self explaining short name without capitals and without spaces (replace them with underscores).
    {% include image.html file="name_file_github.png" inline=true alt="Name the file in GitHub." %}

1. Check the frontmatter/metadata of the markdown page:
    - delete `search_exclude: true` attribute.
    - add the author names to the contributors list.
    - optional: change the title into an appropriate one.

1. Describe shortly which changes you made in the description of your commit below the page. Commit to the master branch by clicking `Commit new file`.
     {% include image.html file="commit_to_master_github.png" inline=true alt="Commit new file in GitHub." %}

1. If the markdown file is named *example.md* the page will be rendered at https://rdmkit.elixir-europe.org/example. This link can be provided to the contributor through the issue.

{% include callout.html type="note" content="It is not a problem to immediately duplicate pages in the master branch, but be aware that new content always needs to be pushed to another branch which will give you the option to open a pull request." %}

### Advanced: working on your own feature branch and pushing local changes

Just like with every change you want to make to this repo, it is possible to do this through Git by working on a local copy. For more information on how to do this, please read our [working with Git](working_with_git) page.


## Find your newly added page back on the website

By default your page will not be linked in the sidebar on the website, or on the landing page, but it will exist as an orphan at *https://rdmkit.elixir-europe.org/markdown_file_name*. In order to prevent that people will not find the page back it is better to link towards it in the sidebar or get linked within an existing page. 

### Linking pages in the sidebar and frontpage

Make sure all pages are accessible from the navigation sidebar. Please, avoid generating sub-pages that are not directly accessible from the navigation sidebar.

This website supports multiple sidebars, the one in the main sections of the website is for example different from the one in the contribute section. Both of them are defined by `.yaml` files in the *_data/sidebars* directory. Changing these yaml file will immediately impact the sidebars and the frontpage of the website. The sidebar supports multiple levels and each level in the hierarchy can contain a URL to a page within this website or an external URL.

The attributes that define the structure are:
- `title`: This is the text that will show up in the sidebar.
- `url`: The URL to the internal page you want to link to. This is mostly in the form of: */markdown_file_name.html*.
- `external_url`: Use this instead of URL if you want to link to an external page.
- `subitems`: to define a sublevel.

```yaml
- title: Level_1_title
  url: level_1_url
  subitems:
    - title: Level_2_title
      url: level_2_url
```

{% include callout.html type="tip" content="Copy around existing parts in the yaml file to add pages to the same level" %}

### Link page within existing page

Avoid manual linking to internal pages. If necessary, you can manually link to the pages like this:

If the markdown page is named example_1.md, you can link towards it using:

```md
[Example 1](example_1)
```

{% include callout.html type="important" content="If you change the file name, you'll have to update all of your links." %}


## Adding extra info to the contributors

Do you want that the GitHub picture of a contributor is shown next to their name? Or maybe you want that the name is clickable and links towards the GitHub page of that person? To enable this please add the name and the necessary metadata to the [CONTRIBUTORS.yaml](https://github.com/elixir-europe/rdmkit/blob/master/_data/CONTRIBUTORS.yaml) file in the *_data* directory like this:

```yaml
Bert Droesbeke:
    git: bedroesb
    email: bedro@psb.ugent.be
    orcid: 0000-0003-0522-5674
    role: editor
    affiliation: VIB-UGent
```
{% include callout.html type="important" content="Make sure that the name in the yaml file is identically the same as the one used in the metadata of the page." %}


## Adding an institution, infrastructure, project or funder

Institutions, projects, funders and infrastructures are listed in the [affiliations.yml](https://github.com/elixir-europe/rdmkit/blob/master/_data/affiliations.yaml) file. The info in this file is used on the support page in the about section, but also for the affiliations in tool assembly pages. Make sure you make use of the same name in those assembly pages. The yaml file has following syntax:
```yaml
- name: VIB
  image_url: /images/institutions/VIB-PSB.svg
  pid: https://ror.org/03xrhmk39
  expose: true
  type: institution
  url: https://www.psb.ugent.be/
```

- `name`: name
- `image_url`: relative url towards the image
- `pid`: url including the unique identifier towards the page of the association on [ROR](https://ror.org)
- `expose`: true or false, when true this association will be shown in the about section
- `type`: can be any of these values: *institution*, *funder*, *infrastructure* or *project*
- `url`: url towards the homepage of this association


The logos can be added to the [/images/institutions](https://github.com/elixir-europe/rdmkit/blob/master/images/institutions/), [/images/projects](https://github.com/elixir-europe/rdmkit/blob/master/images/projects/), [/images/infrastructures](https://github.com/elixir-europe/rdmkit/blob/master/images/infrastructures/) and [/images/funders](https://github.com/elixir-europe/rdmkit/blob/master/images/funders/) directory.

{% include callout.html type="important" content="Upload vector images (.svg filetype) of the institute logo for better quality, scaleability and file size, if possible." %}

## Related pages

### Add "Related pages" to a page 

RDMkit pages from the sections Your tasks, Your domain and Tool assembly can be displayed as "Related RDMkit pages" in a page, grouped by section. 

Only pages from specific sections are allowed in each page (see image below), as pre-defined in the metadata of each template page. Please, do not add extra sections in the metadata of the page.

| _page_id_           | Related pages id: Data life cycle | Related pages id: Your tasks | Related pages id: Your role | Related pages id: Your domain | Related pages id: Tool assembly | Related pages visualised |
|---------------------|-----------------------------------|------------------------------|-----------------------------|-------------------------------|---------------------------------|--------------------------|
| **Data life cycle** |                                   |              yes             |                             |                               |                                 |        Your tasks        |
| **Your tasks**      |                                   |                              |                             |                               |               yes               |       Tool assembly      |
| **Your role**       |                                   |              yes             |                             |                               |                                 |         Your tasks        |
| **Your domain**     |                                   |              yes             |                             |                               |               yes               | Your tasks, Tool assembly |
| **Tool assembly**   |                                   |              yes             |                             |              yes              |                                 |  Your tasks, Your domain  |



An overview of all RDMkit pages (belonging to the sections listed above) and their `page_id` can be found in the [Website overview page](website_overview).


```yml
related_pages: 
   your_tasks: [page_id1, page_id2]
   your_domain: [page_id1, page_id2]
   tool_assembly: [page_id1, page_id2]
  ``` 


### Page ID

To find out what the `page_id` of an RDMkit page is, please check its metadata attribute `page_id` at the top of the markdown file or the [Website overview page](website_overview).
