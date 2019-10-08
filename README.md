# Draw.io HALM Instructions
## Branch Descriptions
* upstream/master - drawio's master branch
* origin/master - the branch we keep up to date with our changes and their changes
* origin/alm-x.x.x - our shipped code

## Initial setup
Clone from our github

    git clone https://github.com/FernCreek/drawio.git

Add the upstream branch for upgrades

    git remote add upstream https://github.com/jgraph/drawio.git

Ensure everything is up to date
    
    git pull origin alm-x.x.x

Move into our dir
    
    cd drawio
    
## Flow For Features
Ensure alm-x.x.x is up to date locally

    git fetch origin/alm-x.x.x

Create new branch based on our default branch

    git checkout -b alm-<new feature name> alm-x.x.x 

Make changes...
Remember more commits are better

    git commit -m <commit notes>

Push to github

    git push origin alm-<new feature name>

PR into alm-x.x.x (use github for this)

Create new release (use github for this)

Once accepted you _may_ delete branch

## For upgrades
Rebase the current version (x.x.y) onto our master branch.

Using rebase means there are new commits added to master, so when the merge from upstream happens, all of the changes we made are the most up-to-date, and we are less likely to loose changes.

    git fetch origin/alm-x.x.y
    git fetch origin/master
    git checkout master
    git rebase alm-x.x.y
    


Ensure you have the upstream version locally

    git fetch upstream/<target release tag>

Merge the upstream into the new branch

    git merge upstream/<target release tag>

Resolve conflicts...

Push to github

    git push origin master

Check out a new branch where x.x.x is the new version to finish the upgrade

    git checkout -b alm-x.x.x

Push to github

    git push origin alm-x.x.x

Make the new branch the default (use github for this)

## About

[draw.io](https://www.draw.io) is an online diagramming web site that delivers the source in this project.

draw.io uses the [mxGraph library](https://github.com/jgraph/mxgraph) as the base of the stack, with the [GraphEditor example](https://github.com/jgraph/mxgraph/tree/master/javascript/examples/grapheditor) from mxGraph as the base of the application part. The mxGraph library build used is stored under /etc/mxgraph/mxClient.js.

## License

draw.io is licensed under the Apache v2.

## Development

A development guide is being started on the GitHub project wiki. There is a [draw.io](http://stackoverflow.com/questions/tagged/draw.io) tag on Stack Overflow currently, please make sure any questions adhere to their guidelines for question.

The [mxGraph documentation](https://jgraph.github.io/mxgraph/) provides a lot of the docs for the bottom part of the stack. There is an [mxgraph tag on SO](http://stackoverflow.com/questions/tagged/mxgraph).

## Running

One way to run draw.io is to fork this project, [publish the master branch to GitHub pages](https://help.github.com/categories/github-pages-basics/) and the [pages sites](https://jgraph.github.io/drawio/src/main/webapp/index.html) will have the full editor functionality (sans the integrations).

Another way is to use [the recommended Docker project](https://github.com/fjudith/docker-draw.io) or to download [draw.io Desktop](https://get.draw.io).

The full packaged .war of the client and servlets is built when the project is tagged and available on the [releases page](https://github.com/jgraph/draw.io/releases).

## Supported Browsers

draw.io supports IE 11, Chrome 32+, Firefox 38+, Safari 9.1.x, 10.1.x and 11.0.x, Opera 20+, Native Android browser 5.1.x+, the default browser in the current and previous major iOS versions (e.g. 11.2.x and 10.3.x) and Edge 23+.
