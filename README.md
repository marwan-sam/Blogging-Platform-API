
### Structure Project :
|
BloggingPlatform/
├── src/
│   ├── BloggingPlatform.API/             # API Gateway
│   │   ├── Controllers/
│   │   ├── Middleware/
│   │   └── Program.cs
│   ├── BloggingPlatform.Auth/            # Authentication Service
│   │   ├── Services/
│   │   └── Models/
│   ├── BloggingPlatform.BlogPost/        # Blog Post Service
│   │   ├── Services/
│   │   └── Models/
│   ├── BloggingPlatform.Comment/         # Comment Service
│   │   ├── Services/
│   │   └── Models/
│   ├── BloggingPlatform.Notification/    # Notification Service
│   │   ├── Services/
│   │   └── Models/
│   ├── BloggingPlatform.Search/          # Search Service
│   │   ├── Services/
│   │   └── Models/
│   ├── BloggingPlatform.Share/           # Social Sharing Service
│   │   ├── Services/
│   │   └── Models/
│   └── BloggingPlatform.Common/          # Shared Code
│       ├── Models/
│       └── Infrastructure/
├── tests/
│   ├── BloggingPlatform.API.Tests/
│   ├── BloggingPlatform.Auth.Tests/
│   └── BloggingPlatform.Services.Tests/
├── docker/
│   ├── docker-compose.yml
│   ├── docker-compose.override.yml
│   └── Dockerfile
└── BloggingPlatform.sln



### Diagram:

+-------------------------------+                     +----------------------------------+
|           API Gateway         |                     | Notification Service (Twilio/   |
+-------------------------------+                     | SendGrid)                       |
              |                                     / +----------------------------------+
              v                                    /
+-------------------------------+                 /
| Authentication Service (JWT)  | <--------------/
+-------------------------------+               /
              |                                 /
              v                                /
+-------------------------------+             /
|          User Service         | <----------/
+-------------------------------+           /
              |                             /
              v                            /
+-------------------------------+         /     +-----------------------------------+
|       Blog Post Service       | <------/------| Search Service (Algolia/         |
+-------------------------------+       /       | Elasticsearch)                   |
              |                         /       +-----------------------------------+
              v                        /
+-------------------------------+     /
|       Comment Service         | <--/
+-------------------------------+
              |
              v
+-------------------------------+
| Database (SQL Server/SQLite)  |
+-------------------------------+
              ^
              |
              |
              |
  +----------------------------------+
  |       Social Sharing Service     |
  +----------------------------------+
