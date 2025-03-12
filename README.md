This project requires some manual configuration steps to ensure proper setup and smooth execution:

Postgres Authentication – Configure password authentication for the postgres user using the command line.
Grant Privileges – Assign superuser privileges to the postgres user.
Backup Setup – Create a backup strategy for the Postgres database.
Set credentials.json Path – Ensure the correct path to credentials.json is configured in each GWService class.
Update UI Host – Modify route.js in the UI project to point to the correct server/host.
Firewall Configuration – Check if the backend port (e.g., 8081) is blocked and allow it if necessary.
Update application.properties – Ensure the correct Postgres and MongoDB connection details are set.
