# simple-lms

A lightweight Learning Management System designed for small educational firms.

## Overview

simple-lms is a streamlined, user-friendly learning management system that prioritizes simplicity and efficiency. Built with small educational firms in mind, it provides essential features for managing courses, students, resources, and administrative tasks without the complexity and overhead of enterprise solutions.

## Project Repositories

This project is organized across three GitHub repositories:

1. **[simple-lms-docs](https://github.com/your-org/simple-lms-docs)** - Project documentation and planning materials
2. **[simple-lms-be](https://github.com/your-org/simple-lms-be)** - Backend API built with Express.js and MongoDB
3. **[simple-lms-fe](https://github.com/your-org/simple-lms-fe)** - Frontend application built with React, Vite, and TypeScript

## Key Features

- **User Management** - Create and manage administrators, teachers, and students
- **Course Management** - Organize educational content and resources
- **Resource Management** - Upload and organize learning materials
- **Class & Cohort Management** - Group students and schedule classes
- **Role-Based Dashboards** - Tailored interfaces for administrators, teachers, and students
- **Google Calendar Integration** - Synchronize class schedules with Google Calendar
- **Firebase Authentication** - Secure, scalable user authentication
- **Responsive Design** - Accessible on desktop and mobile devices

## Getting Started

For detailed information about each component of the project, please refer to the following documents:

- [Product Requirements Document](./PRD.md) - Detailed product requirements and specifications
- [Architecture Overview](./ARCHITECTURE.md) - System architecture and technical design
- [Elevator Pitch](./ELEVATOR-PITCH.md) - Concise project summary
- [Executive Summary](./EXECUTIVE-SUMMARY.md) - Business-focused project overview
- [Technical Summary](./TECHNICAL-SUMMARY.md) - Technical overview for engineering stakeholders
- [Market Research](./MARKET-RESEARCH.md) - Analysis of the LMS market and opportunities
- [Project Plan](./PLAN.md) - Implementation plan and timeline
- [Task List](./TASKS.md) - Detailed breakdown of project tasks

## Technology Stack

### Frontend
- React with Vite
- TypeScript
- Tailwind CSS 4
- React Router
- Firebase Authentication
- Hosted on Netlify

### Backend
- Express.js
- TypeScript
- MongoDB with Mongoose
- Firebase Admin SDK
- Hosted on Render.com

### External Integrations
- Firebase Authentication
- Google Calendar API
- MongoDB Atlas

## Development Timeline

simple-lms is designed for rapid implementation with a development timeline of just one week for the initial MVP, followed by ongoing enhancements.

### Phase 1: MVP (1 Week)
- User, course, and resource management
- Role-based dashboards
- Essential features for educational content delivery

### Phase 2: Enhancements (Post-MVP)
- AI assistant for student support
- Advanced analytics and reporting
- Additional integrations and features

## Repository Structure

### simple-lms-docs
```
simple-lms-docs/
├── README.md
├── PRD.md
├── ARCHITECTURE.md
├── ELEVATOR-PITCH.md
├── EXECUTIVE-SUMMARY.md
├── TECHNICAL-SUMMARY.md
├── MARKET-RESEARCH.md
├── PLAN.md
└── TASKS.md
```

### simple-lms-be
```
simple-lms-be/
├── README.md
├── src/
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── services/
│   ├── utils/
│   └── index.ts
├── tests/
├── package.json
└── tsconfig.json
```

### simple-lms-fe
```
simple-lms-fe/
├── README.md
├── src/
│   ├── assets/
│   ├── components/
│   ├── contexts/
│   ├── hooks/
│   ├── pages/
│   ├── services/
│   ├── utils/
│   ├── App.tsx
│   └── main.tsx
├── index.html
├── vite.config.ts
├── package.json
└── tsconfig.json
```

## Contributing

For developers interested in contributing to the project, please see the individual repository README files for specific setup and contribution guidelines.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For questions or support, please open an issue in the appropriate repository or contact the project maintainers.

---

simple-lms is designed and built to make learning management simple and accessible for small educational firms. We believe that education technology should empower educators, not burden them with complexity.
