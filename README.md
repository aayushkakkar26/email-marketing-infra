# EmailMarketing Infrastructure

## Setup

1. Clone all repos:
   - Frontend: https://github.com/aayushkakkar26/email-marketing-frontend.git
   - Backend: https://github.com/aayushkakkar26/email-marketing-backend.git
   - Infra: https://github.com/aayushkakkar26/email-marketing-infra.git

2. Place the frontend and backend folders at the same level as this infra repo, or update `docker-compose.yml` paths.

3. Copy `.env.example` to `.env` in both frontend and backend folders and fill in values.

4. Run:
   ```sh
   docker compose up --build


---

**Summary:**  
- Each repo contains only its relevant code.
- Infra repo contains orchestration and deployment files.
- Document clearly in each README how to use the repos together.

