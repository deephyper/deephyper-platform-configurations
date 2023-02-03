# DeepHyper Platform Configurations

This repository provides a set of configuration files and example scripts for running DeepHyper experiments on various platforms.

The `generic` subdirectory contains a minimal DeepHyper environment example that can be used as a starting point for systems for which there is no existing recipe.

## Using spack.yaml files

Each platform subdirectory in this repository provides a `spack.yaml` file.
A `spack.yaml` file fully describes a Spack environment, including
system-provided packages and compilers. It does so independently of any
`compilers.yaml` or `packages.yaml` files installed in `~/.spack`, thereby
preventing interference with user-specific spack configurations as much as
possible.

You may use `spack.yaml` files to create a
[Spack environment](https://spack.readthedocs.io/en/latest/environments.html)
in which DeepHyper packages will be installed.

If you don't have Spack installed on your platform, clone it and set it up
as follows.

```bash
git clone -c feature.manyFiles=true https://github.com/spack/spack.git
. spack/share/spack/setup-env.sh
```

Remember that the second line needs to be executed every time you open a new
terminal; it may be helpful to create an alias in your bashrc file as a
shortcut.

You will then need to clone `deephyper-spack-packages`, which contains the DeepHyper packages.

```bash
git clone https://github.com/deephyper/deephyper-spack-packages.git
spack repo add deephyper-spack-packages
```

Now clone the present repository and `cd` into the subdirectory relevant
to your platform. For example:

```bash
git clone https://github.com/deephyper/deephyper-platform-configurations.git
cd deephyper-platform-configurations/ANL/Polaris
```

Edit the path to `deephyper-spack-packages` in the `repos` field of the `spack.yaml` file to
match your installation.

Then, execute the following command
(changing _myenv_ into an appropriate name for your environment).

```bash
spack env create myenv spack.yaml
```

Change to a directory outside of the `deephyper-platform-configurations` folders
and activate the environment as follows.

```bash
spack env activate myenv
```

Once you have added the specs you need in your environment, install
everything by executing the following command.

```bash
spack install
```

You may add more specs later on. For more information on how to manage
Spack environments, please refer to the Spack documentation.


## Acknowledgment

This repository was created by following the example of the [Mochi Project](https://github.com/mochi-hpc-experiments/platform-configurations).