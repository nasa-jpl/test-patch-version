# test-patch-version

Repo to test nasa-jpl/patch-version with varying permissions

This is a sentence
I added another sentence
I added another sentence

### One way to bypass master branch protection

How to setup the action to bypass branches protection
To bypass rulesets protection from a GitHub action:

Create a deploy key with write permissions
Save the private SSH key in a DEPLOY_KEY secret
Add Deploy keys to the Bypass list of the rulesets (Bypass list > Add bypass > Deploy keys)
Make your action checkouts the repo using the SSH key from the secret