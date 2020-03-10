## Initial File Organization/Content for MDN Documents within the Yari Repo

|Status       | proposed <!--becomes accepted, rejected or superseded later-->|
|-----------------|-----------------------------------------------------------|
|**Proposed**     | 2020-03-10
|**Accepted**     | (the date the proposal was accepted/rejected)
|**Driver**       | Ryan Johnson
|**Approver**     | TBD
|**Consulted**    | Peter Bengtsson
|**Informed**     | MDN team and community

### Context

The organization and content of the MDN document files in GitHub must provide the information necessary to at least answer these fundamental questions: what are any given document's parents, children, and translations, and how are redirects handled when documents are moved?

In addition, because MDN would of course have had an extensive history as a Wiki prior to any move to GitHub, our GitHub content would also have to be able to answer some questions that can only be answered by carrying forward some historical data from the Wiki: when was any given document last modified within the Wiki, and who were the contributors to any given document prior to the move to GitHub?

### Decision

We prepose the following **initial** priniciples for the file organization/content of
MDN documents within the Yari repo:

1. The documents will be stored hierarchically under a common root folder called **_content_**.
1. The second level of hierarchy will be folders for each of the locales, so for example all of the English documents would reside (hierarchically) under **_content/en-us_** and all of the French documents under **_content/fr_**.
1. The actual locale will be derived from the locale folder name, where the language code will always be lowercase and the country-code, if present, always uppercase. For example, `en-US` would be the locale used for the folder _**en-us**_.
1. The English documents will be the standard or authoritative documents from which the localized versions will be translated.
1. A document's folder hierarchy intuitively corresponds to its URL slug, but they're not always exactly the same. In other words, although a document's folder hierarchy below each locale folder will exactly match its slug in terms of depth (i.e., number of folders/segments), they may not exactly match in terms of the names of their segments. This is because some of the path segments of a slug may be illegal folder names for a Unix or Windows file system, and of course contributors may be on a Unix or Windows file system when they clone the GitHub repo. For example, under the English locale folder (**_content/en-us/_**), **_web/css/-moz-locale-dir(ltr)_** would be the folder hierarchy for the English slug **_Web/CSS/:-moz-locale-dir(ltr)_**. The folder **_web/css/-moz-locale-dir(ltr)_** and slug **_Web/CSS/:-moz-locale-dir(ltr)_** have the same depth or number of segments, but they differ in the name of the last segment **_-moz-locale-dir(ltr)_** vs **_:-moz-locale-dir(ltr)_**. This is because the `:` character is illegal as part of the name of a file/folder on Windows systems.
1. The ancestral relationships for any given document are definitively provided by its slug, both in terms of depth and names. For example, a document whose `slug` is **_Web/HTML/Microdata_** would have the parents **_Web/HTML_** and **_Web_**, or conversely the children of the document **_Web_** would be **_Web/HTML_** and **_Web/HTML/Microdata_**.
1. Each document, at any point in the folder hierarchy, will be represented by 3 files: **_index.html_**, **_index.yaml_**, and **_wikihistory.json_**. The **_index.html_** file will contain the document's raw HTML (i.e., HTML with any embedded Kumascript macros), and the **_index.yaml_** file will contain the document's metadata. The **_wikihistory.json_** file will contain any historical Wiki metadata for the document that needs to be carried forward into GitHub. The **_wikihistory.json_** file is never modified after it is created (i.e., it's read only), and could be YAML instead of JSON if desired.
1. Each English document's metadata will comprise, for now, 2 pieces of information: the `slug` and the `title`. So, for example:
   ```yaml
   title: Microdata
   slug: Web/HTML/Microdata
   ```
1. Each non-English document's metadata will comprise, for now, 3 pieces of information: the `slug`, the `title`, and the `translationOf` (the slug of the _English_ document from which this translation was created). The `translationOf` key provides the means to link a set of documents as translations of each other, and is similar to Hugo's `translationKey`.
   ```yaml
   title: Microdonnées
   slug: Web/HTML/Microdonnées
   translationOf: Web/HTML/Microdata
   ```
1. The contents of the **_wikihistory.json_** file will comprise, for now, 2 pieces of information: `modified` (when the document was last modified in the Wiki) and `contributors` (a list of all of the MDN account usernames that contributed to the document prior to the move to GitHub).
1. Of course, sometimes documents are moved from one slug to another. Within MDN today, many of the Wiki documents are simply content-based redirects reflecting a move from one slug to another. These existing content-based redirects, as well as any future document movements, will **not** be represented by the 3 files described above. Instead, each of these redirects, a _from_ URL followed by a _to_ URL, are listed, one per line, in a separate _**_redirects.txt**_ file, one file for each locale. For example, all of the English redirects would be listed within _**content/en-us/_redirects.txt**_ like this:
   ```
   # FROM-URL	TO-URL
   /en-US/docs/<img>	/en-US/docs/Web/HTML/Element/img
   /en-US/docs/AJAX	/en-US/docs/Web/Guide/AJAX
   ...
   ```

Here's a small sample of the actual directory structure that provides a better picture of the hierarchy and files:
```
content/
    en-us/
        api/
        web/
            html/
                microdata/
                    index.html
                    index.yaml
                    wikihistory.json
                index.html
                index.yaml
                wikihistory.json
            index.html
            index.yaml
            wikihistory.json
    fr/
        api/
        web/
            css/
            html/
                microdonnées/
                    index.html
                    index.yaml
                    wikihistory.json
                index.html
                index.yaml
                wikihistory.json
            index.html
            index.yaml
            wikihistory.json
```

### Consequences

This decision affects both the developers writing the code that renders/builds the final documents from this information, but also of course content-creators and contributors. The intention here however is not to arrive at a final solution set in stone, but rather to document our initial solution from which we'll begin iterating.

### Alternatives Considered

Here are two GitHub issues that document some of the process in arriving at these decisions:
- https://github.com/mdn/kuma/issues/6441
- https://github.com/mdn/kuma/issues/6124
