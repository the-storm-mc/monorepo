# Environments

The Storm has two environments for its Minecraft servers -- Beta and Prod. The beta environment is pinned to the `dev` branch of the server repository. It automatically redeploys on push to main. It is not intended for anything other than testing.

The prod environment are the servers that players log into and play on. These servers are meant to be more stable, have high uptime, and should be deployed to as little as possible.

| Environment | Server   | Address                       |
| ----------- | -------- | ----------------------------- |
| Prod        | Survival | ts-mc.net, survival.ts-mc.net |
| Beta        | Survival | beta.survival.ts-mc.net       |
