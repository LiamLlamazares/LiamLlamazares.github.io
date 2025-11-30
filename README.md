# Liam Llamazares

This is the source code for my personal website and blog, based on the [al-folio](https://github.com/alshedivat/al-folio) theme.

## Local Installation & Compilation

To compile and run the blog locally, follow these steps:

1.  **Install Prerequisites:**

    - **Ruby:** Install Ruby (version 2.7 or higher). On Windows, use [RubyInstaller](https://rubyinstaller.org/). Ensure you check the option to add Ruby to your PATH.
    - **Bundler:** Open your terminal and run: `gem install bundler`
    - **Node.js:** Install Node.js from [nodejs.org](https://nodejs.org/).

2.  **Install Dependencies:**
    Navigate to the project directory in your terminal and run:

    ```bash
    bundle install
    npm install
    ```

3.  **Run Locally:**
    Start the local server with:
    ```bash
    bundle exec jekyll serve --config _config.yml,_config_local.yml
    ```
    Access your blog at `http://localhost:4000`.

Running locally allows you to see changes instantly as you save files, without waiting for the GitHub Actions build pipeline to complete. This is significantly faster for drafting posts and tweaking designs.

## License

The theme is available as open source under the terms of the [MIT License](https://github.com/alshedivat/al-folio/blob/main/LICENSE).

## Project Structure

Here is an overview of the key folders and files in your blog:

- **`_config.yml`**: The main configuration file. Contains settings for your site title, email, description, and plugins.
- **`_config_local.yml`**: A local override file for Windows. It disables heavy plugins (like ImageMagick) to ensure fast local development.
- **`Gemfile`**: Lists the Ruby gems (libraries) required to build the site.
- **`_news/`**: Contains markdown files for news announcements. Add new files here to create news items.
- **`_pages/`**: Contains markdown files for standalone pages like `about.md`, `cv.md`, etc.
- **`_bibliography/`**: Stores your `.bib` files for publications.
- **`_data/`**: Contains YAML files for site data, such as social media links and repository settings.
- **`_layouts/`**: HTML templates that define the look of different page types (post, page, cv, etc.).
- **`_includes/`**: Reusable HTML snippets (headers, footers, navigation) included in layouts.
- **`assets/`**: Stores static files like images (`assets/img/`), CSS, JavaScript, and PDFs (`assets/pdf/`).

## Restoration

To keep this project clean, several demo files and development tools from the original `al-folio` theme have been removed.

**Removed Content:**

- **Demo Pages:** Example pages like `about_einstein.md`, `teaching.md`, etc.
- **Demo Assets:** `lighthouse_results`, `readme_preview`.
- **Dev Tools:** Docker configuration (`Dockerfile`, `docker-compose.yml`), `.devcontainer`.
- **Theme Docs:** `CONTRIBUTING.md`, `FAQ.md`, `INSTALL.md`, `CUSTOMIZE.md`.

**How to Restore:**
If you need any of these files back (e.g., to reference the original documentation or use Docker), you can find them in the [original al-folio repository](https://github.com/alshedivat/al-folio). Simply download the specific file you need and place it back in your project directory.
