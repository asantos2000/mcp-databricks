# Databricks Jobs Management

**IMMEDIATE ACTION REQUIRED:** Start an interactive Databricks jobs management workflow right now.

## Step 1: Authentication Check

**You must execute this exact command immediately to verify authentication:**

```bash
databricks current-user me
```

**What this does:**
- Loads environment variables from `.env.local`
- Exports Databricks host and token to environment
- Checks if you're currently authenticated with Databricks
- Shows your current user information

**If the command fails with authentication errors, ask the user:**
"You need to authenticate with Databricks. Would you like me to run `databricks auth login` to log you in?"

**Only proceed to login if the user confirms:**

```bash
databricks auth login --host $DATABRICKS_HOST
```

## Step 2: List Jobs in Workspace

**Once authenticated, execute this command to list all jobs:**

```bash
databricks jobs list --expand-tasks --output json
```

**What this command does:**
- Lists all jobs in the Databricks workspace
- `--expand-tasks` includes detailed task and cluster information
- `--output json` provides structured data for analysis
- Shows job IDs, names, creators, schedules, and task details

## Step 3: Interactive Job Analysis

**After listing jobs, provide an interactive menu with these options:**

1. **View job details** - Ask user to select a job ID, then run:
   ```bash
   databricks jobs get --job-id [JOB_ID] --output json
   ```

2. **View job runs** - Ask user to select a job ID, then run:
   ```bash
   databricks jobs list-runs --job-id [JOB_ID] --output json
   ```

3. **Get recent run output** - Ask user to select a job ID and run ID, then run:
   ```bash
   databricks jobs get-run-output --run-id [RUN_ID] --output json
   ```

4. **Trigger job run** - Ask user to select a job ID, then run:
   ```bash
   databricks jobs run-now --job-id [JOB_ID]
   ```

5. **Cancel job run** - Ask user to select a run ID, then run:
   ```bash
   databricks jobs cancel-run --run-id [RUN_ID]
   ```

6. **Search jobs by name** - Ask user for job name pattern, then run:
   ```bash
   databricks jobs list --name "[NAME_PATTERN]" --expand-tasks --output json
   ```

## Step 4: Provide Job Insights

**After each command, analyze the results and provide:**
- Job status summary (running, succeeded, failed, pending)
- Cluster configurations and resource usage
- Schedule information and next run times
- Recent run history and success rates
- Task dependencies and workflow structure
- Error analysis for failed runs

## Interactive Questions to Ask Users

**Based on the job data, ask relevant questions like:**
- "Which job would you like to investigate further?"
- "Would you like to see the recent run history for job '[JOB_NAME]'?"
- "Should I trigger a new run of this job?"
- "Would you like to see the output from the failed run?"
- "Do you want to check the cluster configuration for this job?"
- "Should I cancel the currently running job?"

## Error Handling

**If any commands fail:**
- Show the exact error message
- Suggest troubleshooting steps (authentication, permissions, job existence)
- Offer to retry with different parameters
- Provide links to Databricks documentation when relevant

**Execute the authentication check command now using the Bash tool and begin the interactive jobs management workflow.**