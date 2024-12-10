# pomodoro-infra-configs
Infra configs for Promodoro Application

## Commands to deploy helm chart

Make sure you are inside helm-chart directory and deploy helm charts in below order.

### Deploy Database

Modify the values.yaml file with your configuration and run the following command. Especially secret username and password

```bash
helm install pomodoro-db db -n db --create-namespace
```

### Deploy Report Backend

Modify the values.yaml file with your configuration and run the following command. Especially the mongourl under configmap template file data. If you change username and password in database, change it here as well.

```bash
helm install pomodoro-report-backend report-backend -n backend --create-namespace
```

### Deploy Backend

Modify the values.yaml file with your configuration and run the following command. Especially the values under configmap template file data.

Even though the frontend is not deployed, you have to give the frontend url. The base url will be your nodeip and nodeport you are going to expose the frontend. Same goes for report backend url.

```bash
helm install pomodoro-backend backend -n backend --create-namespace
```

### Deploy Frontend

Modify the values.yaml file with your configuration and run the following command. Especially the values under configmap template file data.

```bash
helm install pomodoro-frontend frontend -n frontend --create-namespace
```

## Commands to deploy helm chart

If you no longer need the setup, run the following command to delete it.

### Frontend

```bash
helm delete pomodoro-frontend -n frontend
```

### Backend
```bash
helm delete pomodoro-backend -n backend
```

### Report Backend
```bash
helm delete pomodoro-report-backend -n backend
```

### Database
```bash
helm delete pomodoro-db -n db
```