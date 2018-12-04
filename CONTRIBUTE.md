# Guide

To make changes of the guide change the following documents:
1. Any file in dir `pages`
2. `SUMMARY.md` represents menu on the lefthand side
3. `README.md` represents the first page of the guide

Everything else is generated with:

```
npm install
gitbook install
gulp
```
Publish the guide with:

```
git add -u
git add docs
git commit -m "update"
git push
```

To run locally and test:

`gitbook serve`



## Troubleshooting

If this doesn't work: `npm cache clean` do this:

> You'll notice the error here is always "Error: ENOENT: no such file or directory, stat"
> Reach into ~/.gitbook/versions/3.2.2/lib/output/website/copyPluginAssets.js and tell cpr (aliased as fs.copyDir) not to "confirm" ...which is what downstream invokes the stat.
> 
> It's this line, here: https://github.com/GitbookIO/gitbook/blob/3.2.2/lib/output/website/copyPluginAssets.js#L112
> 
> Rerun and see the book compile w/o error.
