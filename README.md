Role Name
=========

This role automates creating a Windows Server VM in AzureCloud, and afterwards install a Notepad++ with specific version.

Requirements
------------

Before run this role with ansible-playbook you will have to make some basics presets in AzureCloud.
1.First of all you need to create account in Azure.
2.Then you need to set up Azure service principal:
  - Login:  "az login" (will redirect to your browser, and after sucsessfull authentication console will print out creds of your account including appId that yoy will      use in the next steps)
  - Run is command in your console:    "az ad sp create-for-rbac --name ansible"
  - Then you need assign a role to the Azure service principal: "az role assignment create --assignee <appID> --role Contributor"
  - Run: "az account list".  to see all your accounts
  - Run: "az account set --subscription '<yourAppId>'"

Role Variables
--------------

The role uses next variables:
  - password (Password for user the technical user(azureuser) of your VM. Enter in with --extra-vars="password=yourpassword" while executing ansible playbook)
  - publicipaddress (Creates automatically on step of WinRM of ansible tasks)
  
Dependencies
------------

Main dependencies are:
  - WinRM of python(pip install "pywinrm>=0.3.0")
  - Chocolatey Ansible module (ansible-galaxy collection install chocolatey.chocolatey)
    
Example Playbook
----------------
Playbook described in file depl.yml. You need to copy this role to your roles folder.($HOME/roles). And copy depl.yml to your home folder($HOME/depl.yml)
Run playbook with:
  ansible-playbook --extra-vars "password=Ielt%arg12b" -i depl.yml
  

License
-------

BSD

Author Information
------------------

Mikhail Khovanskiy, Moscow 02:16 Friday, 23.07.2021
