# Netlify Build Plugin: Persist the Gridsome Cache Between Builds

Persist the Gridsome cache between Netlify builds for huge build speed improvements! ⚡️

What are Netlify build plugins? Check out [the announcement page on Netlify](https://www.netlify.com/products/build/plugins/).

### [One-click install to add this to your Gridsome site](https://app.netlify.com/plugins/netlify-plugin-gridsome-cache/install)

## Usage

If you don’t want to use the [UI-based installation](http://app.netlify.com/plugins/netlify-plugin-gatsby-cache/install), you can install manually using `netlify.toml`.

Add the following lines to your `netlify.toml` file:

```toml
[build]
  publish = "dist"

[[plugins]]
  package = "netlify-plugin-gridsome-cache"
```

Note: The `[[plugins]]` line is required for each plugin, even if you have other plugins in your `netlify.toml` file already.

This plugin determines the location of your `.cache` folder by looking at the `publish` folder configured for Netlify deployment (this _must_ be set in your `netlify.toml` in the `[build]` section). This means that if your Gatsby site successfully deploys, it will be cached as well with no config required! 🎉

## How much of a difference does this plugin make in build times?

Each Gatsby site is different, so build times vary widely between them, but one common slowdown in Gatsby builds is processing and transforming images. Gatsby is smart enough to check if these transformations have already been done and skip them, but in order to get that benefit in a build pipeline (e.g. Netlify) the `dist` and `.cache` directories need to be preserved between builds. That’s what this plugin does!

|                                                       | No Cache | Cache | Savings |
| ----------------------------------------------------- | -------- | ----- | ------- |
| _ 231 GraphQL queries<br>_ 295 images<br>\* 295 pages | 27.5s    | 22.4s | 22%     |

tl;dr: Repeat builds with lots of images will be _much_ faster. With few or no images, the difference will be there, but it won’t be as pronounced.

\*note: the above differences are cited from [my blog's repo](https://github.com/edm00se/blog); if you would like to submit a PR to add additional application size/savings data, I will be happy to accept it

## Want to learn how to create your own Netlify Build Plugins?

Check out [Sarah Drasner’s excellent tutorial](https://www.netlify.com/blog/2019/10/16/creating-and-using-your-first-netlify-build-plugin/?utm_source=github&utm_medium=netlify-plugin-gatsby-cache-jl&utm_campaign=devex)!

## Credits

Thank you to @jlengstorf whose work this repo is forked from; [jlengstorf/netlify-plugin-gatsby-cache](https://github.com/jlengstorf/netlify-plugin-gatsby-cache).

## License

MIT
