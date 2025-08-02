# GITLAB in RANCHER
## How to install
1. In your rancher cluster, start with creating the secret for the postgres database
   - This should be the same as the password that will be set in the postgres.yaml file
   - This should be in whatever namespace GitLab wil lbe in.

1. Create the postgres-job.yaml from kubectl interface to setup the database 
   - Copy Pasta code
   - Modify the code to reflect your wanted changes aka password, username, database
   - Ensure this job will run in the same location as your postgresql database

1. Create the issuer.yaml from the kubectl interface for TLS
   - Copy Pasta code either Staging or Production
   - Modify the code to reflect your domain and DNS Solver
   - Ensure the secret for whatever solver you go with exists.

1. Add the chart repo to rancher `http://charts.gitlab.io/`
1. Install the helm chart labeled **gitlab**
1. Update the values.yaml of that helmchart
   1. Copy pasta gitlab-values.yaml to the values
   1. Update any of the comments to what you need for your situation
1. Increase the timeout from 600s to 1200s or something along those lines
1. Pray it all works :)


### Additional Links:

Youtube link for video instruction: 
Docs for postgresql configuration for install in github

https://gitlab.com/gitlab-org/charts/gitlab/-/blob/master/doc/advanced/external-db/_index.md

https://docs.gitlab.com/charts/advanced/external-db/

Docs for Gitlab runner

https://docs.gitlab.com/runner/install/kubernetes/