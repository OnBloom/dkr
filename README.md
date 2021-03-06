This is a small project that started as a few aliases, and then grew into a small framework.

Extendable `docker` cli wrapper. Allows the user to easily add new functionality.

Any command that doesn't exist in `dkr` automatically gets delegated to `docker`.

# Install

```bash
git clone git@github.com:JoelJ/dkr.git
cd dkr
./install
```

There are options to override default locations, etc in the installer.
To see what they are, run:

```bash
./install --help
```

For example, you can override where the dkr bin is installed by running:

```bash
./install --bin-file /bin/dkr
```

# Usage

If you run only `dkr` help will be printed out, including a list of all the extensions. 

# Extending

Any non-executable file in `$DKR_HOME` will be sourced. `$DKR_HOME` by default is `~/.dkr`.

How commands are called:

* Any bash function matching the pattern: `__dkr-{name}` will be added as a new function of dkr and can be called with `dkr {name}`.
* `$DKR_HOME` is added to the `PATH` so any executable files in `$DKR_HOME` matching the naming conventions will also be included.
* If `dkr {name}` is called and `__dkr-name` does not exist, then `docker {name}` will be called instead.
* The `summarys` are chosen by any function/executable named `__dkr-{name}-summary_`
* The `helps` are chosen by any function/executable named `__dkr-{name}-help_`
