# vault-ssh-demo

This Demo is intented to quickly setup an aws environment to showcase the ability to ssh into hosts with vault.
First question is....why do I need vault to ssh into hosts? 
No need to say that password protected logins are less and less secure.
Openssh allows for a large suite of possibilites amongst those: public key authentication.
Public Key authentication is a mechanism based on cryptographic keys.
It is much more secure than passwords, but in itself it has also its limits:
* How do I manage the lifecycle of the keys used to access differents infrastructure components?
* How do I manage onboarding/offboarding of users?
* What happens if a private key of a user get stolen?
* ...

Hopefully, Openssh provides also a mechanism to solve this concerns: it is possible to use signed certificates.
For this to work one needs:
1. A Certificate Authority (and the associated public key)
2. Copy the public key in all target hosts ssh configuration
3. Have all user who want to ssh in those hosts to have their private key signed by the CA
4. Finally the user can log in with a command such as: `ssh -i signed_key.pub -i <public_key.pub> user@host`

The 2 subdirectories in this folder and the associated files will do all the work for you.
What you need:
1. a Terraform Cloud account
2. an AWS subscription
