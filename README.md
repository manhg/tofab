# tofab

This is a set of fabric utils for deploy multi reserved-proxy servers, with systemd.

Notes:
* Ensure you have systemd in nginx
* Create an Linux user (able to login) on server, setup neccessary SSH keys.
* This doesn't use sudo. It switch to root when need permission. So, be sure to add SSH public key for root account.
* This uses ``rsync``, not ``git`` to deploy. Any files under current project folder will be upload. 
To keep some private, overwrite ``env.x.excludes`` options with list of exclude patterns.


Example fabfile.py

```
#!/usr/bin/env python
from tofab import *

env.x.app = 'your_app'
env.hosts = ['your_app.com']
env.x.base_port = 8000
env.x.n_instances = 2
env.x.remote_path = '/home/your_app'
env.x.wait = 3 # (second) time wait for loading complete
env.user = env.x.app
env.port = 9622
```

Commands:
```
# Setup git folder
fab setup

# Deploy
fab deploy

# Show other features
fab list
```
