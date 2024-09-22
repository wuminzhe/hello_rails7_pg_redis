# Make sure RUBY_VERSION matches the Ruby version in .ruby-version
ARG RUBY_VERSION=3.3.5
FROM ghcr.io/rails/devcontainer/images/ruby:$RUBY_VERSION


# Dependencies
RUN apt-get update -qq && apt-get install -y cron postgresql-client zsh fzf

# Node
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && apt-get install -y nodejs
RUN npm install --global yarn

# Uncomment if you need rust
# RUN curl https://sh.rustup.rs -sSf | bash -s -- -y
# ENV PATH="/root/.cargo/bin:${PATH}"

# Zsh and Zim
RUN chsh -s $(which zsh)
RUN curl -fsSL https://raw.githubusercontent.com/zimfw/install/master/install.zsh | zsh

# Debug: Print Ruby version and PATH
RUN echo "PATH: $PATH"

# Try to install Rails with full path
RUN gem install rails -v 7.2.1