# PeBS MBSA Zon 20 Website – Developer Specification Document

## 1. Objective of the Website

To build a centralized, interactive web platform for PeBS Zon 20 under MBSA that:

- Serves as the official information hub
- Facilitates registration and data collection for youth
- Disseminates activity announcements and resources
- Displays the organizational structure and key personnel
- Provides admin and member dashboards for efficient program management

## 2. Technical Stack Requirement

The website must be developed using:

- **Backend**: PHP (latest stable version)
- **Framework**: Laravel (preferred for its security, structure & scalability)
- **Database**: MySQL / MariaDB
- **Frontend**: Blade templating (with Bootstrap or Tailwind CSS), or Vue.js if SPA is preferred
- **Authentication**: Laravel Breeze/Fortify/Jetstream (based on complexity needed)
- **Hosting Recommendation**: Shared VPS or cloud hosting with PHP support (e.g., Cloudways, ServerFreak, Exabytes)

## 3. Core Modules & Features

### A. Public Pages
- Homepage with intro and latest news
- About Us (Vision, Mission, Organizational Chart with photos & roles)
- List of Programs & Announcements
- Online Member Registration
- Contact Page with embedded form
- Downloads (Forms, Reports, Guides)
- Gallery (Photos/Videos)

### B. Admin Dashboard
Accessible by PeBS Zon 20 committee/admins:
- View and export participant data (filterable)
- Add/edit/delete programs & announcements
- Upload resources & gallery content
- Generate attendance/participation reports
- View system notifications (e.g. pending reports)
- Manage admin/user roles

### C. Member Dashboard
Accessible by registered youth:
- Update personal profile
- View upcoming programs
- Register/RSVP for events
- Download participation certificates (if applicable)
- View past attendance records
- Access shared documents/resources

## 4. Security & Access
- Laravel authentication with roles: admin, member, viewer
- CSRF protection and form validation
- CAPTCHA for form spam prevention
- Role-based access control (RBAC)
- SSL (HTTPS) enabled

## 5. Usability & UX
- Fully mobile-responsive (Bootstrap or Tailwind CSS)
- Malay as primary language (English optional)
- Admin and Member interfaces clearly separated
- Fast loading, intuitive UI
- Simple and clean dashboard experience

## 6. Maintenance & Support Expectations
- Weekly auto-backup setup
- Ability to update Laravel packages securely
- Developer should provide handover documents (readme/manual)
- 1 month post-launch support for bug fixes

## 7. Suggested Menu Structure
- Home
- About Us
  - Vision & Mission
  - Organizational Chart
- Programs & Activities
- Youth Registration
- Gallery
- Downloads
- Contact
- Member Login
- Admin Login

## Client Deliverables
To start the project, you should prepare:

- PeBS official logo and colour codes
- Organizational structure and committee bios
- Sample photos for gallery and homepage
- Forms and PDFs to upload
- Initial list of programs (if any)
- Hosting access or domain info (if available)
