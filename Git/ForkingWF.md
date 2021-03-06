# Forking strategy for open source contribution


[![download.png](https://i.postimg.cc/CLZfzTw3/download.png)](https://postimg.cc/nCJLPWj2)

1) First, verify that you have already setup a remote for the upstream repository, and hopefully an origin too:
    1) git remote -v
        ```properties 
           origin git@github.org:my-user/some-project.git (fetch) 
           origin git@github.org:my-user/some-project.git (push) 
         ```

    2) If you don't have an upstream you can easily add it with command

  
    ```properties
      git remote add upstream git@github.org:some-maintainer/some-project.git
    ```

Verify that remote is added correctly 

2)

```properties
   git remote -v
   origin git@bitbucket.org:my-user/some-project.git (fetch)
   origin git@bitbucket.org:my-user/some-project.git (push)
   upstream git@bitbucket.org:some-gatekeeper-maintainer/some-project.git (fetch)
   upstream git@bitbucket.org:some-gatekeeper-maintainer/some-project.git(push)
```

Now you can collect the latest changes of the upstream repository with fetch.
 Repeat this every time you want to get updates:

3)
    ```properties
        git fetch upstream
      ```


At this point, it does not matter if you use merge or rebase, as the result will typically be the same. Let's use merge:

```properties
  git checkout master
  git merge upstream/master
```


When you want to share some work with the upstream maintainers you branch off master, create a feature branch. When you're satisfied, push it to your remote repository.

You can also use rebase instead, then merge to make sure the upstream has a clean set of commits (ideally one) to evaluate:


###### some work and some commits happen
###### some time passes
```properties
git checkout -b feature-x

git fetch upstream
git rebase upstream/master


###### push your work 

git push origin feature-x
```


A slight problem arises if you have to update your remote branch feature-x after you've published it, because of some feedback from the upstream maintainers. 

options to handle this 
  1) Rebase your local branch on top of the updates from upstream and do a force push onto your remote branch:
  2) merge the updates from upstream in your local branch which will record a merge commit. This will clutter the upstream repository.
  3) Create a new branch altogether with the updates from you and the upstream.

```properties
git push -f origin feature-x
```
   
