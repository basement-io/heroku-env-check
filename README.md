# About this project

This project is to be used as a buildpack in a heroku application to check whether or not all the environment variables
that are set in the `.env.development` file are present or not.


## Using

1. Make sure that you have a `.env.development` file in the root of you project
2. If some of the varialbles in the `.env.development` are optional, you can create a file called `.env.optional`, variables listed in there will not make the script to fail
3. Just add this buildpack before any buildpack that might depend on the varialbles being checked

## Examples

If you have a `.env.development` file like this:

```
SOME_API_KEY=the value of the key
OTHER_ENV_VAR:hello
#COMMENTED_VAR=I am not checked
```

The script will only pass if the `SOME_API_KEY` and `OTHER_ENV_VAR` are set for you heroku application

Now, if you have a `.env.optional` file with:

```
#SOME_API_KEY
OTHER_ENV_KEY
```

Then only the `SOME_API_KEY` is necessary to be present
