# Gatsby Incremental Builds + GitHub Actions

Example repository showing how Gatsby Incremental Builds can be accomplished using GitHub Actions deploys.

As a proof of concept, an example deployment using [Cloudflare Workers](https://workers.dev) is included in this repo. When new commits are made, the workflow will run, caching any existing content (using the `.cache` and `public` directories) and not requiring content that hasn't changed to be built again.

Note that this repo is pretty WIP from a documentation perspective, but I do want to shout out @raulfdm who beat me to implementing this with a _significantly_ easier implementation than what I was trying to pull off. Some of the workflow code in this project is based on his work.

## Limitations

- GitHub Actions' caching feature is currently only supported on `push` and `pull_request` event types - this means that any repositories using schedules or `repository_dispatch` (custom webhook events) will be unable to use incremental builds with GitHub Actions at this time. This issue in the actions/cache repo tracks that problem: https://github.com/actions/cache/issues/63.
