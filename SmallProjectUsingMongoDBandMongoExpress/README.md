# Kubernetes MongoDB and Mongo Express Deployment

This project demonstrates a simple setup in Kubernetes with two deployments, one for MongoDB and one for Mongo Express. Additionally, it includes an internal service for MongoDB communication and an external service for accessing Mongo Express from a web browser. The MongoDB credentials are stored in a secret file in base64 encoding.

## Deployments

### MongoDB Deployment

- Deployment Name: `mongodb-deployment`
- Purpose: Store and manage data for the application.
- Internal Service Name: `mongodb-service`

### Mongo Express Deployment

- Deployment Name: `mongo-express`
- Purpose: Provide a web-based interface for interacting with MongoDB.
- External Service Name: `mongo-express-service`

## Services

### Internal Service (MongoDB)

The internal service allows communication within the Kubernetes cluster.

- Service Name: `mongodb-service`
- Target Port: `27017`
- Deployment Connection: `mongodb-deployment`

### External Service (Mongo Express)

The external service allows users to interact with Mongo Express from their web browsers.

- Service Name: `mongo-express-service`
- Target Port: `8081`
- Deployment Connection: `mongo-express`

## Secrets

Credentials for MongoDB are stored in a secret file in base64 encoding.

- Secret File Name: `mongodb-secret.yaml`
- Content:

  ```yaml
  apiVersion: v1
  kind: Secret
  metadata:
    name: mongodb-secret
  type: Opaque
  data:
    username: <base64-encoded-username>
    password: <base64-encoded-password>
