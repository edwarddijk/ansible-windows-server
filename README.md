# Basic Windows Server Configuration

## Requirements

- Microsoft Windows Server 2019
- An Internet Connection
- Python Modules
    - PyWinRM
    - requests-credssp
- Ansible Collections
    - community.windows
    - chocolatey.chocolatey

### Install Ansible Requirements

```bash
ansible-galaxy install -r requirements.yaml
```

## Variables


| Name | Type |Description | Default | 
|------|------|-------|---------|
| cdrom_drive | Boolean | Is a CD-ROM Drive available in the system | yes |
| cdrom_drive_letter | Character | The driveletter to configure for the CD-ROM Drive | Z |
| pagefile_size | Integer | Size of the pagefile in megabyte to be configured | System Memory in MB |
| remote_desktop | Boolean | Enable the Remote Desktop for Admins feature | no |
| staging_directory | String | Storage directory for files needed during install and configuration | C:\Install |
| sysmon_config_url | String | Web location for the Sysmon config xml | https://raw.githubusercontent.com/SwiftOnSecurity/sysmon-config/master/sysmonconfig-export.xml |
| print_server | Boolean | Is the server a Print Server | no |

## Structure

Information : https://stackoverflow.com/questions/55773505/where-to-place-requirements-yml-for-ansible-and-use-it-to-resolve-dependencies

### roles\requirements.yaml

```yaml
---    
- src: https://gitlab.com/EdwardDijk/ansible-role-windowsserver.git
  scm: git
  version: main
  name: windowsserver
```

```bash
ansible-galaxy install -r roles/requirements.yaml -p ./roles/
```

## Configuration Items

- Hostname
- Set Pagefile to memory size 
- Disable LMHOSTS Lookup
- Disable NetBIOS over TCP/IP
- 
