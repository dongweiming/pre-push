[![Build Status](https://travis-ci.org/pre-commit/pre-commit.svg?branch=master)](https://travis-ci.org/pre-commit/pre-commit)
[![Coverage Status](https://img.shields.io/coveralls/pre-commit/pre-commit.svg?branch=master)](https://coveralls.io/r/pre-commit/pre-commit)

## pre-commit

A framework for managing and maintaining multi-language pre-commit hooks.

For more information see: http://pre-commit.com/


##Installation


Before you can run hooks, you need to have the pre-commit package manager installed.

Using pip:

    pip install pre-commit

Non Administrative Installation:

    curl http://pre-commit.com/install-local.py | python

System Level Install:

    curl https://bootstrap.pypa.io/get-pip.py | sudo python - pre-commit

In a Python Project, add the following to your requirements.txt (or requirements-dev.txt):

    pre-commit

##Adding pre-commit plugins to your project

Once you have pre-commit installed, adding pre-commit plugins to your project is done with the .pre-commit-config.yaml configuration file.

Add a file called .pre-commit-config.yaml to the root of your project. The pre-commit config file describes:

| Key             | Description   |
| --------------- |:-------------:|
|repo, sha| 	where to get plugins (git repos). sha can also be a tag.|
|id| 	What plugins from the repo you want to use.|
|language_version| 	(optional) Override the default language version for the hook.See Advanced Features: "Overriding Language Version".|
|files 	(optional)| Override the default pattern for files to run on.|
|exclude 	(optional)| File exclude pattern.|
|args 	(optional)|   additional parameters to pass to the hook.|

For example:

    -   repo: git://github.com/pre-commit/pre-commit-hooks
        sha: 5541a6a046b7a0feab73a21612ab5d94a6d3f6f0
        hooks:
        -   id: trailing-whitespace

This configuration says to download the pre-commit-hooks project and run its trailing-whitespace hook.

other hooks can found from [http://pre-commit.com/hooks.html](http://pre-commit.com/hooks.html)


##Usage


Run

	pre-commit install [-t pre-commit]  # pre-commit will now run on every commit.

or

	pre-commit install -t pre-push	 # pre-push will now run on every push.

to install pre-commit into your git hooks. Every time you clone a project using pre-commit running `pre-commit install` should always be the first thing you do.

If you want to manually run all pre-commit hooks on a repository, run `pre-commit run --all-files`. To run individual hooks use `pre-commit run <hook_id>`.

The first time pre-commit runs on a file it will automatically download, install, and run the hook. Note that running a hook for the first time may be slow. For example: If the machine does not have node installed, pre-commit will download and build a copy of node.
