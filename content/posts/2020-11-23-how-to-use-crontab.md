---
title: "How to Use Crontab"
date: 2020-11-23T00:52:42+08:00
draft: false
tags: [linux]
---
1. Cron is a tool to configure scheduled tasks in Unix/Linux system. It is like Task Scheduler in Windows system.  
2. `crontab` is a command to edit all the scheduled tasks in the machine.  

## Cron Table Format

```
*    *    *   *    *  Command_to_execute
|    |    |    |   |       
|    |    |    |    Day of the Week ( 0 - 6 ) ( Sunday = 0 )
|    |    |    |
|    |    |    Month ( 1 - 12 )
|    |    |
|    |    Day of Month ( 1 - 31 )
|    |
|    Hour ( 0 - 23 )
|
Min ( 0 - 59 )
```

Specifying multiple values in a field

- The asterisk (*) operator specifies all possible values for a field. e.g. every hour or every day.
- The comma (,) operator specifies a list of values, for example: "1,3,4,7,8".
- The dash (-) operator specifies a range of values, for example: "1-6", which is equivalent to "1,2,3,4,5,6".
- The slash (/) operator, can be used to skip a given number of values. For example, "*/3" in the hour time field is equivalent to "0,3,6,9,12,15,18,21"; "*" specifies 'every hour' but the "/3" means that only the first, fourth, seventh...and such values given by "*" are used.

## Editing the crontab

In order to edit the table, proceed to run `crontab` with the flag `-e`:

```bash

 crontab -e

```

📌 If you run the command for the first time, the tool will ask to select a default editor. In the example above, I have selected nano as my editor

## Listing Scheduled Tasks

To view all the tasks listed in the `crontab`, use the command with `-l` flag:

```bash

 crontab -l

```

## Resource(s)

- [Crontab.guru](https://crontab.guru/)
- [Raspberrypi.org - Scheduling tasks with Cron](https://www.raspberrypi.org/documentation/linux/usage/cron.md)
- [Tutorialspoint.com - crontab - Unix, Linux Command](https://www.tutorialspoint.com/unix_commands/crontab.htm)

