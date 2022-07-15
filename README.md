# Development Versioned Flows

This repository is to persist the NiFi Registry Buckets (i.e., flows) in the development stage. 

# Usage

This works with the apache/nifi-registry images in DockerHub. Configure the .conf/provider.xml file in nifi registry passing the following values:

Environment Variable | Configuration Property | Values |
--- | --- | --- |
NIFI_REGISTRY_FLOW_STORAGE_DIR  | Flow Storage Directory  | /opt/nifi-registry/nifi-registry-current/flow_storage |
NIFI_REGISTRY_FLOW_PROVIDER     | Valid values: git, file | git                                                   |
NIFI_REGISTRY_GIT_REMOTE        | Remote to Push          | origin                                                |
NIFI_REGISTRY_GIT_USER          | Remote Access User      | ${github_user}                                        |
NIFI_REGISTRY_GIT_PASSWORD      | Remote Access Password  | ${ssh_key}                                            |
NIFI_REGISTRY_GIT_REPO          | Remote Clone Repository | https://github.com/${github_user}/${repo_name}.git    |

where

- github_user: The name of the user of Github where the versioned flow file is created
- ssh_key: The SSH key for accessing the repository as developer
- repo_name: The name of the storing repository 

**Note**: The official image apache/nifi-registry does not come with `git` installed. An installation to the image with a Dockerfile is recommended.
