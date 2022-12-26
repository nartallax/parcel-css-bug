# How to reproduce

```bash
	git clone git@github.com:nartallax/parcel-css-bug
	cd parcel-css-bug
	npm install
	npm run build
```

This should yield the following error:

```bash
@parcel/bundler-default: The expression evaluated to a falsy value:

  (0, _assert().default)(bundle !== 'root' && bundle != null)
```

## Details

The bug occurs if all of the following conditions are met:

1. There is a non-module imported CSS file (in this example it's `global.css`, imported from `index.html`)
2. There is more than one module CSS files (in this example it's `a.css` and `b.css`, imported from `main.js`)

This also occurs with SCSS and Typescript, and maybe other css/js preprocessors which I didn't test for.  
