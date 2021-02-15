# README

create rails app and cd into it

```
rails new <app_name>
cd <app_name>

```
Install Tailwind compatibility build

```
yarn add tailwindcss@yarn:@tailwindcss/postcss7-compat
```
Add Tailwind plugins
```
yarn add @tailwindcss/forms @tailwindcss/typography @tailwindcss/aspect-ratio

```
Make a new folder 'app/javascript/stylesheets' and a scss file
```
mkdir app/javascript/stylesheets
touch app/javascript/stylesheets/application.scss
```
In 'app/javascript/stylesheets/application.scss' inject some Tailwind styles:

```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```
```
npx tailwindcss init

```
In the 'app/javascript/packs/application.js' after 'import "channels"'

```
import "stylesheets/application.scss"
```

In the 'postcss.config.js' before:

```
require('postcss-import'),
```

```
require('tailwindcss'),
require('autoprefixer'),
```
Amend the 'purge' and 'plugins' in 'tailwind.config.js'

```
module.exports = {
    purge: [
    './app/**/*.html.erb',
    './app/helpers/**/*.rb',
    './src/**/*.html',
    './src/**/*.js',
    './src/**/*.jsx',
  ],

  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
    plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/aspect-ratio'),
  ],

}
```
In 'app/views/layouts/application.html.erb' in header before '<%= javascript_pack_tag 'application', 'data-turbolinks-track': 'reload' %>'
```
<%= stylesheet_pack_tag 'application', media: 'all', 'data-turbolinks-track': 'reload' %>

```


