---
title: Creating and scheduling systemd services
author: Valentinas Bakaitis
---

**Creating a service**

```bash
#/lib/systemd/system/your_new.service
[Unit]
Description=Your service description
After=network.target 

[Service]
User=root
ExecStart=/path/to/binary/or/script/to/run.sh

[Install]
WantedBy=multi-user.target
```

**Creating a timer**

```bash
#/lib/systemd/system/your_new.timer
[Unit]
Description=Your timer description

[Timer]
OnCalendar=*-*-1 4:00:00
Unit=your_new.service

[Install]
WantedBy=timers.target
```

**Reloading systemctl after modifying service files**
```
systemctl daemon-reload
```

**Testing (or running once) the service**
```
systemctl start your_new.service
```


**Enabling the schedule**

```
systemctl start date.timer
```

References:
1. OnCalendar time format reference: <https://www.freedesktop.org/software/systemd/man/systemd.time.html>
