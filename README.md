# Heroku Buildpack Yarn Workspaces

This buildpack is for monorepos configured with yarn workspaces. This is an appropriation of the [heroku-monorepo-buildpack](https://github.com/lstoll/heroku-buildpack-monorepo).

## Rationale
It deals with the issue of not having a `yarn.lock`. The `yarn.lock` is important for ensuring that `yarn` actually pulls the correct dependency versions once the app is deployed.

## Usage

1. Set the `APP_BASE` configuration variable. It should point to the relative path of your intended workspace. e.g. `packages/my-package`.

2. Ensure you have a `yarn.lock` on your project's root directory. This buildpack will copy the `yarn.lock` to the `APP_BASE` directory. This is helpful for Heroku to detect and automatically install `yarn` in our behalf.

3. Add this buildpack to your app using the command: `heroku buildpacks:add -a <app> https://github.com/jg-rivera/heroku-buildpack-yarn-workspaces`
