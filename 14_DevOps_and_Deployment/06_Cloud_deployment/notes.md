# Cloud Deployment

## Explanation

Deploying to cloud platforms lets you scale and manage infrastructure more easily. Common services include AWS (EC2, Elastic Beanstalk, ECS), Heroku, and DigitalOcean.

Key considerations:
- Containerization vs. platform-specific packaging.
- Environment configuration and secrets management.
- Scaling and load balancing.
- Cost monitoring and optimization.

## Examples

### Heroku deployment steps
1. `heroku create`
2. Add `Procfile` with `web: gunicorn myproject.wsgi`.
3. `git push heroku main` to deploy.
4. Configure environment variables with `heroku config:set`.

### AWS Elastic Beanstalk with Docker
```bash
# create Dockerfile and Dockerrun.aws.json
eb init -p docker my-app
eb create my-app-env
eb open
```

## Tasks

### Beginner
1. Deploy a simple Python app to Heroku following their quickstart.
2. Explore the dashboard and view logs in the cloud provider’s console.

### Intermediate
1. Deploy using Docker containers to AWS ECS or DigitalOcean App Platform.
2. Configure auto-scaling rules and test by generating load.

### Advanced
1. Use infrastructure-as-code (CloudFormation, Terraform) to provision environments.
2. Set up CI/CD pipelines that deploy to cloud environments after passing tests.

## Quick Review
- What is a `Procfile` used for on Heroku?
- How does containerization simplify cloud deployments?

---