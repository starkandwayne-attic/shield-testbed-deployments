# For testing SHIELD in BOSH lite

These are test files for `BOSH lite` only. Before running the setup script, please ensure:
* The BOSH lite VM is up and running
* You have a working local Cloud Foundry

To initially set up your SHIELD environment, please run the following script from the parent directory of this project:

```
./bin/setup-env
```

The setup script will:

* Build the shield CLI from source
* Upload the shield (dev), docker, and docker-postgres BOSH releases
* Set up an initial schedule, store, retention policy, target, and backup job. These will need to be updated with valid information.

To view the schedule, store, etc. that were created, use the `list` option for each type. e.g.:

```
shield -H http://10.244.2.11:8080 list stores
```

(Please see the [Shield README](https://github.com/starkandwayne/shield#cli-usage-examples) for all available commands and their syntax.)

Optionally, you can set an environmental variable instead of using the `-H` flag:

```
export SHIELD_TARGET=http://10.244.2.11:8080
shield list stores
```
