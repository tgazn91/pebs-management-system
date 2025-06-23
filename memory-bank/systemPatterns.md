# System Patterns: PeBS Management System

## Architecture Overview

### System Architecture
```mermaid
graph TD
    A[Client Browser] --> B[Laravel Application]
    B --> C[Blade Templates]
    B --> D[MySQL Database]
    B --> E[File Storage]
    
    subgraph Backend
        B --> F[Authentication]
        B --> G[RBAC]
        B --> H[Business Logic]
    end
    
    subgraph Frontend
        C --> I[Tailwind CSS]
        C --> J[Alpine.js]
    end
```

## Design Patterns

### 1. MVC Architecture
```mermaid
graph LR
    A[Routes] --> B[Controllers]
    B --> C[Models]
    B --> D[Views]
    C --> E[(Database)]
```

### 2. Repository Pattern
- Separation of database logic
- Clean controller implementation
- Reusable data access layer

### 3. Service Layer Pattern
- Business logic encapsulation
- Reusable service classes
- Clean controller code

### 4. Form Request Pattern
- Validation logic separation
- Clean controller methods
- Reusable validation rules

## Database Design

### Core Tables Structure
```mermaid
erDiagram
    Users ||--o{ UserRoles : has
    Users ||--o{ Programs : registers
    Programs ||--o{ Resources : contains
    Programs ||--o{ Attendance : tracks
    
    Users {
        id int PK
        name string
        email string
        password string
        remember_token string
        created_at timestamp
        updated_at timestamp
    }

    Roles {
        id int PK
        name string
        description string
    }

    UserRoles {
        user_id int FK
        role_id int FK
    }

    Programs {
        id int PK
        title string
        description text
        date datetime
        capacity int
        status string
    }

    Resources {
        id int PK
        program_id int FK
        title string
        type string
        file_path string
    }

    Attendance {
        id int PK
        program_id int FK
        user_id int FK
        status string
        attended_at timestamp
    }
```

## Authentication Flow

### User Authentication
```mermaid
sequenceDiagram
    participant U as User
    participant A as Auth System
    participant D as Database
    
    U->>A: Login Request
    A->>D: Verify Credentials
    D-->>A: User Data
    A->>A: Create Session
    A-->>U: Auth Response
```

### Role-Based Access
```mermaid
graph TD
    A[Request] --> B{Auth Check}
    B -->|Yes| C{Role Check}
    B -->|No| D[Login Page]
    C -->|Admin| E[Admin Dashboard]
    C -->|Member| F[Member Dashboard]
    C -->|Viewer| G[Public Pages]
```

## File Structure

```
src/
├── app/
│   ├── Http/
│   │   ├── Controllers/
│   │   ├── Middleware/
│   │   └── Requests/
│   ├── Models/
│   ├── Services/
│   └── Repositories/
├── resources/
│   ├── views/
│   │   ├── layouts/
│   │   ├── components/
│   │   ├── admin/
│   │   └── member/
│   ├── lang/
│   │   └── ms/
│   └── css/
└── routes/
    ├── web.php
    └── api.php
```

## Key Technical Decisions

### 1. Authentication
- Using Laravel Breeze for:
  - Simple authentication scaffolding
  - Basic UI components
  - Easy customization

### 2. Frontend
- Blade templating:
  - Server-side rendering
  - Simple syntax
  - Easy integration with PHP
- Tailwind CSS:
  - Utility-first approach
  - Easy customization
  - Responsive design

### 3. Database
- MySQL:
  - Robust and reliable
  - Good Laravel integration
  - Easy to manage

### 4. Language Implementation
- Using Laravel's localization:
  - Language files in resources/lang/ms/
  - Easy switching capability
  - Maintainable translations

## Security Patterns

### 1. Input Validation
- Form request validation
- Sanitization middleware
- Type checking

### 2. Output Security
- XSS protection
- CSRF tokens
- Secure headers

### 3. File Handling
- Mime type validation
- Size restrictions
- Secure storage

### 4. Database Security
- Prepared statements
- Migration rollbacks
- Backup strategies

## Performance Patterns

### 1. Caching Strategy
- View caching
- Query caching
- Configuration caching

### 2. Query Optimization
- Eager loading
- Chunked operations
- Indexed queries

### 3. Asset Management
- Asset compilation
- Cache busting
- CDN integration (future)
