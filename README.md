# Usage

Please see the documentation covering the [Bundles](https://www.authelia.com/integration/deployment/docker/#bundles)
and the [local](https://www.authelia.com/integration/deployment/docker/#local) bundle for usage instructions.

### Quick howto

```
(py39) chiararasi@n181-p119 authelia-demo % ./setup.sh
Checking for pre-requisites
The script requires root access to perform some functions such as modifying your /etc/hosts file
Would you like to elevate access with sudo? [y/N] y
Pulling Authelia docker image for setup
2024/10/31 14:02:47 must use ASL logging (which requires CGO) if running as root
Resetting docker-compose.yml, configuration.yml and users_database.yml
error: pathspec 'docker-compose.yml' did not match any file(s) known to git
error: pathspec 'authelia/configuration.yml' did not match any file(s) known to git
error: pathspec 'authelia/users_database.yml' did not match any file(s) known to git
What root domain would you like to protect? (default/no selection is example.com):
Generating SSL certificate for *.example.com
Enter your username for Authelia: chiara
Enter your display name for Authelia (eg. John Doe): Chiara Rasi
[+] Running 4/4d for chiara:
 ✔ Container authelia  Started                                                                                                                                                                              0.7s
 ✔ Container traefik   Started                                                                                                                                                                              0.8s
 ✔ Container public    Started                                                                                                                                                                              0.6s
 ✔ Container secure    Started                                                                                                                                                                              0.6s
Setup completed successfully.

You can now visit the following locations:
- https://public.example.com - Bypasses Authelia
- https://traefik.example.com - Secured with Authelia one-factor authentication
- https://secure.example.com - Secured with Authelia two-factor authentication (see note below)

You will need to authorize the self-signed certificate upon visiting each domain.
To visit https://secure.example.com you will need to register a device for second factor authentication and confirm by clicking on a link sent by email. Since this is a demo with a fake email address, the content of the email will be stored in './authelia/notification.txt'.
Upon registering, you can grab this link easily by running the following command: 'grep -Eo '"https://.*" ' ./authelia/notification.txt'.
(py39) chiararasi@n181-p119 authelia-demo %
```