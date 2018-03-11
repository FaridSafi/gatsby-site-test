<img src='https://travis-ci.org/MisterAlex95/gatsby-site-test.svg?branch=master' />
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
gatsby develop
```

To build it: 
```sh
cd gatsby-site-test
gatsby build
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
git push --set-upstream origin develop
```

## Configure your github

 - go to Settings
 - go to Branches
 - Select :
    - Protect this branch
        - Require pull request reviews before merging

## DO NOT FORGET
 - certificat ssl ;   <------- 
 - Add a robots.txt to block robots to index the site:
    - just create a robots.txt file at the root of your site http://robots-txt.com ;
 - Do not forget to add a ``.gitignore`` file to not push the build project;

# Travis

## In travis-ci.org
 - create an account and authorize travis ;
 - select the repository you want ;
 - In Settings, select :
    - Build pushed branches ;
    - All auto cancellation ;

## In your project
 - install travis using brew: ``brew install travis`` ;
 - `travis login --pro`
 - `touch .travis.yml`
 - run ``travis setup s3`` and follow it ;
    - local project directory to upload : `public`
    - S3 ACL Settings : `bucket_owner_full_control`
 - A new file appear at the root of your project: ``.travis.yml``
 - You will need to add some options into this file: 
    - specified the language you wanted to use:
        ```yml
        language: node_js
        node_js: '8'
        ```
    - specified the tools you wanted to use and cache:
        ```yml
        cache: 
            yarn
            gatsby-cli
        ```
    - specified the install process of your project
        ```yml
        install: 
            yarn install
        ```
    - specified the script you want to run after the installation of all dependancies:
        ```yml
        script: 
            gatsby build && cp ./robots.txt public/
        ```
    - specified the branch you wanted to build and deploy:
        ```yml
        branches:
            only:
            - master
        ```  
    - Add some options into the deploy configuration:
        ```yml
        deploy:
            provider: s3
            access_key_id: <ALREADY GENERATED>
            secret_access_key:
                secure: <ALREADY GENERATED>
            bucket: gatsby-site-test
            local_dir: public
            skip_cleanup: true
            region: eu-west-3
            acl: 'bucket_owner_full_control'
            on:
                repo: MisterAlex95/gatsby-site-test
        ```

you can see the full file [here](./.travis.yml)

# Amazon Web Services

## S3 
S3 is use to host your files.
Just create a bucket which have the name of your project.

# Authorizations
## Create your own strategy
We need to authorize everyone to see every file in the bucket so:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::gatsby-site-test/*"
        }
    ]
}
```
## Amazon S3 Static Website Settings
  - Utiliser ce compartiment pour héberger un site Web

And that's all ! Enjoyed !
