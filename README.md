hugo -theme-config


# 1. Initialize Git
git init

# 2. Add theme as a submodule
git submodule add https://github.com/janraasch/hugo-developer-portfolio themes/hugo-developer-portfolio

# 3. Tell Hugo to use the theme
echo 'theme = "hugo-developer-portfolio"' >> hugo.toml

# 4. Create placeholder content (so it builds)
mkdir -p content/home
echo '+++
title = "Home"
+++

Welcome to my site!' > content/home/index.md

# 5. Run the build
hugo