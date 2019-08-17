# Pull Request: Adding Code to a Repository

This assignment helps you learn how to add new code to an existing codebase while following best practices. Pull requests are based on the idea of 'requesting' that someone 'pulls in' the changes which you have created. The high level workflow involves creating a new branch, making some changes, pushing that branch to the repository, creating a new pull request using the ui (under "Pull requests"), the PR (pull request) is reviewed, often times new commits are added if the reviewer requests changes, and then it's finally merged into *master*.


## Assignment Instructions
1. Create a branch of the "writing-excellent-poetry" repository
2. Make some changes to it
3. Use `git add [filename]`, `git commit -m "[message...]"` and `git push origin HEAD` to push the branch to the repository
4. Go to 'Pull requests' in the GitHub UI
5. Create a new request (there will probably be a prompt) - if not, click 'new' and set the "base" to "master"
6. Click "create"
7. Voila, you have a pull request. 

At this point you can decide to add more changes, and once ready, the branch can be merged into master. Once this is done it's not easily reverted so be sure about what code you're adding to your master branch. Remember, the *master* branch is the "true" code reference which ends up in production.


