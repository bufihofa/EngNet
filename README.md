<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Node.js-18.x%2B-green.svg" alt="Node.js Version" />
  <img src="https://img.shields.io/badge/npm-8.x%2B-blue.svg" alt="NPM Version" />
  <a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
  <a href="https://www.npmjs.com/~nestjscore" target="_blank"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
  <a href="https://discord.gg/G7Qnnhy" target="_blank"><img src="https://img.shields.io/badge/discord-online-brightgreen.svg" alt="Discord"/></a>
  <a href="https://twitter.com/nestframework" target="_blank"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow" alt="Follow us on Twitter"></a>
</p>

# EngNet - Advanced Learning and Social Platform

EngNet is a robust and scalable server-side application built with the [NestJS](https://nestjs.com/) framework. It aims to provide a comprehensive platform for users to learn, share knowledge, and interact within a community. The backend supports features like user authentication, post management, notifications, AI-powered exercise generation.

## ✨ Features

*   **User Authentication & Authorization**: Secure registration, login, email verification, password reset, and role-based access control using JWT.
*   **Post Management**: Create, read, update, and delete posts. Users can like and comment on posts.
*   **Newsfeed**: Personalized newsfeed for users.
*   **User Profiles**: View and edit user profiles, follow/unfollow users.
*   **Favorites**: Users can mark posts as favorites.
*   **Search Functionality**: Search for users and posts.
*   **Notifications**: Real-time notifications for likes, comments, new posts from followed users, etc.
*   **Email Service**: Integrated mailer service for sending verification emails, password reset links, and other notifications.
*   **AI-Powered Content Generation**:
    *   **Exercise Generation**: Automatically creates English learning exercises from post content using Google Gemini.
    *   **Post Analysis:**: Analysis of English-related content in posts using Google Gemini.
*   **API Documentation**: Swagger (OpenAPI) integration for easy API exploration and testing.
*   **Logging**: Middleware for logging requests.

##  Prerequisites

Before you begin, ensure you have the following installed:
*   [Node.js](https://nodejs.org/) (version 18.x or higher recommended)
*   [npm](https://www.npmjs.com/) (version 8.x or higher recommended) or [Yarn](https://yarnpkg.com/)

## 🚀 Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd EngNet
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Environment Configuration

The application uses environment variables for configuration. Create a `.env` file in the root directory of the project. You can copy the example template below:

```env
# Server Configuration
PORT=3000
JWT_SECRET=your_secure_jwt_secret_key
JWT_EXPIRES_IN=3600s

# Database Configuration
DB_HOST=your-db-host
DB_PORT=your-db-port
DB_USERNAME=your-db-username
DB_PASSWORD=your-db-password
DB_NAME=your-db-name

# Mail Configuration
MAIL_HOST=smtp.gmail.com
MAIL_PORT=465
MAIL_USER=your-email@gmail.com
MAIL_PASS=your-app-password

# Cloudinary Configuration
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret

# Google AI API (for Gemini)
GOOGLE_AI_API_KEY=your-google-ai-api-key

```

**Important**:
*   Replace placeholder values with your actual configuration.
*   Ensure `JWT_SECRET` is a strong, unique random string.
*   Configure database credentials according to your setup.
*   Set up your mail server credentials for the mailer service to work.
*   Obtain a `GEMINI_API_KEY` from Google AI Studio for AI features.

## ධ Running the Application

NestJS provides several ways to run the application:

### Development Mode

Starts the application with live reloading on file changes.

```bash
npm run start:dev
```

The application will typically be available at `http://localhost:3000` (or the port specified in your `.env` file).

### Watch Mode

Similar to development mode, recompiles on changes.

```bash
npm run start:watch
```

### Production Mode

Builds the application and starts it in production mode.

```bash
npm run build
npm run start:prod
```

## 📖 API Documentation

This project uses Swagger (OpenAPI) for API documentation. Once the application is running (e.g., in development mode), you can access the Swagger UI by navigating to `/api` in your browser (e.g., `http://localhost:3000/api`).

The Swagger UI provides a detailed list of all available endpoints, their parameters, request/response schemas, and allows you to interactively test the APIs.

## 🏗️ Project Structure

The project follows a standard NestJS monorepo structure:

```
.
├── .env                  # Environment variables (create this file)
├── src/
│   ├── app.controller.ts   # Root controller
│   ├── app.module.ts       # Root module
│   ├── app.service.ts      # Root service
│   ├── main.ts             # Application entry point
│   ├── common/             # Common utilities, decorators, guards, etc.
│   │   ├── decorators/
│   │   ├── filters/
│   │   ├── guards/
│   │   ├── interceptors/
│   │   ├── middleware/
│   │   └── utils/
│   ├── config/             # Configuration setup (validation, loading)
│   │   ├── configuration.ts
│   │   └── validation.schema.ts
│   └── modules/            # Feature modules
│       ├── auth/           # Authentication and User management
│       ├── posts/          # Post management (CRUD, likes, comments)
│       ├── follows/        # Follow/unfollow functionality
│       ├── mailer/         # Email sending service
│       ├── notifications/  # User notifications
│       └── ...             # Other feature modules
├── test/
│   ├── app.e2e-spec.ts     # Main e2e test file
│   └── jest-e2e.json       # Jest configuration for e2e tests
├── tsconfig.build.json   # TypeScript build configuration
├── tsconfig.json         # TypeScript base configuration
├── package.json          # Project dependencies and scripts
└── README.md             # This file
```

## 🧩 Key Modules Overview

*   **`AppModule` ([`src/app.module.ts`](src/app.module.ts))**: The root module of the application, importing all other necessary modules.
*   **`AuthModule` ([`src/modules/auth/auth.module.ts`](src/modules/auth/auth.module.ts))**: Handles user registration, login, JWT authentication, password management, profile management, and AI-driven content generation (exercises, recipes).
*   **`PostsModule` ([`src/modules/posts/posts.module.ts`](src/modules/posts/posts.module.ts))**: Manages creation, retrieval, updating, and deletion of posts, along with likes and comments.
*   **`NotificationsModule` ([`src/modules/notifications/notifications.module.ts`](src/modules/notifications/notifications.module.ts))**: Responsible for generating and managing user notifications for various events.
*   **`MailerModule` ([`src/modules/mailer/mailer.module.ts`](src/modules/mailer/mailer.module.ts))**: Provides services for sending emails (e.g., verification, password reset).
*   **`ConfigModule` ([`src/config/configuration.ts`](src/config/configuration.ts))**: Manages application configuration using NestJS's `ConfigModule`, including validation of environment variables.
*   **`Common` Directory ([`src/common/`](src/common/))**: Contains shared utilities, custom decorators ([`src/common/decorators/roles.decorator.ts`](src/common/decorators/roles.decorator.ts)), exception filters ([`src/common/filters/all-exceptions.filter.ts`](src/common/filters/all-exceptions.filter.ts)), authentication guards ([`src/common/guards/jwt-auth.guard.ts`](src/common/guards/jwt-auth.guard.ts)), interceptors, middleware ([`src/common/middleware/logger.middleware.ts`](src/common/middleware/logger.middleware.ts)), and pipes.

## 🤝 Contributing

Contributions are welcome! If you'd like to contribute to this project, please follow these steps:

1.  **Fork the Repository**: Click the 'Fork' button at the top right of this page.
2.  **Clone Your Fork**: `git clone https://github.com/your-username/EngNet.git`
3.  **Create a New Branch**: `git checkout -b feature/your-feature-name` or `bugfix/issue-number`
4.  **Make Your Changes**: Implement your feature or bug fix.
5.  **Commit Your Changes**: `git commit -m "feat: Add some amazing feature"` (follow [Conventional Commits](https://www.conventionalcommits.org/))
6.  **Push to Your Branch**: `git push origin feature/your-feature-name`
7.  **Open a Pull Request**: Go to the original repository and open a pull request from your forked branch.

Please ensure your code adheres to the project's coding standards (ESLint, Prettier) and all tests pass.

## 🛠️ Built With

*   [NestJS](https://nestjs.com/) - A progressive Node.js framework for building efficient, reliable and scalable server-side applications.
*   [TypeScript](https://www.typescriptlang.org/) - Superset of JavaScript that adds types.
*   [TypeORM](https://typeorm.io/) (or your chosen ORM) - For database interaction.
*   [PostgreSQL](https://www.postgresql.org/) (or your chosen database) - Relational database.
*   [JWT (JSON Web Tokens)](https://jwt.io/) - For authentication.
*   [Swagger (OpenAPI)](https://swagger.io/) - For API documentation.
*   [Google Gemini API](https://ai.google.dev/) - For AI-powered features.
*   [Nodemailer](https://nodemailer.com/) (or similar) - For sending emails.






<a href="https://ibb.co/k65R4nK0"><img src="https://i.ibb.co/jZbcyKhG/01.png" alt="01" border="0"></a>
<a href="https://ibb.co/ymqZHjgY"><img src="https://i.ibb.co/RGcsRwQB/02.png" alt="02" border="0"></a>
<a href="https://ibb.co/1JByBk73"><img src="https://i.ibb.co/wr8G8fBT/03.png" alt="03" border="0"></a>
<a href="https://ibb.co/1fHCwMWn"><img src="https://i.ibb.co/jv7C1zX5/04.png" alt="04" border="0"></a>
<a href="https://ibb.co/ccZ287Yr"><img src="https://i.ibb.co/JRGrpM3s/05.png" alt="05" border="0"></a>
<a href="https://ibb.co/21np3mk7"><img src="https://i.ibb.co/JwBSj0sR/06.png" alt="06" border="0"></a>
<a href="https://ibb.co/Vp091D4F"><img src="https://i.ibb.co/dJsMT6YN/07.png" alt="07" border="0"></a>
<a href="https://ibb.co/B530PWLN"><img src="https://i.ibb.co/q3jTnqB5/08.png" alt="08" border="0"></a>