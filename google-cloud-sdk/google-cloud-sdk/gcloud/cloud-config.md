# gcloud config

### Connect

```text
gcloud auth application-default login
```

### The Cloud SDK supports multiple configurations and allows us to activate the one we want to use easily.

Create a new gcloud configuration

`gcloud config configurations create (CONFIG_NAME)`

\(Note that creating a configuration will automatically activate it as well\)

List all of your gcloud configurations

`gcloud config configurations list`

Activate another existing gcloud configuration

`gcloud config configurations activate (CONFIG_NAME)`

### List the settings for your active configuration

`gcloud config list`

### List Zone: 

```text
gcloud compute zones list
```

### List Regions:

```text
gcloud compute regions list
```

### Assign a project to a configuration

`gcloud config set project (PROJECT_ID)`

### Set account for your configuration

`gcloud config set account (ACCOUNT_ID)`

### Set Default Zone -&gt; **Important for Exam,**

```text
gcloud config set compute/zone ZONE
```

#### !!! Please check name of Zone - Zone always should be with REGION-\[a\]\[b\]\[c\].. e.g. us-central1**-f**

### Set Default Region -&gt; **Important for exam**

```text
gcloud config set compute/region REGION
```

!!! Please check name of Region - Region should not have zone prefix us-central1.  Sometime options may look similar but you need to figure out the difference.

### You can unset both region and zone using 

```text
gcloud config unset compute/zone
```

```text
gcloud config unset compute/region
```

## **Project setup**

If you need to set gcloud commands for Multiple account - You can initialize every time but its tedious to do it.. gcloud has shortest method to create multiple profile.

```text
// Creates default profile which will be used every time if no parameter is used. 
$ gcloud init 
```

You can check that by following commands

```text
$ gcloud config configurations list
NAME     IS_ACTIVE  ACCOUNT            PROJECT            DEFAULT_ZONE   DEFAULT_REGION
default  True       gcptraince@gmail.com  gcptraince  us-west1-a  us-west1
```

2. You can create named profile by using following gcloud command

```text
$ gcloud config configurations create gcptraince_p
Created [gcptraince_p.
Activated [gcptraince_p].
```

3. Now you can use gcloud init to set the profile for gcpptraince\_p

```text
$ gcloud init 
Choose option 1 ->  Re-initialize This configuration [gcptraince_p] with new settingsuse account login 
Choose project 
Choose default Zone 
```

Now your profile is created   \(// you can create multiple profiles connects different project/accounts \)

You can check profile details using

```text
$ gcloud config list
```

```text
$ gcloud config configurations list
```

4. Activate profile

use following gcloud command to activate profile

```text
$ gcloud config configurations activate gcptraince_p
$ gcloud config configurations activate default
```

5. You can delete any profile using

```text
gcloud config configurations delete gcptraince_p
```

