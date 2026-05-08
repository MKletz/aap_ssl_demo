# Setup
- Update [Change Mes](/vars/change_mes.yml)
- Update secrets created in [here](/vars/controller_credentials.yml).
    - CloudFlare email/token
    - RHEL Admin
    - Windows Admin
    - Vault if not using dev mode "root" token
- Add applicable hosts to the inventory groups
    - rhel_cockpit
    - windows_iis
- The playbooks will provision Cockpit and IIS before applying the cert. Run before hand to save demo time installing packages.
- Everything is provisioned into the default organization of AAP

# How to demo
- All templates can be found under the ssl_demo label
- The workflow does the following
    - ACME DNS challenge to CloudFlare
    - Stash the resulting cert files into a Hashicorp vault instance
    - Pulls out the certs via a credential lookup and installs in Cockpit and IIS
        - Will likely still have cert errors depending on DNS setup. You can see the Let's Encrypt cert is present by checking it in browser though.