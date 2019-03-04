# haraka.ml
# [VPS setup](https://discuss.erpnext.com/t/error-fresh-install-on-ubuntu-16-06/25656)

## INSTALL FRAPPE / ERPNEXT
Ubuntu 16.04 64bit Minimal Fresh install.
Logged in with Root -
1 ```apt-get update -y && apt-get upgrade -y && apt-get dist-upgrade -y && apt-get install python-minimal -y```
2 ```apt-get install -y git build-essential python-setuptools python-dev libffi-dev libssl-dev```
3 ```wget https://raw.githubusercontent.com/frappe/bench/master/playbooks/install.py```
4 ```python install.py --production --user frappe```
>>> [Setup a password for Admin and user frappe]

Got the link to login, Used the username and password I created in step 5 and I was good to go.

USERNAME:	Administrator
PASSWORD:	frappe

## [HTTPS](https://discuss.erpnext.com/t/how-to-make-https-for-my-erpnext/19247/11)(https://discuss.erpnext.com/t/problem-setting-up-let-encrypt/30572/6)
Enable https and use letsecrypt on default site (site1.local) on frappe bench:
 1.	Set DNS Multitenancy on by running :
	 	sudo bench config dns_multitenant on
 2.	Add custom domain to site1.local by running :
 		sudo bench setup add-domain erp.example.com 
 	and enter site1.local when asked
 3.	Setup letsecrypt by running 
 		sudo -H bench setup lets-encrypt site1.local --custom-domain erp.example.com

## [DEMO DATA](https://discuss.erpnext.com/t/trying-to-install-demodata-on-new-site/34596)
Demo is merged into ERPNext.

```cd frappe-bench```
```bench --site site1.local execute erpnext.demo.demo.make```

### Make a demo
Start with a fresh site, create new site and follow these steps
```bench --site <site-name> reinstall```

### Install Demo
```bench --site <site-name> execute erpnext.demo.demo.make```

If Demo breaks, to continue
```bench --site <site-name> execute erpnext.demo.demo.simulate```

