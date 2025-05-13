**up::** [[Linux MOC]]
**index::** [[+Index for Personal]]
 

**tags::** #command_line #Linux #jobs #shutdown

# View Active Jobs (Linux)

**Created:**  22 September 2023 at  15:14 hours.

___
### Note:
When you see the message "There are stopped jobs" upon typing `exit` in your SSH terminal, it means that there are background jobs that have been paused or stopped. You can view and manage these jobs using the `jobs` command and the `fg` and `bg` commands.

Here's how you can work with stopped jobs:

1. To view a list of stopped jobs, simply run the `jobs` command:

   ```bash
   jobs
   ```

   This will display a list of stopped jobs along with their job numbers.

2. To bring a stopped job to the foreground (resume it), use the `fg` command followed by the job number. For example, if you have a job with job number 1 that you want to bring back to the foreground:

   ```bash
   fg %1
   ```

   Replace `1` with the actual job number you want to resume.

3. To send a stopped job to the background, you can use the `bg` command followed by the job number. For example, to send job number 2 to the background:

   ```bash
   bg %2
   ```

   This will allow the job to continue running in the background.

4. If you want to terminate a stopped job, you can use the `kill` command with the appropriate job number. For instance, to terminate job number 3:

   ```bash
   kill %3
   ```

   This will forcefully end the specified job.

After you have managed the stopped jobs using the above commands, you can safely exit the terminal using the `exit` command without encountering the "There are stopped jobs" message.

Remember that job numbers may vary, so be sure to use the correct job number for the job you want to manage.


**See also::** 

### Links to this note:
```query
"[[View Active Jobs (Linux)]]"
```

