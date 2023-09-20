# jetpack.me
## Commands

All commands need to be run from the root of the project. The project is setup with `pnpm`. You can as well set it up using `npm`.

```bash
# install dependencies
$ pnpm
# start local dev server
$ pnpm dev
# build production site
$ pnpm build
# preview build locally
$ pnpm preview
```

## Adding new tags

For adding new tags to posts you need to add the new tag in the array to the post located in `src/pages/blog`. For example `tags: ["general", "tech", "nature", "new-tag"]`.

After adding this new tag you need to add this tag into the `[tag].astro` file that the dynamic route is created and when building the site. Here you need to add the new tag as a param in the `getStaticPaths` method.

```javascript
export function getStaticPaths() {
  return [
    { params: { tag: "general" } },
    { params: { tag: "tech" } },
    { params: { tag: "food" } },
    { params: { tag: "nature" } },
    { params: { tag: "astro" } },
    // added this new-tag
    { params: { tag: "new-tag" } },
  ];
}
```

The tags will be read out of all posts dynamically using the `findTags` method in `src/utils/post.utils`.
