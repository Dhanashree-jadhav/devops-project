# DevOps Version Control Project

## Objective
Learn Git for DevOps with branches, pull requests, tags, and scripts.

## Branching Structure
- `main`: Stable code.
- `dev`: Development work.
- `feature/add-logging`: Added logging script.

## How to Use
1. Clone the repo:
   ```bash
   git clone https://github.com/your-username/devops-project.git
   cd devops-project
   </br>

2 Work on a feature branch:
        git checkout -b feature/your-feature dev
        git add .
        git commit -m "Your feature"
        git push -u origin feature/your-feature

3 Submit pull requests to dev on GitHub.
                devops-project/
            ├── scripts/
            │   ├── deploy.sh   # Deployment script
            │   └── logging.sh  # Logging script
            ├── .gitignore      # Ignores junk files
            └── README.md       # This guide

    