# Deployments

Deployments are tied to Git branches. The docs and site will deploy when there is a push to `main`.

The production Minecraft servers will deploy from `main` periodically. The beta Minecraft servers will push on push to `main`. Deployments can also happen on demand, but this is kept to a minimum so that players aren't kicked off of the server for restarts.

Here's how deployments function:

- GitHub Actions builds the code and configuration for the server
- The built artifacts are uploaded via `rsync` to the server
- Docker containers are repulled and re-built if needed
- Docker containers are restarted
