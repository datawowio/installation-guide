## **Installation guide**

**XCode Command Line Developer Tools**
```
xcode-select --install
```
**Home brew**
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

**Oh my zsh**
```
curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```
**Database**
```
brew install postgresql
brew install mongodb
```
**Version control**
```
brew install git
```
**Cache**
```
brew install redis
```
**Python3**
```
brew install python3
```
**AWS**
```
brew install awsebcli
```
**Yarn**
```
brew install yarn
```
**Node**
```
brew install node
```
**Node version manager**
```
brew install nvm
```

**VScode** ([**Editor**](https://code.visualstudio.com/)) 
```
brew cask install visual-studio-code
```
> **Tip:** another editor such as [**_atom_**](https://atom.io/), [**_sublime_**](https://www.sublimetext.com/),  vim, neovim, etc.
>
> IDE: [**_rubymine_**](https://www.jetbrains.com/ruby/), [**_intellij_**](https://www.jetbrains.com/idea/)

## **Installation ruby on rails guide**

**RBENV - ruby manager control version**
```
brew update brew install rbenv ruby-build rbenv-gem-rehash
```
on ~/.bashrc or ~/.zshrc
```
eval  "$(rbenv init -)"
```
> **Tip:**  after it finished ``` source ~/.bashrc or ~/.zshrc ```

**ruby install by version**
```
rbenv install 2.6.1
```
>**Tip:** ``` rbenv -h``` will show on command to help you
>
>change version ```rbenv shell 2.5.3  ```

**Bundler**
```
gem install bundler2.0.1
```
**Ruby on Rails**
```
gem install rails
```
> **Tip:** after it finished ``` rails -v ```
>
> all command ```rails new -h```

**Basic create rails project**

```
rails new blog -d=postgresql && cd blog
rails db:create
rails s

-- welcome to rails --
```
