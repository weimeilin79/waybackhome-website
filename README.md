# Workshop Landing Page

A static HTML/CSS landing page for the workshop, served via Nginx.

## Run Locally
```bash
python3 -m http.server 8000
```
Access at: http://localhost:8000

## Docker Build & Run (Local)
```bash
# Build
docker build -t landingpage .

# Run
docker run -p 8080:80 landingpage
```
Verify: Access http://localhost:8080 to confirm container works.

## Deploy to Google Cloud Run

### 1. Build and Push to Container Registry
Replace `${PROJECT_ID}` with your GCP Project ID.

```bash
docker build -t gcr.io/${PROJECT_ID}/waybackhome-website .
docker push gcr.io/${PROJECT_ID}/waybackhome-website
```

### 2. Deploy to Cloud Run
```bash
gcloud run deploy waybackhome-website \
  --image=gcr.io/${PROJECT_ID}/waybackhome-website:latest \
  --region=us-central1 \
  --platform=managed \
  --allow-unauthenticated
```
