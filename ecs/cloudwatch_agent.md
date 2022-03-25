```json
{
    "agent": {
        "metrics_collection_interval": 60,
        "run_as_user": "root"
    },
    "logs": {
        "logs_collected": {
            "files": {
                "collect_list": [
                    {
                        "file_path": "/var/log/ecs/ecs-agent.log",
                        "log_group_name": "flask-shareholder-report-ecs-agent-log",
                        "log_stream_name": "{instance_id}"
                    },
                    {
                        "file_path": "/var/log/ecs/ecs-agent-2.log",
                        "log_group_name": "flask-shareholder-report-ecs-agent-log",
                        "log_stream_name": "{instance_id}"
                    }
                ]
            }
        }
    }
}
```

* `file_path`
  * specify the file to be logged
  * here the file is the `ecs-agent` in order to figure out why the agent is failing on new deployments from the CD pipeline with GitHub Actions
* `log_group_name` - will be created automatically in `CloudWatch` if not already present
* can specify multiple files to log as shown above with `ecs-agent-2.log` which doesn't actually exist
  * delete this section if wanting to use in production
