# Google Summer of Code Guides

[![Codacy Badge](https://api.codacy.com/project/badge/Grade/a96cb74f29bb462e92ba805dab9c676f)](https://app.codacy.com/manual/diouldebalde/gsocguides?utm_source=github.com&utm_medium=referral&utm_content=dbalde/gsocguides&utm_campaign=Badge_Grade_Settings)

This project contains the Google Summer of Code Mentor Guide and Student Guide.

## Template

The template and build is based on
https://github.com/tomjoht/documentation-theme-jekyll

Documentation can be found at
http://idratherbewriting.com/documentation-theme-jekyll/

## Local Development

``` shell
# Build docker image (once)
make build-image

# Run server (listens on port 4000)
make serve
```

## Adding New Pages

If you're adding new pages between existing pages, use this script (or similar)
to renumber the existing pages.

```bash
for i in $(seq 28 -1 15);
    do n=$((i+1));
    fi=$(echo $i-*.md);
    fn=$(echo $fi | sed -e "s/${i}-/${n}-/");
    git mv $fi $fn;
    perl -pi -e "s/^order: $i\$/order: $n/" $fn;
done

# 28 is the current last page.
# 15 is the page to insert before.
# Iterate backwards to ensure there's only one page with each index at a time.
```

We need to do this because a) we're naming pages after their order, and b) the
Next/Prev button requires all the order numbers to be contiguous.  You can't
skip any.

# Upgrade Ruby Gems

```bash
bundle install --path vendor/bundle
bundle update github-pages
rm -rf vendor/bundle
```

Don't forget to rebuild the docker image!

## Want to contribute?

Please see the [CONTRIBUTING](CONTRIBUTING.md) instructions.
