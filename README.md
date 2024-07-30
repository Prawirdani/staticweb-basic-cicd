# Basic Automated CI/CD Workflow for Static Frontend Applications

This repository contains a basic CI/CD (Continuous Integration/Continuous Deployment) workflow for automatically building and deploying static frontend applications using GitHub Actions and a Compute Instance.

## Workflow Overview

1. **Trigger**: The workflow is initiated when a new semantic versioning (semver) tag is pushed to the repository.
2. **Release Creation**: A new GitHub Release is automatically created based on the semver tag.
3. **Build and Deploy**: The creation of the release triggers the build and deploy workflow.

## Build Process

- The build process is executed on a GitHub Runner.
- After successful build, the generated static files are sent to a Compute Instance via SSH.

## Deployment

- The example uses [Nginx](https://nginx.org/en/) as the web server for hosting the static files.
- You can easily adapt this to use other web servers like Apache, Caddy, etc.

## Compatibility

This workflow is suitable for frontend libraries/frameworks that require a build step to generate static files, such as:

- React
- Angular
- Vue.js
- And similar libraries/frameworks

⚠️ **Important Note**: This workflow is not compatible with Server-Side Rendering (SSR) meta-frameworks like:

- Next.js
- Nuxt.js
- SvelteKit
- Other SSR-focused frameworks

## Setup Instructions
1. Ensure you have a Compute Instance / VPS with SSH access. It can be an EC2 instance, DigitalOcean Droplet, or any other cloud provider.
2. Generate an SSH key pair and add the public key to the Compute Instance's `~/.ssh/authorized_keys` file.
3. Setup your **SSH_HOST**, **SSH_USER**, and **SSH_PRIVATE_KEY** in the repository secrets. The PRIVATE_KEY is the private key you generated in the previous step.
4. Focus on the `.github/workflows/` dir. You can customize the deployment process to suit your needs.

## Usage

1. Develop your frontend application as usual.
2. When ready to deploy, create and push a new semver tag:
   ```
   git tag v1.0.0
   git push origin v1.0.0
   ```
3. The workflow will automatically trigger, creating a new release and deploying your application.
