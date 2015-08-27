# html-bandwith-report
HTML/JS to make graphic bandwith reports made with my modified version of Speedtest-cli. You can show upload, dowload speed and latency combined or separatedly. Also displays averages.

# Usage
1. Install my modified version of https://github.com/gonzalo/speedtest-cli
2. Install a webserver (apache, nginx...) no need of php or any special module
3. Add bandwith.html and bandwith_report_sample.csv somewhere in the webserver folder. Point with your navigator to the bandwith.html file and test that works correctly. You shoud see something like this
![alt tag](https://cloud.githubusercontent.com/assets/57393/8900874/3320bc86-3444-11e5-9612-4ef2dbb0716b.png)
4. Add a cronjob to execute speedtest-cli and store results in the same folder of bandwith.html. Be sure that user that executes the script has write access to that folder, also check script location and the name that you want for the csv file. Next example executes the test every hour.
```
$crontab -e
0 */1 * * * /root/git/speedtest-cli/speedtest_cli.py --csv /var/www/bandwith_report.csv
```
5. Finally modify bandwith.html to point to your new csv file. Find this line:
```
req.open('GET', 'bandwith_report_sample.csv', true);
```
...and adjust it to your needs.

