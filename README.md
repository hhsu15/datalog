# DataDog 

Here is the basic concept:

- User connects to Agent
- Where agent runs in your machine (localhost:XXXX)
- There are also different types of agents: 
  - The Log/Infra Agents communicating with your machine overall.
  - The App Agents are communicating with your app. Example can be like Apache Agent (agent that monitors Apache server)

Reference documentation: https://www.devopsschool.com/blog/how-to-enable-live-process-monitoring-in-datadog-age 


## Install Agent 

Go to the DataDog app site, maybe something like:
https://app.dataloghq.com

The go to Integrations -->  Agents --> and just pick your OS. If you are using container then you can create docker agent. There are lot of options here.

Follow the instructions to install your agent on your machine.

To see any configurations about the agentm, you can find the path from the logs when you start the agent. E.g., for linux 

```sh
/etc/datadog-agent/datagog.yaml
```
You can also find the token (which uses to call dataDog API) in this file

You can the start the agent. E.g., linux commend: sudo systemctl resart datalog-agent.


## UI features

- Metrics Explorer:  use this to see the metrics. You can also export it.

- Infrastructure: Here you can see your hosts. 


## Monitor Logs 

You need to tell your agent to collect the logs. For example you have an agent set up to monitor Apache server:

Go to the `/etc/datadog-agent/conf.d/apache.d`

And you will see something like this:
```
# logs:
#   - type: file
#   - path: /var/log/apache2/access.log
#...
#   - type: file
#    - path: /var/log/apache2/error.log
#   - source: apache
#   - service: apache
```

Then, you will need to enable the log agent.

Go to `/etc/datadog-agent/datadog.yaml` and enable the logs:

```
logs_enabled: true 
```
Uncomment them and restart the agent. 

Reference: https://www.devopsschool.com/blog/datadog-tutorials-log-collection-process-configuration/

Agent will then collect these logs.


