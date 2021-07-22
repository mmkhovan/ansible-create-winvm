Role Name
=========

This role automates creating a Windows Server VM in AzureCloud, and afterwards install a Notepad++ with specific version.

Requirements
------------

Before run this role with ansible-playbook you will have to make some basics presets in AzureCloud.
1.First of all you need to create account in Azure.
2.Then you need to set up Azure service principal:
  - Login:  az login (will redirect to your browser, and after sucsessfull authentication console will print out creds of your account including appId that yoy will      use in the next steps)
  - Run is command in your console:    az ad sp create-for-rbac --name ansible
  - Then you need assign a role to the Azure service principal: az role assignment create --assignee <appID> --role Contributor
  - If you already installed ansible, you may need download the WinRM python requirement:  pip install "pywinrm>=0.3.0"

Role Variables
--------------

The role uses next variables:
    - password (Password for user the technical user(azureuser) of your VM)
    - publicipaddress (Creates automatically on step of WinRM of ansible tasks)

Dependencies
------------

Main dependencies are:
    - WinRM of python(pip install "pywinrm>=0.3.0")
    -
    
Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
