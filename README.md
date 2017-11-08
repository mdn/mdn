# Mozilla Developer Network (MDN) on Github

Welcome to the mdn repository! This is a meta repository containing information, procedures, and resources related to all the repos inside the MDN organization — the Mozilla Developer Network's home on GitHub for demos, data, and other resources.

## Adding a new project

The MDN organization on GitHub is home to data stores used for various MDN projects, as well as for sample code, tools, and other projects that are useful to web developers as well as people documenting the open web.  We encourage contributions to existing projects, as well as the contribution of new projects that help us further our mission to teach web development.

### Structure of the MDN organization on GitHub

*Describe the structure and hierarchy and where to put different kinds of projects...*

### Project guidelines

To help ensure consistency and to make using our examples and tools as easy as possible, we have some guidelines for projects on MDN.

*Talk about the various guidelines for structuring projects.*

#### Required files

Every project on MDN needs to have the following files, at a minimum:

Name | Description
---- | -----------
[`LICENSE`](https://github.com/mdn/mdn/blob/master/LICENSE) | A text file containing the legal text for the project's license. All MDN code samples must be licensed under [CC0](https://github.com/mdn/mdn/blob/master/LICENSE) (public domain).
`README.md` | A GitHub-flavored Markdown file describing the project. *Add a link to info about the contents, if we have that.*
`contribute.json` | A text file containing a JSON object which provides details about the project. This file matches the [contribute.json schema](https://www.contributejson.org/) defined by Mozilla. Start by copying the file [`contribute.json.dist`](https://github.com/mdn/mdn/blob/master/contribute.dist.json), then make changes as needed to describe your project.

Some recommendations for your `contribute.dist` file:

* Under `"participate"`, you should provide URLs that will help potential contributors or users of the project find assistance.
    * `"home"` should always be a link to the [MDN home page](https://developer.mozilla.org/).
    * `"docs"` should be a link to a page that explains the usage of the project, or to the page on MDN most closely affiliated with the example. For example, if the project is an example that's a key part of a guide article on MDN, this URL should refer to that article.
    * `"mailing-list"` should link to a [Mozilla mailing list](https://lists.mozilla.org/listinfo) where the reader of the article can get help with the technology or concepts demonstrated by the code.
    * `"irc"` should link to an appropriate place to get help understanding the code. If an appropriate [Mozilla IRC channel](https://wiki.mozilla.org/IRC#Commonly_Used_Mozilla_IRC_Channels) exists, link to that channel. Otherwise, you can link to the MDN content contributors' channel, [dev-mdc](https://www.mozilla.org/about/forums/#dev-mdc).
* The `"keywords"` array should be an array of terms which describe the project's purpose or usage. A good guideline is to use the same values we use when tagging MDN articles (except in all lower-case); see [How to properly tag pages](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Howto/Tag) on MDN.

## Making changes to MDN repositories

If you wish to make changes to our code demos or other resources, you don't need special privileges (as described in the section below). The correct process for making changes is to:

* Fork the repo you wish to change.
* Create a new branch to contain your change. Give your branch a descriptive name, such as `chrome-bug-fix`, or `add-object-fit-example`.
* Clone your fork locally.
* Make your change.
* Push the branch to your remote fork.
* Make a pull request to the original repo.

If you are not sure how to complete the above steps, GitHub's [Fork a Repo](https://help.github.com/articles/fork-a-repo/#fork-an-example-repository) guide is a good place to start.

## Requesting privileges for MDN repositories

If you wish to become a collaborator on one of our MDN repos (for example, if you wish to help review pull requests), you should make this request by [filing an issue in this repository (mdn)](https://github.com/mdn/mdn/issues),
or the repo you want to collaborate with. Either is OK.

To become a collaborator, you are required to:

* Agree to abide by our [Code of conduct](CODE_OF_CONDUCT.md).
* Set up [Two factor authentication](https://github.com/blog/1614-two-factor-authentication) on your GitHub account.

Once you have filed your issue, someone from our team will review it, and give you the necessary privileges provided our requirements are satisfied.
