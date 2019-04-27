# gcloud config

The Cloud SDK supports multiple configurations and allows us to activate the one we want to use easily.

Create a new gcloud configuration

`gcloud config configurations create (CONFIG_NAME)`

\(Note that creating a configuration will automatically activate it as well\)

List all of your gcloud configurations

`gcloud config configurations list`

Activate another existing gcloud configuration

`gcloud config configurations activate (CONFIG_NAME)`

List the settings for your active configuration

`gcloud config list`

Assign a project to a configuration

`gcloud config set project (PROJECT_ID)`

Set account for your configuration

`gcloud config set account (ACCOUNT_ID)`

