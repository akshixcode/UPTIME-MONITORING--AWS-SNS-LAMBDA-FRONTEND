# UPTIME-MONITORING--AWS-SNS-LAMBDA-FRONTEND

Uptime monitoring is the continuous process of checking whether a website, API, or service is available and responsive. It helps ensure reliability, detect outages, and trigger alerts when something goes wrong.

🛠️ Core Components in Your AWS-Based Setup
Here’s how your infrastructure ties together:

1. Lambda Function (Heartbeat Checker)
Purpose: Periodically pings a target URL (e.g., your frontend or backend endpoint).

Logic:
Uses requests or urllib to send HTTP GET.

Checks status code (200 OK = healthy).

Logs response time and errors.

Error Handling:

Catches timeouts, DNS failures, and non-200 responses.

Logs detailed error messages to CloudWatch.

2. SNS (Simple Notification Service)
Purpose: Sends alerts when downtime is detected.

Setup:
Create a topic (e.g., uptime-alerts).

Subscribe email or SMS endpoints.

Integration:

Lambda publishes to SNS on failure.

Include timestamp, error type, and affected URL.

3. CloudWatch
Purpose: Logs and metrics.

Usage:

View Lambda execution logs.

Set alarms based on invocation errors or custom metrics.

4. Frontend Trigger (Optional Man. Frontend Trigger (Optional Manual Check)
Purpose: A button like “Instant Alerts” triggers Lambda manually.

Tech Stack: Next.js + Tailwind CSS.

Integration:

Uses Lambda Function URL or API Gateway.

Displays success/failure message to user




graph TD
A[Scheduled Event or Button Click] --> B[Lambda Function]
B --> C{Is Site Up?}
C -- Yes --> D[Log Success]
C -- No --> E[Publish to SNS]
E --> F[Send Email/SMS Alert]
<img width="1920" height="1080" alt="Screenshot (116)" src="https://github.com/user-attachments/assets/6891af3e-be67-4d7d-8e93-29e0130ea034" />
<img width="1920" height="1080" alt="Screenshot (117)" src="https://github.com/user-attachments/assets/b86488b9-208c-4cb7-896a-fb792ec188b4" />
<img width="1920" height="1080" alt="Screenshot (118)" src="https://github.com/user-attachments/assets/f8fe319b-b009-4f2c-aba5-cf6c12fc1c11" />
.
