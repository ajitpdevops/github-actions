# Resource 
- https://github.com/jmstechhome8/web_login_automation

# Docker Login with CLI 
- aws ecr get-login-password --region us-east-2 | docker login --username AWS --password-stdin 243302161856.dkr.ecr.us-east-2.amazonaws.com

# Create a repository
- aws ecr create-repository \
    --repository-name nodeapp \
    --image-scanning-configuration scanOnPush=true \
    --region us-east-2

# Push an image to Amazon ECR
- docker tag cwaapp:latest 243302161856.dkr.ecr.us-east-2.amazonaws.com/nodeapp
- docker push 243302161856.dkr.ecr.us-east-2.amazonaws.com/nodeapp
- docker pull 243302161856.dkr.ecr.us-east-2.amazonaws.com/nodeapp:latest


# Delete an image 
- aws ecr batch-delete-image \
      --repository-name nodeapp \
      --image-ids imageTag=latest \
      --region us-east-2

# Delete a repository
- aws ecr delete-repository \
      --repository-name nodeapp \
      --force \
      --region us-east-2      