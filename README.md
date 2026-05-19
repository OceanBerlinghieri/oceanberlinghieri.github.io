# Blog Project with GitHub Pages, Jekyll, and Netlify CMS

This project implements a static blog hosted on GitHub Pages, using Jekyll as the site generator, integrated with Netlify CMS to edit and publish content from a graphical interface, and with security configurations for access control.

## Technical Stack

- **HTML and CSS**: For the website template and visual styling.  
- **Markdown**: Main format for writing blog posts.  
- **Jekyll**: Static site generator compatible with GitHub Pages.  
- **GitHub Pages**: Free hosting for the website.  
- **Netlify CMS (Decap CMS)**: Administration panel for publishing content without editing HTML code.  
- **OAuth / GitHub OAuth**: Authentication method for secure login.

## Integration of Linters with npm

To maintain code quality and consistency in HTML, CSS, and Markdown, linters installed via npm have been added:

npm is initialized in the project

```shell
npm init -y
```

- Installation of linters:

```shell
npm install --save-dev htmlhint stylelint markdownlint-cli
```

- Scripts added in `package.json` to make execution easier:

```json
"scripts": {
"lint:html": "htmlhint '/*.html'",
"lint:css": "stylelint '/.css'",
"lint:md": "markdownlint '**/.md'",
"lint": "npm run lint:html && npm run lint:css && npm run lint:md"
}
```

- To run the linters:

```shell
npm run lint
```

## Automatic formatting with Prettier

To modify the code and keep it formatted automatically and consistently, Prettier is used:

- Installation of Prettier:

```shell
npm install --save-dev prettier
```

- `.prettierrc` configuration file (example):

```shell
{
"semi": false,
"singleQuote": true,
"tabWidth": 2,
"trailingComma": "es5"
}
```

- Scripts in `package.json` for automatic formatting:

```json
"scripts": {
"format": "prettier --write '**/*.{js,css,html,md}'"
}
```

- To format all the code, run:

```shell
npm run format
```

- Prettier directly modifies the files, adjusting the style according to the configuration.
- It can be integrated with editors (such as VSCode) for automatic formatting on save.

## Useful resources

- [Official GitHub Pages Guide](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
- [Jekyll and Netlify CMS Tutorial](https://dev.to/mrkaushal/jekyll-with-netlify-cms-tutorial-54ii)
- [Netlify CMS Configuration and Security](https://github.com/decaporg/jekyll-decap-cms)
- [Example of integration with GitHub OAuth](https://github.com/vencax/netlify-cms-github-oauth-provider)