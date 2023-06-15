# Backups

The server uses [borg](https://github.com/borgbackup/borg), [borgmatic](https://torsion.org/borgmatic/), and [BorgBase](https://www.borgbase.com/) to backup its data. Backups are taken every hour.

Alerts are setup to ensure that missing backups are detected. Backups are discarded periodically. We keep:

- One backup for each day in the last three days
- One backup for each week in the last four weeks
- One backup for each month in the last twelve months
- One backup for each year in the last two years

<figure markdown>
  ![Screenshot of borgbase UI](/assets/images/borgbase.png){ width="600" }
  <figcaption>The Storm's first backup at borgbase. This is how everyone's hard work is kept safe!</figcaption>
</figure>

## Restoration

We need to test our backups and ensure they are usable. It'd be nice to do this in an automated manner.

## Distribution

Backups are not publically distributed. They may be in the future provided that there is an easy way to scrub sensitive data such as credentials and personally identifiable information (PII) such as IP addresses.
