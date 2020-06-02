
### Gitflow Workflow

[![r-NOOfd-H-Imgur.png](https://i.postimg.cc/yNC612Ny/r-NOOfd-H-Imgur.png)](https://postimg.cc/gx4b4S8x)



The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects.

Git-flow CLI is a wrapper around Git 



Core concept of gitflow workflow come from **Vincent Driessen**. 
 1) this concept is working by split branch for each purpose. 
 2) Master branch — This branch contain production of code base
 3) Develop branch — This branch is develop branch.
 4) Feature branch — This branch split from develop branch. in case we need new feature we must split it from develop branch. when this feature done. we need to combine back to develop
 5) Release branch — This branch for release. checking everything before release. include write document about this release.
 6) Hotfix branch — This branch for fix urgent bug on production.


 ```properties
     ## start master and init

     git checkout -b develop

     git checkout -b "feature/first-feature"

     git checkout develop
     git merge "feature/first-feature"
     git branch -D "feature/first-feature" // delete feature branch


     git checkout -b "release/0.0.1"


     git checkout develop
     git merge "release/0.0.1"
     git checkout master
     git merge "release/0.0.1"
     git branch -D "release/0.0.1" // delete release branch

 ```

#### Nutshell : 

1) A develop branch is created from master
2) A release branch is created from develop
3) Feature branches are created from develop
4) When a feature is complete it is merged into the develop branch
5) When the release branch is done it is merged into develop and master
6) If an issue in master is detected a hotfix branch is created from master
7) Once the hotfix is complete it is merged to both develop and master
