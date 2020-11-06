# Suddenly Remote Handbook Template

## Using this project

This was created to provide an easy way for anybody to use GitLab to create a handbook to meet the new remote working style. 

GitLab's handbook is part of a larger website and blog project so any attempt to use it as a starting point would be problematic. 

This project exists to compensate for that with as little command-line activity as possible.  Forks were disabled because they create a relationship between projects.  To use this one, please export and import it into your own account. 

## After importing this project

There are some configurations that need to happen for this to be used for your own purposes. 

1.  Use the Web IDE to modify the `config.toml` with a fitting title
1.  Remove any template content that doesn't belong in your handbook 
1.  Update the README to contain instructions for contributing pages
1.  Use GitLab Pages with the gitlab.io URL until your company DNS 

If you want to checkout the repo to make local copies and run the local review app, be sure to do `git clone -r git@gitlab.com:brownfield-dev/remote/handbook.git` since the theme is currently in a submodule which needs to be pulled.

## Select a workflow

GitLab offers a lot of workflow flexibility depending on the size of your team and type of content in the handbook.  

If your handbook is meant to have company confidential information in it, be sure to set the project to private and the "GitLab Pages" accessibility to "Only Project Members" to prevent disclosure. 

Since project configurations and master branch changes are controlled by `Maintainer` roles, be sure to restrict that permission level to individuals authorized to speak for the organization.  If these are non-technical personnel, they can use the Merge Request feature to review content without the requirement to do any git commands or fancy technical activity. 

The suggested workflow comes from GitLab Flow and follows these steps: 

1.  Individual identifies content that needs to be added or changed
1.  Individual creates an issue in the project with the change they intend to make (use "content update" template) 
1.  Individual clicks the `Create Merge Request` button from the issue 
1.  Individual opens the Merge Request, clicks on `Web IDE` or checkout code if familiar with git
1.  Individual creates new pages or updates existing pages
1.  Individual `Resolves WIP Status` in Merge Request and assigns to a maintainer 
1.  Maintainer reviews change in Merge Request screen using the `Changes` tab
1.  Maintainer provides feedback on the specific code (comment on a line or section) 
1.  Individual updates the page as directed or discusses further
1.  Maintainer merges the change 

The important part of this flow is that the changes need to be small.  Creating many merge request that only incrementally improve the handbook is acceptable.  If the net benefit is at all positive, it should be merged and then follow-up issues or MRs created to address any additional content updates. 

The other thing you may notice is that there's no meeting or discussion or concensus building that takes place in the workflow.  The individual should be empowered to fix any pages they believe require improvement.  Silver license tier has approvals depending on the change. 

Don't be afraid to flag content as deprecated or invalid or until an update can be created.  Deleting content entirely is also good if it's incorrect, but leaving the pages in will serve as a reminder to execute the update. 
 
### Customize issue templates

In this repositiry is an example issue template for "Change content" which is based on the GitLab issue for requesting a change.  This makes a lot of assumptions and parts are likely not applicable.  It may make sense to duplicate it for various sections.  

These templates are in `.gitlab/issue_templates/` and the filename is used in the dropdown list for creating a new issue. 

Adding [quick actions](https://docs.gitlab.com/ee/user/project/quick_actions.html#quick-actions-for-issues-merge-requests-and-epics) to the bottom of the issue can do things like label them or notify a group. 

### 
