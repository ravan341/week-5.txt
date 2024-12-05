# Jenkins Pipeline Setup

This README provides guidance on configuring a Jenkins pipeline to ensure continuous integration (CI) for a project hosted on GitLab or GitHub. The pipeline validates build stability, triggers based on repository changes, and offers options for concurrency control and durability.This Jenkins pipeline is configured to trigger builds automatically based on changes in a GitLab or GitHub repository. It includes options to manage concurrency, credentials, build triggers, and durability optimizations, ensuring an efficient CI process.

## Prerequisites

- **Jenkins**: Ensure Jenkins is installed and accessible.
- **GitLab/GitHub Access**: Generate API tokens for access to GitLab and GitHub.
- **Webhook Setup**: Configure webhooks in GitLab/GitHub to notify Jenkins of repository changes.

## Pipeline Configuration

### General Settings

1. **Discard Old Builds**: Enable to automatically discard older builds, freeing up storage.
2. **Concurrency Management**:
   - **Do not allow concurrent builds**: Ensures only one build is active at any given time.
   - **Do not allow the pipeline to resume if the controller restarts**: Prevents builds from resuming post-restart.

### GitHub and GitLab Connections

- **GitHub Project**: Connect Jenkins to a specific GitHub repository.
- **GitLab Connection**: Use credentials and repository name to link a GitLab repository.

   - **Use Alternative Credential**: Specify alternative credentials if needed for GitLab.

### Pipeline Options

1. **Pipeline Speed/Durability Override**: Adjust speed and durability settings as needed.
2. **Preserve Stashes from Completed Builds**: Retain stashes across builds if enabled.

### Build Triggers

Configure these triggers to automate builds:

1. **Build after other projects are built**: Useful for dependent projects.
2. **Build periodically**: Schedule builds at specific intervals.
3. **Build when a change is pushed**:
   - **GitLab**: Set up a webhook with URL `http://localhost:8080/project/Hello%20world`
   - **Gitee**: Set up a webhook with URL `http://localhost:8080/gitee-project/Hello%20world`
4. **GitHub Branches**: Monitor specific branches for changes.
5. **GitHub Pull Requests**: Optionally trigger builds for pull requests.
6. **GitHub hook trigger for GITScm polling**: Poll GitHub for SCM changes.
7. **Poll SCM**: Poll SCM for changes periodically to trigger builds.
8. **Quiet Period**: Set a delay before triggering builds after changes.



## Pipeline Script Example

The following example pipeline script demonstrates a basic CI process with build, test, and deploy stages:
pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}



## Pipeline Script

![image](https://github.com/user-attachments/assets/b973100b-09a5-44e5-b9cf-3bbca2702d36)


### OUTPUT
![487402c0-8524-47f2-a5a3-742ee82b76f2](https://github.com/user-attachments/assets/ef1037d0-bd26-4311-b3eb-56ce237aece8)



