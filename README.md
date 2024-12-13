# test-patch-version

Repo to test nasa-jpl/patch-version with varying branch protections set

### To bypass rulesets protection for a GitHub action:

- Create a deploy key with write permissions locally
  - `ssh-keygen -t ed25519 -C "your_email@place.org"`
  - Put the public key on your repo settings
- Save the private SSH key in a DEPLOY_KEY Github Action secret in your repo
- Add `Deploy keys` to the Bypass list of the rulesets (Bypass list > Add bypass > Deploy keys) in your repo's branch protection settings
- Make your `action/checkouts` the repo using the SSH key from the secret

A side effect of doing this is now that magical "prevent recursive calls of the workflow when you push to main again" will now appear since we are no longer using `GITHUB_TOKEN` to authenticate and do our work.
The workaround for this is to include the string `[actions skip]` to the commit that the Action would write, which would prevent a workflow from being triggered. See [this for more information](https://docs.github.com/en/actions/managing-workflow-runs-and-deployments/managing-workflow-runs/skipping-workflow-runs)
