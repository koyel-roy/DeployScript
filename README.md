1. postgres password authentication through command line (this was done manually)
2. priveles for postgres username with postgres as pasword with supervisor priviledge was also given
manually. 
3. backup for postgres criteria was also done manually. 
4. in each gwservice class we need to also mention the correct credentials.json file for where it is present. 
else will throw an file not found error. 
5.In the ui project we need to go to the route.js file and mention the host or server that we currently are on. (this needs to be done manually).
6. also we have to check if the backend port is blocked by the firewall, if it is then we need to change
the rules and allow the particular port. 
7. to start the backend we currently run this sudo java -jar /opt/DataModelAPI/data-model-api-0.0.1-SNAPSHOT.jar,
fo. 

8. Make sure that in the application.properties file has the updated postgres and mongo connection url, username
and password. Mentioning localhosted databases can also work but the password authentication must be there.
