# Implemented Features Documentation

## Project Overview
This document outlines the features and functionalities implemented in the Shopping Cart application as of version `v1`.

## 1. User Management (Admin Panel)
- **User Listing**: Displays a tabular list of all registered users.
    - **Columns**: # (Serial Number), Checkbox, Username (with Avatar), Email, Status, Role, Admin Access, Joined Date, Actions.
- **Visual Enhancements**:
    - **Colorful Badges**: Distinct visual indicators for:
        - **Status**: Verified (Green) / Pending (Orange)
        - **Role**: Admin (Purple) / User (Blue)
        - **Admin Access**: Yes (Green) / No (Red)
- **Edit User**:
    - Modal interface to modify user details.
    - Fields: Username, Email, Verified Status, Admin Status.
    - Protected against modifying the main 'admin' account's critical privileges.
- **Delete User**:
    - Bulk delete functionality using checkboxes.
    - Confirmation modal before deletion.
- **User Numbering**: Dynamic serial numbering for the user list.

## 2. Product Management (Admin Panel)
- **Add Product**:
    - Form to create new products.
    - **Image Handling**: Dual support for:
        - **Image URL**: Direct link to an image.
        - **File Upload**: Uploading images from the local device (stored in `/uploads`).
    - Fields: Name, Price, Description, Stock, Image Source.
- **Stock Management**:
    - Ability to update stock levels for existing products.
- **Delete Product**:
    - Functionality to remove products from the catalog.

## 3. Authentication & Security
- **User Authentication**:
    - Traditional Email/Password Login and Signup.
    - **Google OAuth**: Integration for social login.
- **Access Control**:
    - **Admin Middleware**: Protects admin-specific routes and API endpoints.
    - **Session Management**: Secure session handling using `express-session` and MongoDB store.
- **Security Measures**:
    - Prevention of self-deletion or privilege removal for the root 'admin' user.

## 4. Backend Infrastructure
- **Server**: Node.js with Express framework.
- **Database**: MongoDB with Mongoose ODM.
- **API**: RESTful API architecture for:
    - `/api/auth`: Authentication routes.
    - `/api/admin/users`: User management endpoints (GET, PUT, DELETE).
    - `/api/admin/products`: Product management endpoints (GET, POST, PUT, DELETE).
    - `/api/orders`: Order processing (basic structure).

## 5. UI/UX Design
- **Theme**: Modern, dark-themed "Cyberpunk" aesthetic with neon accents.
- **Components**:
    - Custom Modals for editing and confirmation.
    - Toast Notifications for success/error feedback (slide-in animation).
    - Responsive tables with hover effects.
    - Glassmorphism effects on cards and modals.

## Future Roadmap (v2+)
- **Card Alignment**: Improve the layout and alignment of product/user cards.
- **Password Hashing**: Implement bcrypt for secure password storage (currently TODO).
- **Order Management**: Full implementation of order tracking and history.
- **Shopping Cart**: Frontend cart functionality for users.
