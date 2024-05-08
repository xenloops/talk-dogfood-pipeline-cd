# Deployment

Finally, the meat of the action.

We have:

* Code in a repo
* Secrets that we need to keep secret
* 

## Now, let's put them together!

<br /><br /><br /><br />

### Prerequisites

From last year's talk:

* [Install Jenkins](https://github.com/xenloops/talk-dogfood-pipeline-ci/blob/main/jenkins.md)
* [Install Dependency-Check (for SCA)](https://github.com/xenloops/talk-dogfood-pipeline-ci/blob/main/sca.md)
* [Install SonarQube (for SAST)](https://github.com/xenloops/talk-dogfood-pipeline-ci/blob/main/sast.md)
* [Create the pipeline as code (for best results)](https://github.com/xenloops/talk-dogfood-pipeline-ci/blob/main/pipe_as_code_2.md)

<br /><br /><br /><br />

### Add a secret

* Before, just grabbed a copy of the code
* What if we need to check it out?

1. Create asymmetric keypair
   2. ssh-keygen -b 4096
   3. cat ~/.ssh/id_rsa.pub
   4. Copy for next steps
3. In GitHub:
   1. Settings
   2. SSH and GPG keys
   4. New SSH key button
   7. Name the key
   8. Type: Authentication key
   8. Paste copied public key
1. In Jenkins:
   1. Go to the project > Configure page
   2. Scroll to Pipeline section > Repositories
   3. Under Credentials, Click +Add button and select Jenkins
   4. For Kind, select SSH Username with private key
   5. For Scope: Global
   6. For ID, enter a unique name for the key
   7. For Username: the login for your repo (optionally treat it as a secret)
   8. Copy the private key from a terminal using sudo cat ~/.ssh/id_rsa
   9. Paste the private key into Jenkins
   10. Enter the passphrase used when creating the keypair
   11. Click Add

New window will open

Select Kind drop down value as SSH Username with private key. and add ID whatever you want.
Provide Description and user name of your instance and select Private key as Enter Directly and paste your.



