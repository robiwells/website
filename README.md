# Rob Wells' Website

A repository containing the source code for my website.

**To view the website, [click here](https://robwells.dev).**

---
[![last release](https://img.shields.io/github/release-date/robiwells/website?logo=github&label=Last%20Release)](https://github.com/robiwells/website/releases)
[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/robiwells/website/ci.yml?logo=github&label=CI)](https://github.com/robiwells/website/actions/workflows/ci.yml)

## 🤖 Deployment

- Code is tested using [GitHub Actions](https://github.com/robiwells/website/actions/workflows/ci.yml)
Deployment is automated by [GitHub Actions](https://github.com/robiwells/website/actions).
- Pushes to `main` trigger a new [`latest`](https://github.com/robiwells/website/releases/tag/latest) release and deploay to Netlify.

## 🔧 Development

- **Dependencies**
  - [Ruby](https://www.ruby-lang.org/en/)
  - [Jekyll](https://jekyllrb.com/) (`gem install jekyll bundler`)
  
- **Theme**
    [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/)

- **Serve**:
  ```bash
  bundle exec jekyll serve --livereload
  ```

## 🔏 License

This project is dual-licensed under both [Apache 2.0](LICENSE-APACHE) and [MIT](LICENSE-MIT) licenses.
