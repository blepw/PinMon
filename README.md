# PinMon


A self-hosted Pinterest monitoring bot that watches a Pinterest profile's RSS feed and automatically forwards new pins to a Telegram channel — with adaptive polling, image caching, dual-layer deduplication, and a scraper-based safety net to catch anything the RSS feed misses.


<img width="983" height="692" alt="Screenshot From 2026-11-08 11-16-05" src="https://github.com/user-attachments/assets/e9b95018-42bd-486c-aede-66262c5b1ae3" />



# Configuration 



```ini
[pinterest]
username = <pinterest username to monitor>

[telegram]
channel  = @your_channel
token    = <token_here>

[timing]
count_poll       = 3600
send_delay       = 3
fail_alert_at    = 3
min_interval     = 600
max_interval     = 7200
initial_interval = 1800

[paths]
db  = data/pins.db
log = logs/monitor.log

[logging]
file_level    = INFO
console_level = INFO
```


# Running

```bash
python main.py
```


On startup you'll be asked:

1. **Use username from config?** — `y` to use `config.ini`, `n` to type one in.
2. **Enable streamer mode?** — `y` to mask the username as `@****` in all output.



# Telegram commands 

| Command   | Description                                               |
|-----------|-----------------------------------------------------------|
| `/status` | Live stats: interval, fail streak, pins, board sync state |
| `/resync` | Force an immediate board-count check and queue gaps       |
---



<img width="843" height="359" alt="Screenshot From 2026-11-08 11-30-18" src="https://github.com/user-attachments/assets/20d2e6da-bd20-4cf9-9023-bbddf6232670" />



## Project Structure 

```
phs/
├── main.py             
├── tiny_db.py          # lightweight key-value store
├── config.ini          # configuration
├── data/               # pin database
├── logs/               # rotating log files
└── media/              # cached pin images
```

### No warranty - Private source code 




