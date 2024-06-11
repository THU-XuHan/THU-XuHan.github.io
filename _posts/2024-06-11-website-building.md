---
layout: article
title: How to build a personal website?
key: 10001
tags: note
category: note
lang: en
mermaid: true
---

I built my website through jekyll. You can check out the following contents to learn how to build a personal website from scratch.

<!--more-->

# The Theme I'm Using
https://github.com/kitian616/jekyll-TeXt-theme

The theme also comes with a tutorial:
https://kitian616.github.io/jekyll-TeXt-theme/docs/en/quick-start

# Building a Personal Website with Jekyll

Using Jekyll to build a personal website is a great choice, especially because of its seamless integration with GitHub Pages. Here is a detailed step-by-step guide to help you set up a Jekyll site from installation to deployment.

### Step 1: Install Jekyll and Bundler

First, make sure you have Ruby installed on your system. You can check with the following command:

```bash
ruby -v
```

If Ruby is not installed, you can install it with the following command (for macOS). However, you need to install Homebrew first. See [Install Homebrew](#homebrew-installation-and-ruby-update):

```bash
brew install ruby
```

Next, install Jekyll and Bundler:

```bash
gem install jekyll bundler
```

Generally, the above steps should help you successfully install Jekyll. However, you might encounter a situation where the Jekyll command is unavailable. This is often because the gem’s bin folder hasn’t been added to the PATH environment variable. The underlying reason is that tools downloaded by gem are placed in a specific folder, and if this folder is not included in the PATH, the computer cannot find the executable files of the downloaded tools. 

To resolve this, follow these steps:
First, run:
```bash
gem env
```

After running this command, look for the "- INSTALLATION DIRECTORY" output, similar to the following:

```bash
- INSTALLATION DIRECTORY: /opt/homebrew/lib/ruby/gems/3.3.0
```

Based on the address displayed above (this is where gem places the downloaded tools), add the following environment variable (note that the path “/opt/homebrew/lib/ruby/gems/3.3.0/” matches the output above):

```bash
export PATH="/opt/homebrew/lib/ruby/gems/3.3.0/bin:$PATH"
```

It's important to note that adding an environment variable is not done by running the above command directly. To learn how to add environment variables, refer to [Adding Environment Variables](#adding-path-environment-variable).

### Step 2: Create a New Jekyll Site

Use the Jekyll command line tool to create a new site:

```bash
jekyll new mywebsite
```

Navigate into the newly created site directory:

```bash
cd mywebsite
```

### Step 3: Run the Local Server

Install dependencies and start the Jekyll local development server:

```bash
bundle install
bundle exec jekyll serve
```

Open your browser and visit `http://localhost:4000` to see your site.

### Step 4: Write Content

Jekyll uses Markdown to write content. You can add new Markdown files in the `_posts` directory to create new blog posts. For example:

```bash
jekyll new post "My First Post"
```

This will create a new Markdown file in the `_posts` directory, with a filename formatted as `YYYY-MM-DD-my-first-post.md`.

### Step 5: Customize the Theme

You can choose to use Jekyll's built-in themes or select a theme from the Jekyll theme marketplace: [Jekyll Themes](https://jekyllthemes.io/). To install a new theme, follow these steps:

1. In the root directory of your site, open the `Gemfile` and add the new theme:

   ```ruby
   gem "minima", "~> 2.0"
   ```

2. Run `bundle install` to install the theme.

3. In the site's configuration file `_config.yml`, set the theme:

   ```yaml
   theme: minima
   ```

### Step 6: Deploy to GitHub Pages

1. **Create a GitHub Repository**:
   - Create a new repository named `<username>.github.io`, where `<username>` is your GitHub username.

2. **Push Code to GitHub**:
   - Initialize git and push your code to GitHub:

     ```bash
     git init
     git remote add origin https://github.com/<username>/<username>.github.io.git
     git add .
     git commit -m "Initial commit"
     git push -u origin master
     ```

3. **Configure GitHub Pages**:
   - In the GitHub repository’s `Settings` page, find the `GitHub Pages` section and select the `main` branch as the publishing source.

### Detailed Guides and Resources

For more detailed guides, you can refer to these resources:

- **Jekyll Documentation**: [Jekyll Documentation](https://jekyllrb.com/docs/)
- **GitHub Pages Documentation**: [GitHub Pages Documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)

### Summary

By following these steps, you should be able to successfully build and deploy a Jekyll website. If you encounter any issues or need further assistance, please let me know.

Installing Ruby manually via Homebrew will not directly affect the system’s built-in Ruby unless you explicitly change the default Ruby path configuration. Homebrew-installed Ruby will be located in Homebrew’s installation path, while the system’s built-in Ruby is usually located in the `/usr/bin/` directory.

# Homebrew Installation and Ruby Update

### Installation Steps

1. **Install Homebrew**

   If you haven't installed Homebrew yet, you can do so with the following command:

   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

2. **Install Ruby Using Homebrew**

   Run the following command to install Ruby:

   ```bash
   brew install ruby
   ```

3. **Update Environment Variables**

   After installation, update your shell configuration file to ensure the newly installed Ruby is used. Edit the `~/.zshrc` (for Zsh) or `~/.bash_profile` (for Bash) file and add the following line:

   ```bash
   export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
   ```

   Save the file and reload the configuration:

   ```bash
   source ~/.zshrc  # or source ~/.bash_profile
   ```

4. **Verify the Installation**

   Run the following command to ensure the newly installed Ruby is recognized:

   ```bash
   ruby -v
   ```

   You should see the output showing the Ruby version installed by Homebrew, not the system’s built-in version.

### Notes

- **Environment Variable Priority**: The Ruby installed by Homebrew will take priority over the system’s built-in Ruby because you configured Homebrew’s path to be prioritized in the environment variables.
- **System Stability**: Generally, installing Ruby via Homebrew won’t affect system stability as they exist independently. The system’s built-in Ruby can still be used.

### Switching Back to the System's Built-in Ruby

If you want to switch back to the system’s built-in Ruby, simply remove Homebrew’s Ruby path from the environment variables. Edit the `~/.zshrc` or `~/.bash_profile` file, delete the previously added line, and reload the configuration file:

```bash
source ~/.zshrc  # or source ~/.bash_profile
```

Run `ruby -v` to confirm that the system’s built-in Ruby is being used.

Following these steps, you can smoothly install and use Ruby managed by Homebrew while keeping the system’s built-in Ruby intact. If you encounter any problems or need further assistance, please let me know.

# Adding 'PATH' Environment Variable

### 1. Check the Current `PATH` Variable

First, check your current `PATH` environment variable:

```bash
echo $PATH
```

### 2. Open the Shell Configuration File

Depending on the shell you use, open the corresponding configuration file:

- For Zsh (typically the default shell on macOS):

  ```bash
  nano ~/.zshrc
  ```

Note: The above command opens a text editor in the terminal displaying the `~/.zshrc` file.

### 3. Find and Edit the `PATH` Variable

After opening the file, we need to modify it to add the environment variable. For example, if we want to add “/opt/homebrew/lib/ruby/gems/3.3.0/bin”, we add the following line:

```bash
export PATH="/opt/homebrew/lib/ruby/gems/3.3.0/bin:$PATH"
```

### 4. Save and Exit

In the nano editor, press `Ctrl + X` to exit, `Y` to save the changes, and then `Enter` to confirm the file name.

### 5. Reload the Shell Configuration File

After saving the changes, reload your shell configuration file to apply the changes:

- For Zsh:

  ```bash
  source ~/.zshrc
  ```

### 6. Verify the `PATH` Variable

After reloading the configuration file, check if the `PATH` environment variable has been successfully updated:

```bash
echo $PATH
```

<!--more-->
