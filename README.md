# Mac OS herokuapp_pinger
A script to ping the heroku app dyno and prevent it from sleeping, with the notification for Mac OS for success and failure. This is a forked version of [sharadcodes/herokuapp_pinger](https://github.com/sharadcodes/herokuapp_pinger) that is Mac OS-specific.

## Requirements

* crontab
* curl

## Set Up

### Clone or download the repository

If you choose to download the files, be sure to rename `herokuapp_pinger_master` to `herokuapp_pinger`.

### Follow the steps below for installation

1. Move the repository folder inside the `/Users/${USER}/` directory. This should be your ROOT user directory.

	It will look like:
	```bash
	/Users/${USER}/herokuapp_pinger/
	```
	
2. Navigate to the `/herokuapp_pinger` directory:
	```bash
	cd /Users/${USER}/herokuapp_pinger/
	```

	Open the script `pinger.sh`:
	```bash
	vim pinger.sh
	```
	Replace the DUMMY_USER_NAME on the line 30 with your user name like this: `export HOME=/Users/your_user_name'



3.  Run the following command to give yourself access to execute `pinger.sh` and create folders to store logs.

	```
	chmod +x pinger.sh && mkdir logs && mkdir csv_logs
	```
	
	These two folders will be used to store logs.
	`csv_logs` folder will store logs in the form of CSV files and the `logs` folder will store them with `.log` extension
	
	
4. Add the hosts to the `hosts_list.txt` file inside `herokuapp_pinger/script_data` folder.
    
    **Every host url should be on a new line**
    
    **NOTE: There should be a new empty line after the last host otherwise last entry in the file will not be read**
    
    **ALSO ANY NUMBER OF HOSTS CAN BE SPECIFIED IN THE `hosts_list.txt` file**

4. Setup crontab like this: 
   ```bash
   chrontab -e
   ```
   And add the following line to your `chrontab` editor.
   ```bash
   * * * * * /home/your_user_name/herokuapp_pinger/pinger.sh
   ```
   **You should change the crontab schedule according to your needs as \* \* \* \* \* will run the script every minute**
   
   I ping my Heroku website every 30 minutes.

5. Test the script by running
   ```bash
   ./pinger.sh
   ```
   The script should: create two log files, run with no errors to the console, and display a notification with your hostname as the title and the status as the	 body. 
   
   To turn off notifications, simply remove the `display notifications` (line 47) from `.pinger.sh`. 
 
---

## Your logs will be inside 
```bash
/home/${USER}/herokuapp_pinger/logs/
```
### and
```bash
/home/${USER}/herokuapp_pinger/csv_logs/
```
---

### Submit a pull request if you have any issues or contact me on [Telegram](https://t.me/ndongre).
