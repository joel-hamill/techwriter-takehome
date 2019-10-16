### How do you revert a change from one branch and add it to another?
Scenario: You make an update and commit the the `master` branch. Afterward you realize that you should've made this
change to another branch named `staging`. What do you?

#### Answer
The answer below is based on two assumptions:
- The commit you want to move is the last commit made in the `master` branch.
- The commit was not pushed to the remote repo.

To move a git commit from the `master` branch to the `staging` branch:
1. Check out the `master` branch.
```
$ git checkout master
```
1. Get the commit hash, a 40-character SHA-1 hash that uniquely identifies the commit you want to move.
```
$ git log
```
1. Copy the commit hash, \<commit hash\>, from the `git log` output.
1. Remove the last commit.
```
$ git reset --hard HEAD^
```
1. Checkout the `staging` branch.
```
$ git checkout staging
```
1. Move the commit to the `staging` branch.
```
$ git cherry-pick <commit hash>
```

### What is wrong with this sample JSON syntax?

```
{
  "first_name" : "Franz",
  "last_name" : "Kafka",
  "location" : "San Francisco"
  "streams" : true,
  "kafka" : 2.3
}
```

#### Answer
A comma is missing after ``"San Francisco"`` at line #4.

### How many Kafka topics are created by default when you install Confluent Platform?

Scenario: Complete step 1 of [this quick start](https://docs.confluent.io/current/quickstart/ce-docker-quickstart.html) to
install a local version of Confluent Platform. After completing step 1, what are the names of the default topics that
are created by Kafka?

#### Answer
The following three Kafka topics are created by default when you install Confluent Platform:
- docker-connect-configs
- docker-connect-offsets
- docker-connect-status
