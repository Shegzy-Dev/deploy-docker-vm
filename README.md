# 🚀 deploy-docker-vm

A composite GitHub Action to deploy any Dockerized backend to a remote VM over SSH.

## ✅ Inputs
| Name | Description | Required |
|------|-------------|----------|
| host | SSH host | ✅ |
| username | SSH username | ✅ |
| key | SSH private key | ✅ |
| container_name | Docker container name | ✅ |
| image_name | Docker image name | ✅ |
| app_port | Port exposed by app | ✅ |
| env_mongo | MongoDB URI | ✅ |
| env_jwt | JWT secret | ✅ |

## 🔧 Usage

In your project’s workflow (`.github/workflows/deploy.yml`):

```yaml
- name: 🚀 Deploy to VM
  uses: <your-username>/deploy-docker-vm@v1
  with:
    host: ${{ secrets.VM_HOST }}
    username: ${{ secrets.VM_USER }}
    key: ${{ secrets.VM_SSH_KEY }}
    container_name: ${{ vars.CONTAINER_NAME }}
    image_name: ${{ secrets.DOCKERHUB_USERNAME }}/${{ vars.PROJECT_NAME }}:latest
    app_port: ${{ vars.APP_PORT }}
    env_mongo: ${{ secrets.MONGO_URI }}
    env_jwt: ${{ secrets.JWT_SECRET }}
```
⭐ Tip: Tag a release in this repo (v1) so you can use @v1 in other projects.

---

### ✅ **Steps to make it live**

1. Create a new GitHub repo called **deploy-docker-vm**.
2. Add `action.yml` and `README.md`.
3. Commit & push.
4. Go to **Releases** → create a new release with tag `v1`.

Now in any backend project, you can add this to your workflow:
```yaml
- name: Deploy to VM
  uses: <your-username>/deploy-docker-vm@v1
  with:
    host: ${{ secrets.VM_HOST }}
    username: ${{ secrets.VM_USER }}
    key: ${{ secrets.VM_SSH_KEY }}
    container_name: ${{ vars.CONTAINER_NAME }}
    image_name: ${{ secrets.DOCKERHUB_USERNAME }}/${{ vars.PROJECT_NAME }}:latest
    app_port: ${{ vars.APP_PORT }}
    env_mongo: ${{ secrets.MONGO_URI }}
    env_jwt: ${{ secrets.JWT_SECRET }}
