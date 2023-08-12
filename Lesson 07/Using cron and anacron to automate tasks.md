<strong>Using Cron and Anacron to automate tasks</strong>

Creating bash scripts and other bits of software is very useful in automating the mundane tasks that you may have to perform on a repeated basis. The idea of scripts or other bits of software is to cut down on a lot of the repitive tasks, doing this saves you and your employer time to do other more important tasks.

However, so far I have demonstrated using scripts by interacting with the terminal. Meaning that you have to actually be present. But what if you could do tasks on a schedule without actually being present at the computer. Would that interest you? Good.

The ability to perform tasks without being present is baked into the Linux operating system using two primary methods. The first is called cron and is managed by crontab which is the interface of sorts to manage the cron jobs that you start. The second is called anacron and the anacron service or daemon is something that is setup so that if you turn off your computer a scheduled service or script will still run.

You can access cron in linux by using the crontab command. Crontab is short for Cron Table. This table is lists all of the jobs that you can add to the cron daemon.

The syntax for crontab can be somewhat difficult to understand. It is essentially broken down by minute, hour, day, day of the week, and so on. There are websites that can help you create schedules for cron jobs in case you forget the syntax or can’t be bothered to memorize how it works.

Believe me if you work with cron jobs you will start to master how they can be activated quite easily.

Working with anacron is a bit different.
