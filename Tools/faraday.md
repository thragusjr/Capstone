# Working with the GUI

You can start working with the GUI by typing Faraday -h in your terminal. This will provide you with credentials for your work space and you can go from there.

- **Navigation**: 
	- The Faraday GUI has a navigation bar on the left side of the screen that you can use to quickly access different parts of the application, such as your workspace, hosts, vulnerabilities, and reports. You can also use the search bar at the top of the screen to search for specific hosts or vulnerabilities.
- **Hosts view**: 
	- The hosts view displays a list of all the hosts in your workspace. You can click on a host to see more information about it, such as its IP address, operating system, and open ports. You can also use the filter and sort options at the top of the screen to narrow down the list of hosts based on certain criteria.
- **Vulnerabilities view**: 
	- The vulnerabilities view displays a list of all the vulnerabilities in your workspace. You can click on a vulnerability to see more information about it, such as its severity, description, and affected hosts. You can also use the filter and sort options at the top of the screen to narrow down the list of vulnerabilities based on certain criteria.
- **Reports view**: 
	- The reports view displays a list of all the reports in your workspace. You can click on a report to see more information about it, such as its title, date, and status. You can also use the filter and sort options at the top of the screen to narrow down the list of reports based on certain criteria.
- **Working with hosts**: 
	- To add a new host to your workspace, click on the "Hosts" tab in the navigation bar and then click on the "Add Host" button. You can then enter the host's IP address, hostname, and other information. To edit an existing host, click on the host in the hosts view and then click on the "Edit" button.
- **Working with vulnerabilities**: 
	- To add a new vulnerability to your workspace, click on the "Vulnerabilities" tab in the navigation bar and then click on the "Add Vulnerability" button. You can then enter the vulnerability's title, description, severity, and other information. To associate a vulnerability with a host, click on the host in the hosts view and then click on the "Add Vulnerability" button.
- **Working with reports**: 
	- To create a new report in Faraday, click on the "Reports" tab in the navigation bar and then click on the "New Report" button. You can then select the type of report you want to create (e.g., PDF, HTML, Markdown) and enter the report's title and description. You can also choose which hosts and vulnerabilities to include in the report.
- **Integrations**: 
	- Faraday supports a number of integrations with other tools, such as Nmap, Metasploit, and Burp Suite. To configure an integration, click on the "Integrations" tab in the navigation bar and then click on the integration you want to configure. You can then enter the necessary configuration details and save the integration. Once an integration is configured, you can use it to import data into Faraday or launch external tools from within Faraday.

# Working with the CLI

- **Start Faraday in CLI**
	- faraday-cli
- **Authentication Info**
	- faraday-cli auth
- **Other Useful Faraday Commands**
	- -f/--faraday-url FARADAY_URL	url of your faraday server
	- -i/--ignore-ssl	Ignore SSL certificate validation
	- -i/--ignore-ssl	Ignore SSL certificate validation
	- -u/--user USER	Faraday user
	- -p/--password PASSWORD	Faraday password
- **List Current Workplace(s)**
	- faraday-cli workspace list -p
- **Delete a workspace**
	- faraday-cli workspace delete test
- **Import Report From Tool**
	- faraday-cli tool report $HOME/Downloads/openvas-report.xml

## **Resources:**
https://docs.faraday-cli.faradaysec.com/
https://github.com/infobyte/faraday_plugins
[Importing - Faraday](https://docs.faradaysec.com/import/)
