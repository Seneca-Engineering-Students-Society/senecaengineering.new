# Seneca Engineering Students' Society (SESS) Website

This repository contains the official website of the Seneca Engineering Students' Society (SESS).

The website, [senecaengineering.org](https://senecaengineering.org), is built using [Hugo](https://gohugo.io/), an open-source static site generator, with the [Blowfish theme](https://themes.gohugo.io/themes/blowfish/) and deployed using [GitHub Pages](https://pages.github.com).

The philosophy behind this architecture is to ensure ease of maintenance and collaboration.

# Updating the Website

## 1. Install Hugo

Reference: [Hugo: Installation](https://gohugo.io/installation/)

### Windows Users

Open PowerShell and install Hugo Extended:

```shell
winget install Hugo.Hugo.Extended

```

### Linux Users

Open a terminal and install Hugo Extended:

```shell
sudo snap install hugo

```

### Mac Users

Open a terminal and install Hugo Extended:

```shell
brew install hugo
```

### Validate Hugo Installation

Open a new terminal/shell and run:

```shell
hugo version
```

## 2. (Fork or) Clone this Repository and Run the Website Locally

*(Optionally, you may also fork this repository to your own GitHub account.)*

Open a new terminal/shell and clone this repository:

```shell
git clone --recurse-submodules https://github.com/Seneca-Engineering-Students-Society/senecaengineering.org.git

cd senecaengineering.org
```

Ensure you are in the project root directory (`senecaengineering.org/`), then serve the website on localhost:

```shell
hugo serve
```

Open [http://localhost:1313/](http://localhost:1313/) in your web browser to see the website.

If you see "Page Not Found" or the page is not displaying correctly, you most likely missed the submodule during the initial clone. Update your local repo to include the submodule:

```shell
git submodule update --init --recursive
```

During cloning of submodules, nothing much will show in the terminal until the complete download and verification is done so just wait and be patient.

## 3. Modifying the Content

**LiveReload:** When the server is running, Hugo injects JavaScript into the generated HTML pages. The LiveReload script creates a connection from the browser to the server via web sockets. As you save files, the browser will refresh automatically. You do not need to install any software or browser plugins, nor is any configuration required.

```text
senecaengineering.org/
├── archetypes/   <-- contains templates for new content
│   └── default.md
├── assets/       <-- global resources such as images, custom CSS, JavaScript
├── config/       <-- all the config files for the website
│   └── _default/
│       └── hugo.toml
├── content/      <-- all the website content
├── public/       <-- created when you build the site locally
├── resources/    <-- created when you build the site locally
├── static/       <-- contains files such as favicon.ico, robots.txt, logo
└── themes/       <-- contains the theme used for the website
```

Unless you are changing site-wide settings or the theme, you only need to modify files within the `content` directory to update information on the website.

Before starting any modifications, create and switch to a new branch locally:

```shell
git checkout -b name-of-your-branch
```

This ensures you will not overwrite the `main` branch when you commit your changes later on.

Make your changes and preview the updates in your browser.

* To stop the Hugo server, press <kbd>Ctrl</kbd>+<kbd>C</kbd>.
* To restart it, run: `hugo serve`

## 4. Upload the Changes

Once you are satisfied with your changes, save, commit, and push them to GitHub.

```shell
git add .
git commit -m "Provide a detailed message of the changes that you made"
git push -u origin name-of-your-branch
```

If you made changes to multiple unrelated files, the best practice is to stage multiple commits by adding the files individually:

```shell
git add file1.md file2.md
git commit -m "Provide a detailed message of the changes related to file1 and file2"

git add file3.md
git commit -m "Provide a detailed message of the changes related to file3"

git push -u origin name-of-your-branch
```

After pushing your branch, create a **Pull Request (PR)** on GitHub to merge your changes into the `main` branch. Create one pull request for every logical group of changes; do not create one massive request.

Another member from SESS will review and approve the changes.

## 5. Rules and Best Practices for Website Content

* All content, except for site-wide scripts or graphics, should be created within the `content` directory.
* All content (Markdown files and images) for a specific page should be contained within its own directory as a **Page Bundle**.
* Hugo treats `index.md` as a single page (Leaf Bundle) and `_index.md` as the listing page for a directory containing multiple pages (Branch Bundle). Hugo will automatically search for `index.md` within the directory structure.
* To update the theme layout, create overrides in the `layouts/` directory. Do NOT modify files in the `theme/` directory directly.

For example, to create a new post for the blog:

1. Create a new directory under `blog` and add an `index.md` file:

    ```shell
    mkdir content/blog/my-post/
    touch content/blog/my-post/index.md 

    ```

    *(Alternatively, use the Hugo command to generate it with the proper front matter:)*

    ```shell
    hugo new content/blog/my-post/index.md 

    ```

2. Edit the `.md` file using a text editor:

    ```shell
    nano content/blog/my-post/index.md 

    ```

    **Example content:**

    ```text
    ---
    title: "Robotics Workshop"
    date: 2026-03-05
    ---

    We are hosting a robotics workshop this Friday at Seneca.
    ```

    Save and exit.

    All images for the post should go into the exact same directory:

    ```text
    content/blog/my-post/my-post-image.png 
    ```

> **Note:** The `static` directory is strictly reserved for site-wide static content such as `favicon.ico`, `robots.txt`, and the main site logo.

## Contact Us

This project is maintained by the Seneca Engineering Students' Society. For technical issues, please contact the repository maintainers.