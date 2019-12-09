---
description: >-
  Dashboard app die de Active collective servers watched zo dat we bericht
  krijgen wanner deze offline is.
---

# Dashboard

#### Data ping model

Dit is de data die elke minuut naar de server wordt verstuurd en wordt gelogged in de database en File systems worden opgeslagen.

```javascript
const sendThis = {
            name: listItem.name ? listItem.name : null,
            site_name: process.env.NAME ? process.env.NAME : 'asdad',
            pid: listItem.pid ? listItem.pid : null,
            version: listItem.version ? listItem.version : null,
            created_at: listItem.pm2_env.created_at ? listItem.pm2_env.created_at : null,
            restart_time: listItem.pm2_env.restart_time ? listItem.pm2_env.restart_time : null,
            uptime: listItem.pm2_env.pm_uptime ? listItem.pm2_env.pm_uptime : null,
            memory_use: listItem.monit.memory ? listItem.monit.memory : null,
            cpu_use: listItem.monit.cpu ? listItem.monit.cpu : 0,
            time: moment().format('HH-MM-SS'),
            date: moment().format('DD-MM-YYYY')
      }
```

Wanneer de server een 65 seconden lang geen reactie heeft ontvangen van de server verstuurd de dashboard een message naar slack om de developers op de hoogte te brengen van het probleem.Dit zorgt er voor dat de servers niet al te lang offline zijn en dat de gebruiker er last van heeft.

De error wordt ook opgeslagen op de database zodat we later kunnen terug kijken wanneer we de error hadden en of er een correlatie in zit met de anderen database.

#### Data end-point

Dit is een data endpoint zo kan je dat van de server ophalen met een variable naam, voor nu werkt het alleen nog voor dagen maar wil ook per maand / per jaar maken.

```javascript
async function serveJSON (req, res) {
  fs.readFile(`data/${req.params.name}`, (err, data) => {
    if (err) {
      res.sendStatus(500)
    } else {
      let json = JSON.parse(data)
      res.send(json)
    }
  })
}
```

