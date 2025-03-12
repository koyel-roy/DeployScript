## 📝 **Project Setup Summary**  

This project requires some manual configuration steps to ensure proper setup and smooth execution:  

1. **Postgres Authentication**  
   - Configure password authentication for the `postgres` user using the command line.  

2. **Grant Privileges**  
   - Assign `superuser` privileges to the `postgres` user.  

3. **Backup Setup**  
   - Create a backup strategy for the Postgres database.  

4. **Set `credentials.json` Path**  
   - Ensure the correct path to `credentials.json` is configured in each `GWService` class.  

5. **Update UI Host**  
   - Modify `route.js` in the UI project to point to the correct server/host.  

6. **Firewall Configuration**  
   - Check if the backend port (e.g., `8081`) is blocked and allow it if necessary.  

7. **Update `application.properties`**  
   - Ensure the correct Postgres and MongoDB connection details are set.  


