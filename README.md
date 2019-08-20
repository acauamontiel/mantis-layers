Mantis Layers
=============

> A utility to handle z-index layers with simplicity

[![npm version](https://badge.fury.io/js/mantis-layers.svg)](http://badge.fury.io/js/mantis-layers)

<p align="center">
  <img title="Mantis Layers" src="mantis-layers.png" width="200" />
</p>

---


Installing
----------

The installation can be done in 3 steps:

- **Step 1**

	Install via NPM:

	```sh
	$ npm i --save mantis-layers
	```

- **Step 2**

	You can use this plugin in different ways, but all consist of passing the plugin to the [`.use`](http://stylus-lang.com/docs/js.html#usefn) method of Stylus.
	For this example, I'll use it with [Gulp](http://gulpjs.com/) in a ES6 enviornment.

	```javascript
	import gulp from 'gulp';
	import stylus from 'gulp-stylus';
	import layers from 'mantis-layers';

	gulp.task('css', () =>
		gulp.src('path-to-source.styl')
			.pipe(stylus({
				use: [
					layers()
				]
			}))
			.pipe(gulp.dest('path-to-dest/'))
	);
	```

- **Step 3**

	Now just import the plugin into your `.styl` file as you already know.

	```styl
	@import 'mantis-layers'
	```


Examples
--------

```styl
$mantis.layers.context = {
	default: (element-a element-b element-c),
	element-a: (child-a child-b)
	element-b: (child-b child-a)
}

.element-a
	z-index element-a

	.child-a
		z-index element-a child-a

	.child-b
		z-index element-a child-b

.element-b
	z-index element-b

	.child-a
		z-index element-b child-a

	.child-b
		z-index element-b child-b

.element-c
	z-index element-c
```

**Will result:**

```css
.element-a {
	z-index: 100;
}

.element-a .child-a {
	z-index: 100;
}

.element-a .child-b {
	z-index: 200;
}

.element-b {
	z-index: 200;
}

.element-b .child-a {
	z-index: 200;
}

.element-b .child-b {
	z-index: 100;
}

.element-c {
	z-index: 300;
}
```


License
-------

© 2016 [Acauã Montiel](http://acauamontiel.com.br)

[MIT License](http://acaua.mit-license.org/)
