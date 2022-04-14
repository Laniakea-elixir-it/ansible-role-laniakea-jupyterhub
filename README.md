Laniakea JupyterHub
===================

This role installs and configure JupyterHub and JupyterHub, creating a new user with a random password to access
and use JupyterHub.\
This role follows the [JupyterHub and JupyterLab installation guide](https://github.com/jupyterhub/jupyterhub-the-hard-way/blob/HEAD/docs/installation-guide-hard.md).

It has been tested on Ubuntu 20.04


Role Variables
--------------

### Dependencies variables
| Variable           | Description                              | Default |
| ------------------ | ---------------------------------------- | ------- |
| wheel_version      | Version of wheel installed with pip      | 0.37.1  |
| jupyterhub_version | Version of jupyterhub installed with pip | 2.2.2   |
| jupyterlab_version | Version of JupyterLab installed with pip | 3.3.3   |
| notebook_version   | Version of notebook installed with pip   | 6.4.10  |
| markupsafe_version | Version of markupsave installed with pip | 2.0.1   |
| ipywidgets_version | Version of ipywidgets installed with pip | 7.7.0   |

### JupyterHub configuration variables
| Variable                  | Description                                        | Default                                          |
| ------------------------- | -------------------------------------------------- | ------------------------------------------------ |
| jupyterhub_username       | Name of the user created to access JupyterHub      | jupyterhub                                       |
| jupyterhub_virtualenv     | Path to JupyterHub virtual environment             | /opt/jupyterhub                                  |
| jupyterhub_virtualenv_bin | JupyterHub virtualenv bin directory                | {{ jupyterhub_virtualenv }}/bin                  |
| jupyterhub_config_dir     | Directory containing JupyterHub configuration file | {{ jupyterhub_virtualenv }}/etc/jupyterhub       |
| jupyterhub_config_file    | Path to JupyterHub configuration file              | {{ jupyterhub_config_dir }}/jupyterhub_config.py |
| jupyterhub_unit_name      | Name for jupyterhub unit file                      | jupyterhub.service                               |
| jupyterhub_systemd_dir    | Path to directory containig JupyterHub unit file   | {{ jupyterhub_virtualenv }}/etc/systemd          |
| jupyterhub_relative_url   | URL where JupyterHub is accessible                 | /jupyter                                         |
| role_debug                | If true, the JupyterHub user password is printed   | false                                            |

### Conda variables
| Variable                   | Description                                                 | Default                                                                        |
| -------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------ |
| conda_gpg_key_url          | URL to conda gpg key                                        | https://repo.anaconda.com/pkgs/misc/gpgkeys/anaconda.asc                       |
| conda_repo                 | URL to conda deb repo                                       | deb [arch=amd64] https://repo.anaconda.com/pkgs/misc/debrepo/conda stable main |
| conda_dir                  | Path where conda is installed with apt                      | /opt/conda                                                                     |
| conda_script_path          | Path were conda script is linked to be available to users   | /etc/profile.d/conda.sh                                                        |
| conda_envs_dir             | Path were conda environments are installed                  | {{ conda_dir }}/envs                                                           |
| default_conda_env_name     | Name of the default conda env for JupyterHub                | python                                                                         |
| default_conda_env_dir      | Path to the default conda env                               | {{ conda_envs_dir }}/{{  |default_conda_env_name }}                            |
| default_conda_env_packages | Packages installed in the conda env (ipykernel is required) | [ipykernel]                                                                    |
| python_version             | Python version used for the default conda env               | 3.7                                                                            |

### Nginx variables
| Variable                   | Description                                                 | Default    |
| -------------------------- | ----------------------------------------------------------- | ---------- |
| nginx_conf_dir             | Nginx configuration directory                               | /etc/nginx |
| jupyterhub_nginx_site_file | Name of the file for JupyterHub reverse proxy configuration | jupyterhub |

Dependencies
------------

None


Example Playbook
----------------

```yml
- hosts: all
  roles:
    - role: "/path/to/ansible-role-jupyterhub/"
      become: true
```
License
-------


Author Information
------------------

[Daniele Colombo](https://github.com/dacolombo)