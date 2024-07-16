# PR Checklist

## Checklist for Submitting a SQL Model PR <a href="#docs-internal-guid-73128d2e-7fff-b92b-1cf2-fe868168c9e9" id="docs-internal-guid-73128d2e-7fff-b92b-1cf2-fe868168c9e9"></a>

When done with your work and you contribution is ready for review, open a PR for the Flipside team to review. A set of reminders is provided below.&#x20;

{% hint style="info" %}
A `yml` file must accompany every `sql` model with tests and documentation for the additions. If updating an existing model, be sure to update tests and documentation, where applicable. Notes on model properties are available on the [Model Standards](model-standards/) page.
{% endhint %}

* [ ] Commit all changes of your working model to GitHub
* [ ] Run `git merge main` to pull any changes that have been merged
* [ ] Check for conflicts this may have caused, including up and down-stream dependencies.
* [ ] Merge any and all final changes, ready for approval
* [ ] Open a PR in GitHub with the following
  * [ ] Description of what is changing or being added.
  * [ ] The dbt command to run, default is likely `dbt run -s <model name>+`
  * [ ] Output of the dbt run showing success.
  * [ ] Output of a dbt test showing success.
* [ ] Post in the Discord channel that your PR is ready for review and tag your Flipside contact to review.
