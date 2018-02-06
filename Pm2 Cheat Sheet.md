PM2 is a production process manager for Node.js applications with a built-in load balancer.  
It allows you to keep applications alive forever, to reload them without downtime and to facilitate
common system admin tasks.

### Install pm2
npm install pm2@latest -g

### Fork mode
pm2 start app.js --name my-api 
  Name process

### Listing
pm2 list               # Display all processes status

### Logs

1. pm2 logs [--raw]       # Display all processes logs in streaming
2. pm2 flush              # Empty all log files
3. pm2 reloadLogs         # Reload all logs

### Actions

1. pm2 stop all           # Stop all processes
2. pm2 restart all        # Restart all processes

3. pm2 reload all         # Will 0s downtime reload (for NETWORKED apps)

4. pm2 stop 0             # Stop specific process id
5. pm2 restart 0          # Restart specific process id

6. pm2 delete 0           # Will remove process from pm2 list
7. pm2 delete all         # Will remove all processes from pm2 list

