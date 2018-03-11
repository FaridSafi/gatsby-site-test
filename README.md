# gatsby-starter-default
The default Gatsby starter.

For an overview of the project structure please refer to the [Gatsby documentation - Building with Components](https://www.gatsbyjs.org/docs/building-with-components/).

## Install

Make sure that you have the Gatsby CLI program installed:
```sh
npm install --global gatsby-cli
```

And run from your CLI:
```sh
gatsby new gatsby-site-test
```

Then you can run it by:
```sh
cd gatsby-site-test
npm run develop
```

To build it: 
```sh
cd gatsby-site-test
npm run build
```

# Gihub

## Create your repo

```sh
git init
```

```sh
git add -A
```

```sh
git commit -m "first commit"
```

```sh
git remote add origin https://github.com/MisterAlex95/gatsby-site-test.git
```

```sh
git push -u origin master
```

## Create a ``develop``branch

Create a second branch named ``develop``

```sh
git checkout -b develop 
```
```sh
git add -A
```

```sh
git commit -m "first commit into develop"
```

```sh
git push --set-upstream origin develop
```

## Configure your github

 - go to Settings
 - go to Branches
 - Select :
    - Protect this branch
        - Require pull request reviews before merging

## DO NOT FORGET
 - certif ssl ;
 - Add a robot.txt to block robot to index the site:
    - just create a robot.txt file at the root of your site . http://robots-txt.com ;



# Amazon Web Services



## Deploy

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/gatsbyjs/gatsby-starter-default)
