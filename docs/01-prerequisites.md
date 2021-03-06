# Prerequisites

## Google Cloud Platform

This tutorial leverages the [Google Cloud Platform](https://cloud.google.com/) to streamline provisioning of the compute infrastructure required to bootstrap a Kubernetes cluster from the ground up. [Sign up](https://cloud.google.com/free/) for $300 in free credits.

[Estimated cost](https://cloud.google.com/products/calculator/#id=55663256-c384-449c-9306-e39893e23afb) to run this tutorial: $0.23 per hour ($5.46 per day).

> The compute resources required for this tutorial exceed the Google Cloud Platform free tier.

## Google Cloud Platform SDK

### Install the Google Cloud SDK

Follow the Google Cloud SDK [documentation](https://cloud.google.com/sdk/) to install and configure the `gcloud` command line utility.

Verify the Google Cloud SDK version is 262.0.0 or higher:

```
gcloud version
```

---

_メモ:_
_今回試したバージョンは次の通り。_

```
Google Cloud SDK 289.0.0
alpha 2020.04.10
beta 2020.04.10
bq 2.0.56
core 2020.04.10
gsutil 4.49
kubectl 2020.04.10
```

---

### Set a Default Compute Region and Zone

This tutorial assumes a default compute region and zone have been configured.

If you are using the `gcloud` command-line tool for the first time `init` is the easiest way to do this:

```
gcloud init
```

---

_メモ:_
_`gcloud init` を実行した後に表示されるプロンプトで"新しいプロジェクトを作成する"を選び、何かユニークな(※他の人とも被ってはいけないっぽい)名前のプロジェクトを作成しておく必要がある。あるいは`gcloud projects create`でプロジェクトを作成する([#219](https://github.com/kelseyhightower/kubernetes-the-hard-way/issues/219))。([#225](https://github.com/kelseyhightower/kubernetes-the-hard-way/pull/225)のせいで余計にわかりにくくなってないか…？)_

---

Then be sure to authorize gcloud to access the Cloud Platform with your Google user credentials:

```
gcloud auth login
```

Next set a default compute region and compute zone:

```
gcloud config set compute/region us-west1
```

Set a default compute zone:

```
gcloud config set compute/zone us-west1-c
```

> Use the `gcloud compute zones list` command to view additional regions and zones.

## Running Commands in Parallel with tmux

[tmux](https://github.com/tmux/tmux/wiki) can be used to run commands on multiple compute instances at the same time. Labs in this tutorial may require running the same commands across multiple compute instances, in those cases consider using tmux and splitting a window into multiple panes with synchronize-panes enabled to speed up the provisioning process.

> The use of tmux is optional and not required to complete this tutorial.

![tmux screenshot](images/tmux-screenshot.png)

> Enable synchronize-panes by pressing `ctrl+b` followed by `shift+:`. Next type `set synchronize-panes on` at the prompt. To disable synchronization: `set synchronize-panes off`.

Next: [Installing the Client Tools](02-client-tools.md)
