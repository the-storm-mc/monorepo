# Monitoring

A public dashboard showing detailed [here](https://p.datadoghq.com/sb/a75dfe26-225b-11ed-b34a-da7ad0900002-db9d77ad26203770040b0c64f56cace3).

The server is monitored with [Datadog](https://www.datadoghq.com/). Alarms exist to ensure the following:

- TCP connections can be established to ts-mc.net:25565
- The documentation site is accessible and the SSL certificate is valid
- The main site is accessible and the SSL certificate is valid
- The LiveMap is accessible and the SSL certificate is valid
- TCP connections can be establish to ts-mc.net:22

These alerts help to catch issues as fast as possible, so that time to resolution can be minimal.

Datadog also takes care to monitor host metrics, Docker container metrics, store logs, and much more. These functionalities help to detect problems before they happen, and have easy access to historical logs to help diagnose problems.

<figure markdown>
  ![Screenshot of the Datadog metrics UI](/assets/images/datadog-metrics.png){ width="500" }
  <figcaption>Datadog metrics for The Storm.</figcaption>
</figure>

<figure markdown>
  ![Screenshot of the Datadog metrics UI](/assets/images/datadog-tests.png){ width="500" }
  <figcaption>Datadog tests for The Storm.</figcaption>
</figure>
