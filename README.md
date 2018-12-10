# wiser-cron

A Helm Chart Starter to create cronJobs from a single configuration

## TL;DR

Install the starter in `$HELM_HOME/starters` (default is `$HOME/.helm/starters`)...

```bash
$ cd $HELM_HOME/starters
$ git clone git@github.com:WiserSolutions/wiser-cron.git
```

Create a Helm chart for your cron jobs...

```bash
$ cd your_work_directory
$ helm create --starter wiser-cron my-cronjobs
```

Edit to taste...

The resulting *Helm Chart* is pretty similar to a basic *deployment* starter with the addition of a `cron` section. Update the *podSpec* int `templates/cronjob.yaml` to match your specific needs for *volumes*, *environment variables* etc. Then setup your `cron` entries in `values.yaml`

Install...

```bash
$ helm install --name <your-release-name> --namespace <your-namespace> my-cronjobs
```

## cron entry details

* historyLimit: how many results to keep around
* backoffLimit: how many times to try before giving up
* jobs: an array of cronjob specifications
    * name: the name of the job that will be created in the cluster
    * schedule: a crontab compatible specification (remember to put quotes around this)
    * command: a command string that will be passed to "sh -c" by default


