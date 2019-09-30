# IAmRepoSpawner
Creates `x` number of empty repositories under the given user or organization.

### SYNOPSIS:
`repo-spawner [-o=<org_name>] [-u=<username>] [-n=<number-of-repos>] [-r=<repo-name>]`

## DESCRIPTION:
Creates n repositories for the user (if -u=<username> is used) or for an organization (if -o=<org_name> is used instead) with the name <repo-name><n>. If the name already exists, it will skip and continue to the next iteration.

### PRE-REQUISITES:
Before running this script, you must [create a Personal Access Token (PAT)](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/) with the permissions `<repo>` and `<admin:org>` scopes. Read more about scopes [here](https://developer.github.com/apps/building-oauth-apps/scopes-for-oauth-apps/). Once created, you must export your PAT as an environment variable named <GITHUB_TOKEN>.
- Exporting PAT as GITHUB_TOKEN
`export GITHUB_TOKEN=abcd1234efg567`

#### OPTIONS:
`--org`
`-o`
When running the tool, this flag sets the API endpoint to point to an organization (specififed by `-o=<org_name>`), creating the repos under that organization
- _NOTE:_ Can NOT be used with the -u option.

`--user`
`-u`
When running the tool, this flag sets the API endpoint to point to a user (specified by `-u=<username>`), creating the repos under that account.
- _NOTE:_ Can NOT be used with the -o option.

`--number`
`-n`
When running the tool, this flag denotes the number of repos to create.

`--repo`
`-r`
When running the tool, this flag denotes the name of each repo to be created. The name will be appended with <n>, i.e. MyRepo1, MyRepo2, MyRepo3, etc.

#### EXAMPLE USAGE:
- Lists repos under user account `IAmHughes` that are available to be deleted.
  
`bash repo-cleaner -u=IAmHughes`

- Deletes repos under org "TheBeardedTom" that are named "Test_Repo_*". _For example, Test_Repo_, Test_Repo_qa, Test_Repo_234,_ etc.

`bash repo-cleaner -o=TheBeardedTom -s=Test_Repo_`

- Deletes repos under user "IAmHughes" that are named "MyRepo*". _For example, MyRepo, MyRepo1, MyRepo99, MyRepoQA,_ etc.

`bash repo-cleaner -u=IAmHughes -s=MyRepo`

#### API DOCUMENTATION:
All API documentation can be found at [developer.github.com](https://developer.github.com/v3/)
