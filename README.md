# EmailMarketing Infrastructure

Email Marketing SaaS — Infrastructure

This repository contains the Docker Compose setup and deployment guide for the Email Marketing SaaS.

🌐 Architecture Overview

      [ Cloudflare DNS ]
             |
             v
      [ AWS EC2 Public IP ]
             |
       docker-compose
           / | \
           / | \
           v v v
   [frontend] [backend] [mongoDB]

🛠 Tech Stack

Docker

Docker Compose

AWS EC2

Cloudflare for DNS

Clerk for Auth

## Setup

1. Clone all repos:

   - Frontend: https://github.com/aayushkakkar26/email-marketing-frontend.git
   - Backend: https://github.com/aayushkakkar26/email-marketing-backend.git
   - Infra: https://github.com/aayushkakkar26/email-marketing-infra.git

2. Place the frontend and backend folders at the same level as this infra repo, or update `docker-compose.yml` paths.

/infra
├── docker-compose.yml
/frontend
├── Dockerfile
/backend
├── Dockerfile

docket-compose.yml

version: "3.8"

services:
frontend:
build:
context: ./frontend
dockerfile: Dockerfile
ports: - "3001:3001"
env_file: - ./frontend/.env.local
depends_on: - backend
restart: unless-stopped

backend:
build:
context: ./backend
dockerfile: Dockerfile
ports: - "3000:3000"
env_file: - ./backend/.env
depends_on: - mongo
restart: unless-stopped

mongo:
image: mongo:6
ports: - "27017:27017"
volumes: - mongo_data:/data/db

volumes:
mongo_data:

3. Copy `.env.example` to `.env` in both frontend and backend folders and fill in values.

4. Run:
   cd infra
   docker-compose up --build

---

**Summary:**

- Each repo contains only its relevant code.
- Infra repo contains orchestration and deployment files.
- Document clearly in each README how to use the repos together.
