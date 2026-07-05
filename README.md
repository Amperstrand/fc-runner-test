# fc-runner-test

E2E test target for the SHC Firecracker pool runner autoscaler.

Trigger via:
```
gh workflow run shc-pool-test.yml \
  -R Amperstrand/fc-runner-test \
  -f runner_label=fc-test-$(date +%s)
```

The webhook autoscaler on the SHC host VM will see the `workflow_job` event
with the matching label, spawn a μVM, register a runner with that label,
the job will run on that μVM, and the μVM will be killed when the job
finishes (ephemeral runner).
