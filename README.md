#### Basic CI/CD Using GitHub Actions for Static Website.
Workflows trigger on semver tags, it will create a release and when the release is created, it will trigger the build and deploy workflow. 
Build process using Github Runner and send it to Compute Instance using SSH. In this example, I am using Nginx as a web server, but you can use any other web server like Apache, Caddy, etc.

It can be use for frontend libraries like React, Angular, Vue, etc, that require build step to generate static files.
Please note this won't work if you are using SSR (Server Side Rendering) on Meta frameworks like Next.js, Nuxt.js, SvelteKit, etc.
