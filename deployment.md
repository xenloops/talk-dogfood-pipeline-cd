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

<details>
  <summary> 1. Create asymmetric keypair </summary>
   
   1. ssh-keygen -b 4096
   1. cat ~/.ssh/id_rsa.pub
   1. Copy for next steps

</details>

<details>
  <summary> 2. Setup key in GitHub </summary>

   1. Settings
   2. SSH and GPG keys
   4. New SSH key button
   7. Name the key
   8. Type: Authentication key
   8. Paste copied public key

</details>

<details>
  <summary> 3. Setup key in Jenkins </summary>
  
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
   12. Back on the project's Configure page, select the credential just created
   13. Click Save

</details>

<details>
  <summary> 4. Configure Git host key verification in Jenkins </summary>

  The console output of a build will show "You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist." We need to tell Jenkins how to identify the remote host it's connecting to.
  
  1. Run cat ~/.ssh/known_hosts in a terminal
  2. Copy the www.github.com key (to the end "=")
  3. Manage Jenkins > Security > Git Host Key Verification Configuration
  4. For Host Key Verification Strategy, select Manually Provided Keys
  5. Paste the www.github.com key into the Approved Host Keys field
  6. Click Save
   
</details>


[Next slide](verify.md)

