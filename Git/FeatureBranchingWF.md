
### Feature branching workflow


1) The core idea behind the Feature Branch Workflow is that all feature development should take place in a dedicated branch instead of the master branch. 

2) This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase.

3) It also means the master branch will never contain broken code, which is a huge advantage for continuous integration environments.

4) promotes collaboration with team members through pull requests and merge reviews

5) focused on branching patterns

6) use git rebase (only if we have large changes that doesnt cause any conflicts with existing code base ) during the review and merge stages of a feature branch will create enforce a cohesive Git history of feature merges.


```properties
   git remote add origin <repo_github>

   git push origin master


   git checkout -b develop

   git checkout -b "feature/first-feature"


   git push origin feature/first-feature

   ## make a Pull Request

   git push origin feature/first-feature --delete // del remote branch
   git branch -D feature/first-feature // del local branch


```