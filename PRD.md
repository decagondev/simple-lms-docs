# Product Requirements Document (PRD)

## simple-lms: A Lightweight Learning Management System

### Overview
simple-lms is a streamlined learning management system designed for small educational firms that need an efficient, user-friendly platform to manage their educational content, students, teachers, and administrative tasks. The system prioritizes simplicity and ease of use while providing essential features for effective course management and student engagement.

### Target Users
1. **Small Educational Firms** - Primary customers who need a lightweight LMS solution
2. **Administrators** - Staff who manage users, courses, and overall system settings
3. **Teachers/Instructors** - Education providers who manage classes, resources, and student progress
4. **Students** - End users who access educational content and participate in courses

### Core User Stories

#### For Administrators
- As an administrator, I want to manage user accounts so that I can control access to the system
- As an administrator, I want to create and manage courses so that I can organize educational content
- As an administrator, I want to assign teachers to courses so that they can provide instruction
- As an administrator, I want to assign students to cohorts so that they receive the appropriate education
- As an administrator, I want to view system analytics so that I can make informed decisions

#### For Teachers
- As a teacher, I want to manage my assigned classes so that I can effectively deliver educational content
- As a teacher, I want to create and organize resources so that students can access learning materials
- As a teacher, I want to view student progress so that I can provide appropriate guidance
- As a teacher, I want to manage cohorts so that I can address group-specific needs
- As a teacher, I want to integrate with calendar tools so that I can schedule and remind students of important events

#### For Students
- As a student, I want to access my assigned courses so that I can learn at my own pace
- As a student, I want to view educational resources so that I can study effectively
- As a student, I want to see my progress so that I can track my learning journey
- As a student, I want to know which cohort I belong to so that I can collaborate with peers
- As a student, I want calendar integration so that I can manage my learning schedule
- As a student, I want AI assistance when I'm stuck so that I can progress without waiting for human help

### Functional Requirements

#### Authentication & Authorization
- Firebase Authentication integration for secure user login and registration
- Role-based access control (Admin, Teacher, Student)
- Password reset and account recovery functionality

#### User Management
- Create, read, update, and delete operations for all user types
- Role assignment and modification
- User profile management

#### Course Management
- Create, read, update, and delete operations for courses
- Assign teachers to courses
- Assign courses to cohorts
- Track course completion and progress

#### Resource Management
- Upload, organize, and manage educational resources
- Support for various content types (documents, links, etc.)
- Organization by course, class, or cohort

#### Class & Cohort Management
- Create and manage classes within courses
- Create and manage cohorts of students
- Assign students to appropriate cohorts
- Schedule classes with calendar integration

#### Dashboard Interfaces
- Administrative dashboard with system-wide controls and analytics
- Teacher dashboard focusing on classes, resources, and student management
- Student dashboard showing enrolled courses, resources, and progress

#### Calendar Integration
- Google Calendar integration for class scheduling
- Event reminders and notifications
- Schedule visibility for all user roles

#### AI Assistant (Post-MVP)
- Contextual assistance based on curriculum content
- RAG (Retrieval Augmented Generation) implementation to leverage existing resources
- Student-focused interface for asking questions and receiving guidance

### Non-Functional Requirements

#### Performance
- Page load times under 2 seconds
- Support for up to 100 concurrent users
- Responsive design for all screen sizes

#### Security
- Secure authentication via Firebase
- Data encryption for sensitive information
- Regular security audits and updates

#### Scalability
- Modular architecture for easy feature additions
- Database design that accommodates growth
- Horizontal scaling capability for backend services

#### Usability
- Intuitive interface requiring minimal training
- Mobile-responsive design
- Accessibility compliance with WCAG 2.1 AA standards

#### Reliability
- 99.9% uptime during business hours
- Automated backups daily
- Disaster recovery plan

### Technical Constraints
- MongoDB for primary data storage
- Express.js for API development
- React with Vite and TypeScript for frontend
- Tailwind 4 for styling
- Render.com for backend hosting
- Netlify for frontend hosting
- Three GitHub repositories (docs, backend, frontend)

### Success Metrics
- User adoption rate (>80% of target users active within first month)
- Task completion rates (>90% of core tasks completed without assistance)
- System uptime (>99.9% during business hours)
- User satisfaction (>4/5 on satisfaction surveys)

### Timeline
- MVP development: 1 week
- Post-MVP features (AI Assistant): TBD based on initial feedback

### Assumptions & Risks
- Assumes users have basic technical literacy
- Risk: Integration challenges with Google Calendar
- Risk: Performance issues with MongoDB at scale
- Risk: User adoption barriers due to existing systems
