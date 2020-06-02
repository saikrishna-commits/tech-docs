

First, verify that you have already setup a remote for the upstream repository, and hopefully an origin too:

Step1 ) 
    git remote -v
    origin git@bitbucket.org:my-user/some-project.git (fetch)
    origin git@bitbucket.org:my-user/some-project.git (push)

 If you don't have an upstream you can easily add it with the remote command:
      git remote add upstream git@bitbucket.org:some-gatekeeper-maintainer/some-project.git



Verify that remote is added correctly 

step2 )
   git remote -v
    origin git@bitbucket.org:my-user/some-project.git (fetch)
    origin git@bitbucket.org:my-user/some-project.git (push)
    upstream git@bitbucket.org:some-gatekeeper-maintainer/some-project.git (fetch)
    upstream git@bitbucket.org:some-gatekeeper-maintainer/some-project.git (push)

Now you can collect the latest changes of the upstream repository with fetch.
 Repeat this every time you want to get updates:

step3 )
    git fetch upstream


At this point, it does not matter if you use merge or rebase, as the result will typically be the same. Let's use merge:


git checkout master
git merge upstream/master


When you want to share some work with the upstream maintainers you branch off master, create a feature branch. When you're satisfied, push it to your remote repository.

You can also use rebase instead, then merge to make sure the upstream has a clean set of commits (ideally one) to evaluate:


git checkout -b feature-x
#some work and some commits happen
#some time passes
git fetch upstream
git rebase upstream/master



push your work 

git push origin feature-x




A slight problem arises if you have to update your remote branch feature-x after you've published it, because of some feedback from the upstream maintainers. 

options to handle this 
  1) Rebase your local branch on top of the updates from upstream and do a force push onto your remote branch:
  2) merge the updates from upstream in your local branch which will record a merge commit. This will clutter the upstream repository.
  3) Create a new branch altogether with the updates from you and the upstream.


git push -f origin feature-x
   