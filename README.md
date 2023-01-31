# test-github-actions

This repo contains simple github actions to perform various tasks.

## Contributing

If you want to contribute new snippet just do following:

1. Fork this repo.
2. Optionally generate personal access token with read access to repo. (needed for some workflows)
3. Create file in .github/workflows
4. Make sure your workflow can be run locally using `act`
5. Create Pull request to `master`
6. Wait for approvals
7. Merge! :)

## Local usage

You can use [act](https://github.com/nektos/act) to run all workflows locally. See installation guides in act repository.


Usually to test workflows with act you can do:

1. `act -l` to list workflows.
2. `act -j workflow_name` where `workflow_name` is name of workflow you want to start.

Some workflows need GITHUB_TOKEN to be set - or otherwise these will fail to checkout repository on docker based actions. Example below:

```bash
# This is readonly token with access to this repository only. It will calm down act workflows that need GITHUB_TOKEN variable.
export TOKEN="GITHUB_PAT_TOKEN_WITH_ACCESS_TO_REPO"
act -s GITHUB_TOKEN=${TOKEN} -j modify_json

# or for m1 macs
act --container-architecture linux/amd64 -s GITHUB_TOKEN=$TOKEN -j modify_json
```
